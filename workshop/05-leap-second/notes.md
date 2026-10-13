# Editor's notes on draft 1

"Conclusion" is back. It's a draft-1 reflex and I've stopped being annoyed about it; it gets deleted.

## The real problem: this is an explainer, not an essay

Draft 1 explains leap seconds competently and argues nothing. "The atom wins" is a description
of the vote, not a point of view.

### What's the argument?

The spine quote is sitting right there: Cloudflare's postmortem blamed "the belief that time
cannot go backwards." Read the CGPM resolution: the stated reason for ending leap seconds is
risk to "critical digital infrastructure." So, for essentially the first time, humanity is
changing the *definition of civil time* because our software holds a belief about time that
the planet doesn't share. For all of history, clocks were corrected to match the sky. Now
the sky is being told to wait, so the servers don't fall over.

That's a defensible, specific claim, and it's interesting. I also want to be fair to it: the
software people are *right*. A discontinuity in the base layer of time is a bad design.

### The turn past the twist

What do we do about the gap the sky and the clocks build up? We already shift clocks by a
whole hour, twice a year, in daylight saving time, and nothing breaks. Why does one second
crash Reddit when an hour doesn't? Because DST happens in the *display layer* (local time
zones, a lookup table built to change) while leap seconds hit the *base layer* (UTC itself,
which everything assumes is smooth). That's the systems-engineering insight, and it's the real
resolution: put the planet's irregularity in the layer designed to absorb irregularity. That's
my opinion and should be labelled as one.

## Missing mechanism

Why is the modern day "too long"? Because the atomic second was calibrated to match the average
day of the 19th century, and the Earth has slowed since. That's the eel-disguise equivalent:
the reason the problem exists. Draft 1 skipped it.

## Fact hygiene

- The "around 2026" negative-leap-second date is my inference from Agnew's "three years." Say
  "about three years sooner," and quote his "by 2029."
- Add: IERS says there will be no leap second at the end of 2026.
- Add my own arithmetic on how long an hour of drift takes at the recent rate, shown as
  arithmetic, not as an expert forecast (27 s in 44 years → ~0.6 s/yr → thousands of years).
  The secondary-source "50–100 years" figure is inconsistent with that arithmetic, so I won't use it.
- The vote result isn't in yet (the meeting is this week). Say so plainly, in the text.
- 2012 mechanism: say "livelock" (sourced), don't elaborate the hrtimer/futex story (unverified).
