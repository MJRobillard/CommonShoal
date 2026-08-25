# Common Shoal: Oxford, MD sandbar demo

A concept demo for a crowd-sourced, gamified sandbar map of the Tred Avon
River around Oxford, Maryland. Boaters trace a closed loop over water; the
loop becomes claimed "territory." Claims are built to reward precision over
size:

- **Small beats sprawling.** Where two claims overlap, the smaller one
  always keeps that ground. A bigger loop can surround a tight claim and
  take the open water around it, but can never swallow it. Tracing tighter
  than an existing claim carves that piece out, for reduced points.
- **Holds until it's proven wrong.** Claims run on a long clock, but any
  boater who finds open water where a claim says there's a bar can report
  it; enough reports reopen the ground. That's how the map tracks a bar
  that's actually moved, instead of guessing off a timer alone.

Over time, held and contested claims become a live, shared record of where
the river's shifting sandbars actually are.

This project is **nonprofit and community-run**: no ads, no paid tiers, no
data resale. It exists to give local boaters, and researchers who study the
river, a shoal map that's current, instead of one that's a season out of
date.

## What's in this folder

- `index.html`: the pitch page. Open it directly in a browser, no build
  step or server required. The hero is a phone-shaped mockup running a real
  [Leaflet.js](https://leafletjs.com/) map (OpenStreetMap tiles, Oxford, MD)
  loaded with a set of **illustrative** sample claims. Two of them, "Bob's"
  and "John's," overlap; since Bob's is the smaller claim, it's rendered
  carved out of John's territory (a real polygon boolean difference via
  [Turf.js](https://turfjs.org/), not just two overlapping shapes), which is
  the small-beats-sprawling rule in action. Claim edges are also rounded
  into a wandering curve (a small Catmull-Rom spline) so they read like an
  actual boat's track instead of a ruled polygon. All of it is demo data,
  there is no live GPS feed or database behind this yet.

- `mobile.html`: a standalone, larger version of the same phone mockup,
  wrapped in a full iPhone-style frame for showing what the app would look
  like in someone's hand.

- `how-it-works.html`: a dedicated, always-looping explainer for the
  small-beats-sprawling rule, linked from the pitch page's "how it works"
  section. Two SVG panels run the rule both directions: one traces a tight
  loop inside an existing claim and carves it out (using the same Turf.js
  `turf.difference`), the other traces a wide loop around an existing claim
  and shows it can only take the water surrounding it, never the claim
  itself.

- `draw.html`: a working drawing tool for collecting real outlines. Open it
  in a browser, use the polygon tool (top-left of the map) to trace shoals
  you actually know from experience on the river, name each shape, and hit
  **Export GeoJSON** to download `common-shoal-claims.json`. Everything runs
  client-side, nothing is sent anywhere, and in-progress shapes are kept in
  the browser's local storage so a refresh won't lose your work. The
  exported file is a standard GeoJSON `FeatureCollection`, with each
  polygon's `properties` carrying its `name`, `notes`, `area_m2`, and
  `area_acres`; hand that file back to fold real shoal locations into the
  demo.

## Project timeline

- **Demo (current):** the pitch page, mobile mockup, drawing tool, and
  mechanic explainer in this repo. Proving the concept before writing any
  real backend.
- **Community outreach (current):** talking to local boaters, the art
  shop, the pub, and the state aquatic and natural resources researchers
  who'd actually use a live shoal map, to find out if this is worth
  building for real.
- **Real build (next, pending outreach):** live GPS tracking, loop-closure
  detection, and a realtime backend for expiring claims.

## Possible future features

Nothing here is committed, these are ideas worth trying once the core
game is real:

- **Team mode:** claim and defend ground as a crew instead of solo.
- **Oxford vs. Bellevue:** a standing rivalry mode between the two towns
  on either side of the Tred Avon, tallying whose side holds more of the
  river.

## License (intended, once this becomes a real project)

- **Code:** MIT.
- **Sandbar/shoal data:** an open geodata license requiring attribution
  (ODbL or CC-BY), so the map stays free to use but the community's
  contribution stays credited.

## Contact

Matt Robillard · [mjrobillard.com](https://mjrobillard.com) ·
robillard.matthew22@gmail.com · (510) 220-9685
