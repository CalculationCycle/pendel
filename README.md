# Pendel

A one-page commute dashboard on Västtrafik's open API (Planera Resa v4). Static, so it runs on GitHub Pages.

- **Home** (default until 10:30): Källarbacken → Delsjömotet → Gårdatorget or Liseberg station
- **Office** (default from 10:30): Gårdatorget or Liseberg station → Delsjömotet → Källarbacken

Each first bus is paired with the earliest bus from Delsjömotet you can still catch (2 minutes to
change, `TRANSFER_MINUTES` in `index.html`). Direct buses are listed too. Realtime delays and
cancellations are shown, and the page refreshes every 30 seconds.

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
