---
layout: post
title:  "[EN] Monitoring a Victron Multiplus inverter"
date:   2014-06-22 12:00:00
categories: autonomie
---

In previous posts, I've described how I monitored the BMV battery
monitor (reading what goes in and out of the batteries), and the MPPT
solar controller (reading what comes from the solar panels). Most of
the electricity, coming from the shore or from the fuel generator,
is inverted back from 24VDC to 230VAC, to feed the boat's equipment,
by the charger-inverter.

The protocol used by the Victron Multiplus isn't as straightforward as
for the MPPT or the BMV. Indeed, inverters need more advanced
communication systems: they can be hooked up together, either in
parallel to addition their maximal output power, or with a pi/3
phase-shift to produce a 3-phase 400VAC power supply. The protocol
needs to be not only write-friendly for embedded microcontrollers, but
also read-friendly. Although it's not published, Victron essentially
states in its documentation "it's tricky to implement, but if you're
sure you want to do it, write us and we'll send the spec". Sure
enough, that's what I did and how they responded :)

I'm not publishing the spec, because it's theirs and they must have
their reasons not to open it up more than they do, but it's clear,
no-nonsense and not ambiguous. I wish all IETF or OMA specs
high-profile public specs were as well written as that.

What to tell to an inverter?
----------------------------

I'm not going to implement, let along test, any code that might modify
the inverter's settings in non-trivial ways, save for what can be done
by a remote panel (limit current input, switch the charger and
inverter functions on and off). Bricking the family's 230VAC supply
would get me in too much trouble, and ban me from pursuing any
monitoring expriment :)

So the functions I'll use are:

* `version`, returning the device's firmware version, because it's a
  safe and easy first test:

        > :assets.multiplus:version()
        = { mode = "VE.Bus",
            version = 1130126 }

* `led`, returning the status to be displayed on remote panels, mostly
  LED indicators in a state among `on`, `off`, `blink` and `inverted_blink`:

        > :assets.multiplus:led()
        = {
           inverter = "on",
           temperature = "off",
           overload = "off",
           mains = "off",
           float = "off",
           low_battery = "off",
           absorption = "off",
           bulk = "off" }

* `state`, which conversely to `led`, sends to the inverter what can
be set from a remote panel, i.e. the switch's state (`on`, `off`,
`charger` or `inverter`) and the 230VAC input current limit (up to 16A
on my system):

        > :assets.multiplus:state('on', 16)

* `frame`, returning instant statistics about an electric line, either
  the DC one connected to the batteries, the AC one in a signle-phase
  install, or each of the phases on a 3-phase system:

        > :assets.multiplus:frame 'AC'
        = {
           inverter_current = 9.1,
           inverter_factor = 1,
           phase_name = "L1",
           n_phases = 1,
           bf_factor = 1,
           mains_current = 0,
           mains_period = "n/a",
           voltage = 229.84 }
        > :assets.multiplus:frame 'DC'
        = {
           used_current = 6.27,
           provided_current = 0,
           inverter_period = 13.6,
           phase_name = "DC",
           voltage = 27.37 }

Implementation details
----------------------

I won't describe the implementation in detail: there's no point if I'm
not going to publish the spec it's based on. The subset of commands
I'm using here is fairly standard: frames with a length prefix, a
command byte to make sense of the arguments in the remaining of the
frame, and a checksum byte. Relevant data are encoded as bytes, of
(decimal) fixed-point multi-byte numbers.

The implementation is cut in two main modules, `victron.mk2.encode`
and `victron.mk2.decode`. They convert between binary representation
and Lua tables. Apart from translation, the code does typical
management of serial data over Linux (through USB): read a frame
(frame size then frame content), retry in case we stumbled in the
middle of a frame or if checksum indicates a problem, close/reopen the
port in case the USB/serial adapter gets lost, etc.

What do do with this?
---------------------

* For energy monitoring, the values in `frame 'AC' .inverter_current`
  and `frame 'AC' .voltage` allow to compute the amount of 230VAC
  current consumed in the boat.

* `frame 'DC' .provided_current` indicates what's pushed form the
  shore or the fuel generator in the batteries.

* `frame 'DC' .used_current`, combined with the MPPT figures, allows
  to compute the consumption of 24VDC devices.

* `led` and `state(switch, limit)` allow to reimplement a software
  remote panel. Victron provides high-resolution pictures of their
  products, including the remote control panel, so with a quick CSS
  hack, a web app should be quickly pieced together. An Android app
  might follow, but I feel in no hurry to go down that rabbit hole :)
