# Pendel

A one-page commute dashboard on Västtrafik's open API (Planera Resa v4). Static, so it runs on GitHub Pages.

The page is built around the leg that matters, the bus between Källarbacken and Delsjömotet (or
Landvetter). The other leg has buses every few minutes, so it only gets a small line.

- **Home** (default until 10:30, rides 06:00–09:30): every 300 and 430 from Källarbacken towards
  Landvetter or Åkareplatsen, with its arrival at Delsjömotet (or Landvetter for the 430). Under
  each: the first bus you can catch on to Gårdatorget and Liseberg station.
- **Office** (default from 10:30, rides 15:00–17:30): every 300 and 430 from Delsjömotet (or 430
  from Landvetter) to Källarbacken. Under each: the last bus from Liseberg station or Gårdatorget
  that makes it. A bus home you can no longer reach from work is marked *Too late*. The box at the
  top counts down to when you have to leave the office.

Departures come from each stop's departure board, so no bus is left out; a bus's own stop list
rules out buses going the other way. Rides that have left stay listed, greyed out, with a *Now* line
before the next one, and the page scrolls to it. "Load more" extends the window by 30 minutes. At the
bottom are the next buses on the easy leg. Delays and cancellations come from Västtrafik's realtime
data; the page refreshes every 30 seconds.

Settings at the top of the script: `WINDOWS`, `TRANSFER_MINUTES` (2), `HOME_LINES`,
`HOME_DIRECTIONS`, `STOPS` and `TRANSFERS`.

## Publish

1. Push this folder to a GitHub repo.
2. Settings → Pages → Deploy from branch → `main` / root.
3. Open the page on your phone and add it to the home screen.

## Connect

On first open the page asks for a Västtrafik key and secret. Create an application at
<https://developer.vasttrafik.se> and subscribe it to **Planera Resa v4**. The key is stored in
that browser's localStorage only, never in the repo. "Change key" at the bottom clears it.

Stops are matched by name on first load and remembered. If a name matches the wrong stop, pin it
in `STOPS` at the top of the script as `{ gid: '9021014…', name: '…' }`.
