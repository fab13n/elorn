---
layout: post
title:  "[EN] Solar electricity: connecting the MPPT"
date:   2014-05-22 12:00:00
categories: autonomie
---

After some hardware issues (broken USB prolongator, due to my own
clumsiness), I've connected the MPPT solar controller to the Raspberry
Pi. Compared to the situation as described in the previous post, it
means I get not only measures at the battery connectors, but also what
gets out of the solar panels. I still miss some measures at the
inverter's boundaries in order to get the whole picture, but it's
getting clearer.

Here's a diagram with all of the boxes I'd like to fill:

![What ought to be measured]({{ site.baseurl }}/img/solar-diag-legend.png)
_What ought to be measured in the electrical production system._

## What misses

The Battery monitor gives me direct access to _"Battery state"_ and to
_"MPPT->battery"_+_"Battery<->inv."_-_"Battery->24V"_. By connecting
the MPPT, I get _"MPPT->battery"_, so I can compute
_"Battery<->inv."_-_"Battery->24V"_. In a first approcimation I'll
consider that most of the power is used by the inverted, so
_"Battery->24V"_~0W. This will be corrected when I'll be able to read
the inverter input directly.

Position is returned directly by the GX440's integrated GPS. It can be
returned on the local network on a configurable socket, and/or to
AirVantage servers.

_"Inverter->230V"_ is very close to _"Battery<->inv."_ (efficiency is
around 95%) as long as shore and genset are
off. _"Shore->inv."_+_"Gen.->inv."_ can be deduced from
_"Battery<->inv."_ and _"Inv->230V"_, both of whom will be provided by
the inverter. Discriminating between shore and genset can be done by
checking whether the genset's battery circuit is switched on, or by
clamping cheap AC current sensors around cables.

## Still enough

Anyway, what's important to check is approximately how much comes from
the panels, at what time, and how much is consumed by big appliances,
so _"MPPT->battery"_ and a reasonable estimate of _"Battery<->inv."_;
with those we can take the key decisions: should we rather move to the
shade or switch conditioned air on? Do I need to switch the genset on
to use the angle grinder? et.

## Looking at some curves

Here's a _"Battery<->inv."_ curve:

![Power balance at battery boundaries]({{ site.baseurl }}/img/mppt-curve-1.png)
_Power balance at battery boundaries._

We see that from around 11:00AM, when the sun gets over the platanus
trees, the batteries are filled with 600-700W of power. That's
actually 800-900W from the panels, with about 100W of concurrent
consumption (cf. below). We see a couple of short but intense
discharges, typically due to washing machine heaters and pumps.

From around 2PM, we see a nice decreasing asymptote to the curve: the
battery being nearly full (94% at 2PM), it accepts less incoming
power, so the MPPT artificially raises the impedence, hence the
voltage, presented to the panels, to reduce their production. It's
more obvious on the solar production curve:

![Power from MPPT to battery]({{ site.baseurl }}/img/mppt-curve-2.png)
_Power form MPPT to battery._

The deliberate change of mode is even more striking if we check
directly the voltage at the panels:

![Tension on panels]({{ site.baseurl }}/img/mppt-curve-3.png)
_Tension on panels._




