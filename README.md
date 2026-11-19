# Yantra Fleet, robot fleet management demo

A clickable, front-end only demo of the fleet app that would ship with a commercial
cleaning robot and a service robot built on one shared hardware platform. It exists to
make one point in a pitch: your robot runs on our software.

Everything is mocked in the browser. There is no backend, no network call and no
dependency apart from Google Fonts. Telemetry, task progress, battery, alerts and
map positions are simulated once per second.

## Open it

- Double-click `index.html`. It works from `file://` in Chrome, Edge, Safari and Firefox.
- Or serve the folder and open it on a phone on the same Wi-Fi:

  ```powershell
  python -m http.server 8080
  ```

  then open `http://<your-pc-ip>:8080/` on the phone or tablet.

- Sign in with any 10 digit mobile number. The OTP is `1234` (any 4 digits work).
- For a pitch, `index.html?demo#live-r1` skips sign-in and opens a screen directly. Screen names:
  `fleet`, `map`, `tasks`, `alerts`, `more`, `assign-r1`, `live-r1`, `robot-r1`, `done-h1`,
  `schedules`, `history`, `reports`, `settings`, `profile`, `about`, `connect`
  (robots are `r1` Mira, `r2` Tara, `r3` Neel, `r4` Riya, `r5` Veer).

Phone first. On a phone there is a bottom tab bar; from 768 px wide (tablets) a left
rail and two-column layouts take over. Tested at 360, 390, 430, 768, 834 and 1024 px.

## What the demo shows

| Screen | What you can do |
| --- | --- |
| Sign in | OTP style login, language picker (English, Gujarati, Hindi) |
| Connect a robot | Scan QR (animated, finds a robot after a moment) or type an ID (`YC-...` cleaning, `YS-...` service), name it, pick site Wi-Fi, watch the pairing steps, success screen |
| Fleet | Summary tiles, robot cards with live status, battery, task progress and location, filters, skeleton loader on first load |
| Map | SVG floor map with zones, cleaning and service paths, moving robot marker with trail, obstacles, dock, tap a zone to send the selected robot there |
| Assign task | Cleaning: zones, quiet / standard / deep, now or later, repeat, estimate. Service: pick-up point, table or room, trays with LEDs, Go / Return. Review sheet, confirm |
| Live task | Progress ring, time left, area or deliveries, pause / resume / stop, return to dock, telemetry tiles, map, event feed |
| Task finished | Summary (time, area or deliveries, battery used, incidents), star rating, share report |
| Alerts | Obstacle stuck, low battery, dustbin full, delivery picked up, e-stop pressed. Each has actions that change robot state |
| Robot detail | Overview (battery and BMS, connectivity, compute, firmware update), Sensors (LiDAR, RGB-D, IMU, ultrasonic, cliff, bumper, encoders with self-check), Maintenance (brush, filter, suction hours, dustbin, tanks, trays, door relay, lift), Safety (e-stop, bumper circuit, watchdog, speed limit, reboot) |
| More | Schedules (toggle, add, run now, delete), task history, reports with charts, settings (language, voice announcements, quiet hours, notifications, max speed), profile, hardware platform summary |

Voice announcements use the browser's speech synthesis when available, in the chosen
language, and always show a toast.

Simulated time runs 12x faster than real time, so a 60 minute cleaning task finishes
in about 5 minutes while you talk.

## Files

- `index.html`: the whole app (HTML, CSS, JS). Single file, no build step.
- `README.md`: this file.

## Conventions

- Light theme only, custom colour tokens at the top of the stylesheet.
- No em dash or en dash characters anywhere in the files.
- `prefers-reduced-motion` turns off the animations.
- All text uses `overflow-wrap`, flex children use `min-width: 0`, sizes use `clamp()`,
  so long names, Gujarati script and large numbers never overlap or clip.
