---
layout: post
title:  "[EN] Solar electricity: first measures"
date:   2014-05-22 12:00:00
categories: autonomie
---

Wednesday has been the first day spent unplugged, not under the trees,
and with active monitoring of the batteries. The incoming measures are
extremely good, given that the sky was rather cloudy. Actually,
production has been so good (and we've been so frugal last night) that
I have no idea how many kWh we could have harvested: the sun came over
the trees at around 11AM, and by 3PM the solar controller was limiting
their production because the batteries where almost full.

There's been a bet in the choice of the panels: I purchased some
thin-film panels, which have a rather poor performance in W/m2, but
are more resilient to cloudy conditions, because their preferred
photon frequency is lower than crystalline panels' (red and
near infrared, when conventional panels work in the near UV, to which
clouds are much less transparent).

![Panels positioning]({{ site.baseurl }}/img/panels-schematic.png)
_Panels positioning on the fore of the boat._

[Those 12 panels](http://www.sharp.eu/cps/rde/xchg/eu/hs.xsl/-/html/product_details.htm?product=NAE135G5)
are rated at 12\*135W in Wonderland (what salespeople call "Standard
Test Conditions", which are anything but standard), and 12\*100W in
realistic ([NOCT](http://www.amsolar.com/home/amr/page_164))
conditions. They take 12\*1m\*1.40m = 18m2 of space, but I have
13m\*4.20m=55m2 of freight roof, so I can afford it. Moreover, I had
them for a good price (less than 1€/W NOCT).

Here are the curves:

![Our first production day]({{ site.baseurl }}/img/wednesday-charts-640.png)
_Power range is +/-1kW. The -800W dip around 13:15 is most likely a
water pump_.

We can see that the panels push between 300W and 800W, but from 3PM,
the batteries are almost charged and the MPPT actively limits the
input power, by raising its panel-side impedance. It probably means
that on sunny days, we could afford to run the 150l electrical water
heater on photovoltaic electricity, as preposterous as it seems! 800W
will heat 150l of water at about 4.5°C/hour.

I currently haven't found a way to setup an effective and good-looking
solar water heater for much less than 2000€. Under similar sun
conditions, a 4m2 heat panel would pump about 1.6kW, counting a
reasonable 80% efficiency. That would produce about 9°C/h; starting
from 20°C I'd boil my tank in two days... I'm glad I haven't rushed
buying heat panels :)

Tonight, we have friends coming aboard, and we'll cook a
[cassoulet](http://en.wikipedia.org/wiki/Cassoulet) in the oven;
weather forecasts being similar to today's, we'll have an opportunity
to test longer loads!
