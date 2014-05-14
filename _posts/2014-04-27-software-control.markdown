---
layout: post
title:  "[EN] Software Control: domotics--or rather, naumotics"
date:   2014-04-27 12:00:00
categories: software
---

**French summary:** _Cette page est en Anglais, parce qu'elle
n'intéresse que des informaticiens et des électroniciens, qui sont à
peu près tous anglophones. Elle liste quelques idées que j'ai en tête,
plus ou moins concrètes, pour surveiller et automatiser divers
systèmes sur le bateau (essentiellement la production d'électricité et
d'eau)._

Introduction
------------

So I live aboard a 100ft Belgian barge, on the Canal du Midi. It has
quite a few specialized systems, including an on-board oil electric
generator, 12kWh worth of lead batteries, a converter from/to 230VAC
and the batteries' 24VDC, solar panels, a shore electricity limiter, a
water purifier and its tank, Internet through a 4G modem... This page
describes what I've done and what I intend to do to monitor and
control those system through software.

Victron gear
------------

Most of my electricty gear comes from Victron. They have a good
reputation, are one of the two mainstream brands for boats, and
produce very good documentations--including the specs of the protocols
needed to communicate with their systems.

I have 3 devices I want to monitor:

* a [battery monitor](http://www.victronenergy.fr/battery-monitors/bmv-600s%20and%20bmv-602s/), which counts what goes in and out of the
  batteries. It has a 3.3V TTL serial line readily available, on which
  it publishes easy-to-parse ASCII text.

* an [MPPT](http://www.victronenergy.fr/solar-charge-controllers/mppt7550/), which stores solar energy into the batteries.

* a
  [charger-inverter](http://www.victronenergy.fr/inverters-chargers/multiplus-12v-24v-48v-800va-3kva/),
  which pushes electricity from the shore or the genset into the
  batteries, and converts battery power back into 230VAC as needed. It
  also has a couple of nice features, such as shore power limitation
  and assistance, load smoothing to save the genset from sudden
  surges, etc. It talks _MK2_, a proprietary binary protocol, whose
  specs have been kindly sent to me by Victron.

I plan to do a bit more than just monitor the charger-inverter,
actually: it can be remote-controlled by a
[dedicated panel](http://www.victronenergy.fr/panel-systems-remote-monitoring/remote-control-panels/),
which can be emulated in software with a serial line. I'd like to make
a simple Android app acting as such a panel. I could also decide to
switch the charger on and off programmatically, or limit its intake
current, depending on solar production, to use a mixed shore + solar
electricity.

![Multiplus control panel]({{ site.url }}/img/Digital-Multi-Control--Panel-Front-640.jpg)
_The control panel I look forward to emulate on my phone._

There are a couple of other things, either interesting or fun to
monitor:

* 230VAC input. My meter has an impulsion output, so that's fairly
  easy.

* Whether the genset is running. It allows to keep separate accounts
  of shore electricity consumption vs. that produced from fuel by the
  genset.

* GPS position: the 4G router has a GPS chip in it, so it would be fun
  to correlate with solar panels' production. I'd like to also have
  orientation, but I don't think it has a compass, and I don't think a
  compass would be very accurate in a 60 tons steel hull.

* 3G and 4G signal strength, also correlated with GPS, and public
  positions of [BTS antennas]().

* I'd probably like to check the individual consumption of some
  systems. Can be done with an amperemetric clamp on the main panel,
  or with some meter plug. For instance, if I knew how much the
  electric water heater costs, I could decide whether I'm in a hurry
  to install a solar / wood pellet heater. Beware, affordable clamps
  only monitor AC, not DC (they're based on AC transformers, not
  Hall-effect probes).

Finally, some non-electric things might also be worth logging:

* Temperature: inside, outside, in the water. I wonder what's the net
  impact of water on the boat's temperature, compared to a house.

* Maybe inside hygrometry, just because many air temperature sensors
  provide the information for free.

* Water: production, and consumption (there's a 1.5 tons tank in
  between, which we fill with purified canal water in about 10-15h
  depending on turbidity). I wonder whether I can correlate the
  production, in liters per hour, to the weather, the GPS position,
  the age of the filters. Also worth investigating is the pressure
  loss between the beginning and the end of the tank filling process,
  due to filters clogging.
