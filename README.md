# Study Spaces: CPSC 344 prototype

A medium-fidelity prototype for finding and booking study spaces at UBC. The spaces, photos, and their facts come from our field visits. Today's bookings, free-seat counts, and reviews are mock data. Nothing is actually booked or emailed.

## Put it on GitHub Pages

1. Create a public GitHub repository and upload `index.html`, this README, and the whole `images` folder, keeping the folder name.
2. Go to **Settings → Pages**, set **Source** to "Deploy from a branch", choose `main` and `/ (root)`, then save.
3. After about a minute, the site is live at `https://<your-username>.github.io/<repo-name>/`.

The photos are about 1.5 MB in total (resized, with GPS and camera data removed). The campus map is drawn by the page itself, so no map service or API key is needed. Only the Leaflet map library loads from the internet.

## Screens

| Screen | How to get there |
| --- | --- |
| Search list | **Find** tab. Filter by noise, outlets, seating, group size, distance, "available now", and "rooms I can book". |
| Map → building | Tap a building pin on the map. The building screen lists its study spaces. |
| Room | Tap any space. Photos, live status, who can book it, facts, today's schedule, **Book this room**, and **See reviews**. |
| Booking | **Book this room**. Shows whether you're eligible, a 7-day picker, and a time grid (tap a start time, then an end time). |
| Confirmation | After **Confirm booking**. Includes a preview of the confirmation email. |
| Reviews | **See reviews** on a room. |
| My bookings | **Bookings** tab. Check in, reschedule, or cancel. |
| Saved | **Saved** tab. ICICS X237 and the Woodward Quiet Study Room start out saved. |

## Built-in cases for testing

The demo user is **Alex Chen, a Computer Science student**, at DMP 110 on **Wed, Nov 25 at 2:10 PM**. The clock doesn't move, so every participant sees the same thing.

- **ICICS X237:** CS students only, so Alex **can** book it.
- **Shrum 2005:** Chemical Engineering students only, so Alex **can't** book it.
- **IKB 263:** anyone can book, but at least 24 hours ahead, so today is unavailable.
- **Woodward Quiet Study Room:** groups of 3 or more only, so group size starts at 3.

Reloading the page resets everything, which is handy between participants.

## Editing the data

Everything is at the top of the `<script>` in `index.html`:

- `BUILDINGS`: building names and map positions (approximate; the Shrum and CHBE positions in particular are estimates).
- `ROOMS`: every space. Times are minutes after midnight (`H(15)+30` = 3:30 PM). `access` sets who can book; `rules` sets `advance` (minutes ahead) and `minGroup`.
- `USER`, `BASE`, `NOW`: the demo student, date, and time. Change `program` to see eligibility change.
- To add photos, put them in `images/` and list them in the room's `photos`. A space with no photos shows a simple drawing instead.
