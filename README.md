# Pendel

A one-page commute dashboard on Västtrafik's open API (Planera Resa v4). Static, so it runs on GitHub Pages.

- **Home** (default until 10:30): Källarbacken → Delsjömotet → Gårdatorget or Liseberg station,
  rides leaving Källarbacken 06:00–09:30
- **Office** (default from 10:30): Gårdatorget or Liseberg station → Delsjömotet → Källarbacken,
  rides leaving 15:00–17:30

Rides that have already left stay in the list, greyed out and marked *Departed*, with a *Now* line
before the next one. "Load more" extends the window by 30 minutes. Once a window has passed for the
day, the view shows the next two hours instead. The windows are `WINDOWS` at the top of the script.

Home lists **every** departure from Källarbacken in the window, straight from the stop's departure
board, so no bus is left out. Under each one are the onward connections from Delsjömotet to
Gårdatorget and Liseberg station: the earliest bus you can catch with 2 minutes to change
(`TRANSFER_MINUTES` in `index.html`), or "stay on" when the same bus goes all the way. Buses
that don't stop at Delsjömotet are listed and marked as such. Office lists every bus from
Gårdatorget and Liseberg station towards Delsjömotet, each with its connection home. Realtime
delays and cancellations are shown, and the page refreshes every 30 seconds.

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
