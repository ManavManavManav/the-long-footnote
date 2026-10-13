---
layout: post
title: "The Belief That Time Cannot Go Backwards"
subtitle: "This week, the world's timekeepers are voting on whether to stop matching our clocks to the Earth. The reason is software."
reading_time: 11
date: 2026-10-13 13:00:00 -0400
---

At midnight UTC on New Year's Day 2017, a small fraction of the internet's DNS lookups started failing. The company was Cloudflare, and over the next few hours its engineers traced the problem to a few lines of code in their DNS server that measured how long things took. You record the time, do the work, record the time again, and subtract. The answer is always zero or positive.

That night it came out negative. At the stroke of midnight, the world had added a second to the clock — 23:59:59, then 23:59:60, then 00:00:00 — and on some machines the system clock briefly stepped backward. A function that was handed a negative number did what it was written to do, which was to panic. Cloudflare had most of the affected machines patched within 90 minutes and everything fixed by 6:45 in the morning. Their public postmortem named the root cause with unusual philosophical clarity:

"The belief that *time cannot go backwards*."

I think that sentence is the best summary of a decision being made this week in Versailles. From October 13 to 15, 2026, the General Conference on Weights and Measures, the body that defines the meter, the kilogram and the second, is meeting to settle the future of the leap second. The draft resolution on the table would make Coordinated Universal Time continuous from May 20, 2027, with no further adjustments, and let it drift up to a full hour away from the Earth's rotation before anyone does anything about it.

If it passes (the result isn't out as I write this), it will be the first time in history that humanity deliberately stops correcting its clocks to match the sky. And the stated reason, more or less, is that our software agrees with Cloudflare's code: time is not allowed to go backwards, or sideways, or to have 61 seconds in a minute. The planet disagrees. The planet is losing the vote.

---

## Two clocks

There are two ways to keep time, and for almost all of human history they were the same way.

The first is the planet. A day is a rotation, and noon is when the sun is highest. Every sundial, every church bell, every railway timetable for most of the 19th century was ultimately a reading of where the Earth was in its spin.

The second is the atom. Since 1967, the second has officially been a fixed number of oscillations of a cesium atom: 9,192,631,770 of them. Atomic clocks count those oscillations with absurd precision. They don't care where the sun is.

When atomic clocks arrived in the 1950s, they revealed something embarrassing about the first clock: the Earth is a bad timekeeper. It's slowing down, mostly because the Moon's tides act as a brake, drawing on the planet's rotation and lengthening the day by roughly 1.5 to 2 milliseconds per century. Superimposed on that slow trend is a lot of unpredictable wobble from the liquid core, the oceans, the atmosphere and the shifting of ice.

There's one more twist, and it's the reason the problem exists at all. When scientists fixed the length of the atomic second, they calibrated it to match the average length of a second in the 19th century, since that was what the best astronomical data covered. But by the time the definition was adopted, the Earth had slowed a little further. So a modern day, measured in atomic seconds, is usually a touch longer than 86,400 of them, by a millisecond or two. A couple of milliseconds a day doesn't sound like anything. Over 500 days, at two milliseconds a day, it adds up to a full second.

## The patch

In 1972, the world adopted a compromise, and it was a very human one. Coordinated Universal Time, UTC, would tick in atomic seconds, perfectly regular, but it would be kept within 0.9 seconds of the time told by the Earth's rotation. When the gap got too wide, timekeepers would insert an extra second into the last minute of a day, usually June 30 or December 31. That minute would have 61 seconds, and its final one would be labeled 23:59:60.

To start things off, UTC was set ten seconds behind International Atomic Time. Since then, 27 leap seconds have been added, on average about one every eighteen months. The last one was at the end of 2016. The current gap between atomic time and UTC is 37 seconds: the original ten, plus 27.

For most of the period since 1972 this was an elegant fix. Atomic precision for the people who needed it, the sun staying overhead at noon for everyone else, and a tiny correction every so often to keep the two in step. It's the kind of compromise a committee is proud of.

Then everything got networked.

## Sixty-one seconds

Computers assume a lot about time. A minute has 60 seconds. A day has 86,400. Clocks move forward. If you subtract an earlier timestamp from a later one, you get a positive number. Most of the time all of this is true, and code that relies on it works fine. Every year and a half or so, it briefly wasn't true, at exactly the same moment for every computer on Earth.

On June 30, 2012, the leap second exposed a bug in the Linux kernel that, when the extra second came, could send machines into what engineers call a livelock: processors running flat out, doing no useful work. Reddit went down. So did parts of LinkedIn, Mozilla, Yelp and Foursquare. In Australia, the Amadeus reservation system that handles check-in for Qantas and Virgin Australia fell over for about an hour, and airport staff checked people in by hand.

In 2017 there was Cloudflare and its negative stopwatch. Smaller incidents turned up around other leap seconds too, each one a variation on the same theme. Somebody, somewhere, wrote code that believed time was smooth.

The big companies' answer was to lie about time, very gently. Google has done it since 2008 and calls it the "leap smear." Rather than adding a second at midnight, it runs every clock in its fleet about 0.001% slow for 24 hours, from noon to noon, so the extra second is spread across the day in increments too small for anything to notice. Its very first smear, in 2008, used a cosine curve; it later switched to a straight line. Meta smears too, over 17 hours, on a quadratic curve. In other words, the world's largest computer networks each spend a day running on a private, slightly wrong version of time to keep from having to experience 23:59:60.

In 2022 Meta's engineers published a blog post titled "It's time to leave the leap second in the past." They called the leap second "a risky practice that does more harm than good" and suggested freezing the count at 27 permanently.

## The first vote

That November, the General Conference on Weights and Measures agreed. Resolution 4 of its 2022 meeting said that the allowed gap between UTC and Earth time "will be increased in, or before, 2035," so that UTC could run without breaks "for at least a century." It gave its reason explicitly: the risk of "serious malfunctions in critical digital infrastructure," including the satellite navigation systems that much of the modern world quietly depends on.

Russia voted against. Its satellite navigation system, GLONASS, was built with leap seconds baked in, and it wanted the change pushed out to 2040 or later. The International Telecommunication Union came on board in 2023 and left the details, including the actual tolerance and start date, to this year's meeting.

So far, this looks like a story about engineers being right, and they are. A discontinuity in the most basic layer of a system is bad design. If you were building a global timekeeping system from scratch, you would not choose to insert an irregular, unpredictable extra second, announced six months in advance, into the one number every computer treats as sacred.

But there's another reason for urgency, and it comes from the planet.

## The Earth speeds up

For decades the leap second was understood as a one-way patch. The Earth was slowing, so you always added seconds. Nobody ever planned for the other direction.

Then, around 2020, the Earth started spinning faster. On July 19, 2020, the day came in 1.46 milliseconds short of 86,400 seconds, the shortest day since precise measurement began. On July 5, 2024, the record fell again: 1.66 milliseconds short. The likely cause is the liquid outer core, which seems to be slowing in a way that, by conservation of angular momentum, speeds up the solid planet around it.

A faster planet means the gap between UTC and the Earth starts closing from the other side. Keep that up and the rules would require something that has never happened in the history of UTC: a negative leap second. The clock would go from 23:59:58 directly to 00:00:00, skipping 23:59:59 entirely.

If a positive leap second, which happened 27 times, could take down Reddit and an airline check-in system, a negative one, which has never happened at all, is a much scarier prospect. Meta's 2022 post warned that it had never been tested at scale. The 2022 resolution called it something "whose insertion has never been foreseen or tested." The IERS, which announces leap seconds, has said there won't be one of either sign at the end of 2026. After that, nobody knows. Estimates quoted in the press for the chance of a negative leap second before 2035 range from about 30% to 40%.

## The part where we change the planet

And here's the strangest fact in this essay.

In 2024, the geophysicist Duncan Agnew published a paper in *Nature* titled "A global timekeeping problem postponed by global warming." His analysis says UTC "will require a negative discontinuity by 2029." But it would have come about three years sooner except for one thing: the polar ice sheets are melting. As water runs off Greenland and Antarctica into the oceans, mass moves from the poles toward the equator. A spinning object that moves its mass outward slows down. That's the same physics as a figure skater opening her arms.

Read that again, slowly. Human beings have burned enough carbon to melt enough ice to measurably change the rotation of the Earth, and the most immediate consequence anyone has calculated is a delay to a software risk. Climate change has, among its other effects, bought the world's IT departments roughly three years.

## A second versus an hour

So, assuming the vote goes the way the draft resolution suggests, UTC becomes continuous from May 2027, and the Earth will be allowed to drift up to an hour out of step before anyone corrects it.

How long would that take? Here is a bit of arithmetic, and it's mine, not the conference's. Over the 44 years from 1972 to 2016 the gap grew by 27 seconds, about 0.6 seconds a year. At that rate an hour of drift would take nearly 6,000 years. The tides will steadily lengthen the day, so the real number will be shorter, and the wobbles make any long forecast shaky. But the 2022 resolution's "at least a century" is very safe. Nobody now living will see the sun noticeably late at noon because of this.

Which brings me to the thing I keep coming back to.

We already shift our clocks by an entire hour, twice a year, in a great many countries. Daylight saving time moves billions of clocks by 3,600 seconds overnight, and Reddit doesn't go down. Why does a single second break the internet while an hour breaks nothing?

The answer is layers. Daylight saving happens in the *display* layer, in local time zones, which are basically a lookup table that turns UTC into the time on your wall. That table was built to change, and it changes all the time when governments redraw zones or tweak their rules. Software expects it. The leap second happened in the *base* layer, in UTC itself, the one quantity every system treats as smooth and unchanging. Put a discontinuity there and everything built on top feels it.

This is my opinion, not anything the conference has said: I think the real lesson of the leap second isn't that the sky lost to the servers. It's that the correction was in the wrong layer. The Earth's irregularity is real, and someone, someday, will need to account for it. The right place to do that is the layer built to absorb irregularity: a time zone shift, the kind we already do without thinking. Keep the foundation smooth, and let the planet's moods live in the lookup table.

---

For fifty-four years, every eighteen months or so, a handful of people at an observatory in Paris looked up at the Earth, looked down at their atomic clocks, and decided whether to make the world wait one second for the planet to catch up. If the vote goes through, the last time that happened will have been New Year's Eve, 2016.

Nobody will notice at first. Atomic time will keep counting. The Earth will keep turning slightly unevenly, slowing under the Moon's pull and speeding as its core sloshes and its ice melts. The gap between them will grow, a fraction of a second a year, too small to see. Sometime, centuries from now, someone will look at the sun and the clock, notice they've wandered apart, and move the time zone over by an hour, the way we already do every spring.

Time can't go backwards. It can, though, wander off.

---

<div class="sources" markdown="1">

**Sources and notes**

- Cloudflare, "How and why the leap second affected Cloudflare DNS" (2017) — [link](https://blog.cloudflare.com/how-and-why-the-leap-second-affected-cloudflare-dns/)
- *The Register* on the 2012 leap second outages — [link](https://www.theregister.com/2012/07/02/leap_second_crashes_airlines/)
- NIST Leap Seconds FAQ — [link](https://www.nist.gov/pml/time-and-frequency-division/leap-seconds-faqs); USNO, "What is a leap second?" — [link](https://maia.usno.navy.mil/information/what-is-a-leap-second)
- IERS Bulletin C (no leap second at end of 2026) — [link](https://datacenter.iers.org/data/latestVersion/bulletinC.txt)
- Google, "Leap Smear" — [link](https://developers.google.com/time/smear)
- Meta Engineering, "It's time to leave the leap second in the past" (2022) — [link](https://engineering.fb.com/2022/07/25/production-engineering/its-time-to-leave-the-leap-second-in-the-past/)
- CGPM 2022 Resolution 4 — [link](https://www.bipm.org/en/cgpm-2022/resolution-4); CGPM 2026 draft resolutions — [PDF](https://www.bipm.org/documents/20126/284836054/CGPM-2026-Draft-Resolutions.pdf)
- BIPM on WRC-23 — [link](https://www.bipm.org/en/-/2023-12-12-wrc-dubai)
- *Scientific American* on the 2022 vote and Russia's objection — [link](https://www.scientificamerican.com/article/the-leap-seconds-time-is-up-world-votes-to-stop-pausing-clocks/)
- D. C. Agnew, "A global timekeeping problem postponed by global warming," *Nature* 628, 333–336 (2024) — [link](https://www.nature.com/articles/s41586-024-07170-0)
- Shortest-day records: timeanddate — [link](https://www.timeanddate.com/time/earth-faster-rotation.html); *Smithsonian* — [link](https://www.smithsonianmag.com/smart-news/today-will-likely-be-shorter-than-usual-and-it-will-happen-again-in-august-heres-why-180986989/)
- Negative leap second probability estimates (secondary) — *Tech Times* — [link](https://www.techtimes.com/articles/320185/20260711/earth-rotation-records-spur-october-vote-avert-negative-leap-second.htm)

*Written on October 13, 2026, the first day of the 28th CGPM. The vote's outcome was not yet public. The 6,000-year figure is the author's own back-of-envelope arithmetic, not a forecast.*

</div>
