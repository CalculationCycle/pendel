# Pendel

A one-page commute dashboard on Västtrafik's open API (Planera Resa v4). Static, so it runs on GitHub Pages.

Two legs each way:

- **Home → work** (default until 10:30, rides 06:00–09:30): leg 1 is 300 or 430 from Källarbacken to
  Delsjömotet (main), or 430 from Källarbacken to Landvetter (exception). Under each: the first bus
  from there on to Liseberg Station.
- **Work → home** (default from 10:30, rides 15:00–17:30): the same legs in reverse. Each bus home
  shows the last bus from Liseberg Station that makes it; one you can no longer reach is marked
  *Too late*, and the box at the top counts down to when you have to leave work.

Every trip comes from Västtrafik's journey planner, asked for direct trips between the two stops, so
only buses that actually go that way are listed. Rides that have left stay listed, greyed out, with
a *Now* line before the next one, and the page scrolls to it. "Load more" extends the window by 30
minutes. The footer shows which stops the names matched.

Settings at the top of the script: `STOPS`, `FIRST_LEGS`, `WINDOWS`, `TRANSFER_MINUTES` (2).

## Publish

1. Push this folder to a GitHub repo.
2. Settings → Pages → Deploy from branch → `main` / root.
3. Open the page on your phone and add it to the home screen.

## Connect

On first open the page asks for a Västtrafik key and secret. Create an application at
<https://developer.vasttrafik.se> and subscribe it to **Planera Resa v4**. The key is stored in
that browser's localStorage only, never in the repo. "Change key" at the bottom clears it.

Stops are matched by name on first load and remembered; the footer shows the matches. If a name
matches the wrong stop, pin it in `STOPS` or `FIRST_LEGS` as `{ gid: '9021014…', name: '…' }`.
