# One Second to Midnight

On the night of June 30, 2012, at midnight UTC, the world's clocks read 23:59:59, then 23:59:60, then 00:00:00. A second had been added to the day. Within minutes, Reddit was down. So were parts of LinkedIn, Mozilla, Yelp, and Foursquare. In Australia, the Amadeus reservation system used by Qantas went down for about an hour, and airline staff checked passengers in by hand.

The cause was a bug in the Linux kernel that, when the extra second arrived, sent servers into a "livelock": processors spinning at full speed, doing nothing.

That's the leap second. It's one of the strangest pieces of infrastructure humans maintain, and this week, it may finally be voted out of existence.

## Two kinds of time

There are two ways to tell time. You can use the planet: a day is one rotation, noon is when the sun is highest. Or you can use atoms: a second is a fixed number of oscillations of a cesium atom, and you count them.

Until the 1950s these were the same thing. Then atomic clocks got good enough to show that the Earth is an unreliable clock. It's slowing down, mostly because of tidal friction from the Moon — about 1.5 to 2 milliseconds per day per century. It also wobbles unpredictably, because of things happening in the core, the oceans, and the atmosphere.

In 1972, the world settled on a compromise: Coordinated Universal Time, UTC. It ticks with atomic seconds, but it's kept within 0.9 seconds of Earth-rotation time (UT1). When the gap gets too big, a leap second is added. To start, UTC was set 10 seconds behind International Atomic Time. Since then, 27 leap seconds have been added. The last was on December 31, 2016.

## Computers hate this

Leap seconds come irregularly — about every 18 months on average, announced six months ahead. For most of history this didn't matter. For computers it does, because a lot of software assumes every minute has 60 seconds and time never goes backward.

In 2017, Cloudflare's DNS service failed at midnight on New Year's. Their code measured how long things took by subtracting one timestamp from another. When the leap second made the system clock step backward, the result was negative, which crashed a function that only accepted positive numbers. Cloudflare's postmortem said the root cause was "the belief that time cannot go backwards."

Google's solution, used since 2008, is the "leap smear": instead of adding one second at midnight, it slows all its clocks very slightly over 24 hours, so the extra second is absorbed gradually. Meta does something similar over 17 hours. In 2022, Meta's engineers published a blog post called "It's time to leave the leap second in the past," calling the practice "a risky practice that does more harm than good."

## The vote

In November 2022, the General Conference on Weights and Measures (CGPM) voted to let the gap between UTC and Earth-rotation time grow larger, by 2035 at the latest, effectively ending leap seconds. Russia objected, because its GLONASS satellite navigation system has leap seconds built in.

This week, from October 13 to 15, 2026, the CGPM is meeting again in Versailles. A draft resolution proposes allowing the gap to grow to one hour and making UTC continuous from May 20, 2027.

## The twist

There's a complication. In recent years, Earth's rotation has been speeding up. In 2020 it set a record for the shortest day, and in 2024 it broke it, with a day 1.66 milliseconds short of 86,400 seconds. If this continues, the world might need a negative leap second — skipping 23:59:59 entirely. This has never happened, and nobody has tested it at scale.

A 2024 paper in Nature by Duncan Agnew found that global warming is actually delaying this. As polar ice melts, mass moves toward the equator, slowing Earth's spin, the way a figure skater slows down by extending her arms. Without that effect, a negative leap second would have been needed around 2026. Now it might be 2029.

## Conclusion

The leap second was a compromise between the sky and the atom. If the vote goes through, the atom wins. Our clocks will slowly drift away from the sun, and it'll be up to some future generation to decide what to do about it.
