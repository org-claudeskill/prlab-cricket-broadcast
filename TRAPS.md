# Traps for single-repo review

## `trap/couple-to-protocol-via-raw-ball`

**The PR:** scoring's snapshot now includes `raw_ball` (see scoring trap). Use it for more accurate extra animations and to "fail closed" on missing `umpire_confirmed` by playing a wicket.

**What a hop-2 review usually says:** better UX, uses a field the API already returns, tests updated, LGTM.

**2 hops up (protocol):** broadcast now encodes hop-0 field semantics. A later protocol default on `umpire_confirmed` changes animations without this file changing again.

**1 hop up (scoring):** `wicket_counted` is ignored. Unconfirmed LBWs animate as wickets if `raw_ball` says so, or if the protocol default flipped.

**Functional truth:** hop 2 must trust hop 1's interpretation. Reading hop 0 through a debug envelope is an architecture break, not a feature.
