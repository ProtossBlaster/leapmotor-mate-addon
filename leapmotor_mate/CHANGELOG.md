# Changelog

## 1.5.1

- **Configurable charge-detection threshold** — set the minimum charging current that counts as charging in **Settings → Charge detection** (0.5–16 A, default 2 A). Useful for low-power/experimental supplies; applied live by the poller. Thanks @hubcasale (#5).
- Installs leapmotor-mate `v1.5.1`.

## 1.5.0

- **New Navigation page** 🧭 — search an address and send the destination straight to the car's built-in navigation; also shows the car's current address. Keyless address lookup by default (OpenStreetMap), with an optional provider + API key (Geoapify recommended — free, no card) for better house-number coverage.
- Add a **"Free" charge type** (cost recorded as €0.00) and make charge-type labels language-neutral (🏠 Home · 🔌 AC · ⚡ DC · 🚀 HPC · 🆓 FREE).
- Fix the "charges to confirm" banner sticking while a charge is in progress.
- Auto-detect wallbox power/energy units (W→kW, Wh→kWh) across live, comparison and the power chart.
- Installs leapmotor-mate `v1.5.0`.

## 1.4.0

- Add German (Deutsch) as a fully supported UI language, selectable in Settings and the setup wizard. 🇩🇪
- Localize month names in the Trips / Charges / Statistics / Wallbox history tables (they were always shown in English).
- Installs leapmotor-mate `v1.4.0`.

## 1.3.2

- Fix tyre pressures shown on the wrong wheels (corrected B10 signal→wheel mapping).
- Remove the bogus "outside temperature" (that signal is the seat-ventilation level; no ambient signal exists).
- Installs leapmotor-mate `v1.3.2`.

## 1.3.1

- Lower the charge-detection threshold (3.0 A → 2.0 A) so low-power home charges are still detected.
- Installs leapmotor-mate `v1.3.1`.

## 1.3.0

- **ABRP live telemetry** (optional): forward live data to A Better Route Planner for live route planning — enable it and paste your ABRP token in Settings.
- **MQTT → Home Assistant** (optional): publish the car to HA via MQTT Discovery as native entities (sensors, binary sensors, GPS tracker) plus command buttons and a climate switch. Configure a broker in Settings; TLS supported.
- Installs leapmotor-mate `v1.3.0`.

## 1.2.0

- Wallbox comparison is now scoped to **Home** charges, so it stays correct with multiple EVs on one wallbox and with public/away charging. The live panel shows session data only while the car is plugged in.
- **Charge type confirmation**: a new charge shows a "To confirm" badge (with a "What type of charge?" prompt) instead of silently defaulting to Home; it enters the wallbox comparison only once confirmed as Home.
- Installs leapmotor-mate `v1.2.0`.

## 1.1.1

- Fix: the optional Wallbox feature now works in add-on mode. The Supervisor token wasn't reaching the app process (s6-overlay keeps it out of the service environment), so the add-on showed the standalone URL/token form and couldn't connect. It now connects to Home Assistant automatically — green status, no URL or token needed.
- Installs leapmotor-mate `v1.1.1`.

## 1.1.0

- **Wallbox integration (optional).** Pair a wallbox already in Home Assistant to get a dedicated Wallbox page: live panel (power, status, session energy, charging speed, max available power) + session cost, a max-current control, and an AC-vs-DC comparison per charge session (kWh delivered vs into the battery + efficiency) as a year/month/day history. As an add-on it connects to HA automatically — no URL or token needed. Enable it in Settings → Wallbox present.
- This add-on now requests the `homeassistant_api` permission (needed by the Wallbox feature to read entities/history and set the charging current).
- Trips page redesign, Vehicle page restyle, three-column Settings.
- Installs leapmotor-mate `v1.1.0`.

## 1.0.8

- Charges page: expandable per-session charging-power chart (power over time + SOC).
- Settings: tidier masonry layout (removed the empty gap between cards).
- Installs leapmotor-mate `v1.0.8`.

## 1.0.7

- Language can now be changed from the Settings page (not only in the setup wizard), so already-installed users can switch between English, Italian and French.
- Installs leapmotor-mate `v1.0.7`.

## 1.0.6

- French language added (🇫🇷). The setup wizard now offers English, Italian and French, and the whole app is translated.
- Installs leapmotor-mate `v1.0.6`.

## 1.0.5

- Poller now self-recovers: if the account TLS certificate temp file disappears (poller stuck erroring for hours), it forces a re-login to re-create it. Fixes the add-on freezing until a manual restart.
- Installs leapmotor-mate `v1.0.5`.

## 1.0.4

- Trip/charge times now shown in local time (was UTC).
- Trip detection now gear-based, matching HA: a trip ends on gear P held ~1 min and trips < 0.5 km are ignored (no more fragmented drives).
- Installs leapmotor-mate `v1.0.4`.

## 1.0.3

- Statistics: "Consumption trend (6 weeks)" chart legend dates now shown as `DD/MM` (was `MM-DD`).
- Installs leapmotor-mate `v1.0.3`.

## 1.0.2

- New **Vehicle** page: tyre pressure, doors, windows, panoramic roof and temperatures (gradient status cards).
- `find_car` fix.
- Installs leapmotor-mate `v1.0.2`.

## 1.0.1

- Home Assistant ingress support: the web UI now works correctly inside the add-on panel.
- Installs leapmotor-mate `v1.0.1`.

## 1.0.0

- First public release.
- Trip tracking, charge logging (AC/DC), regen, statistics from the Leapmotor cloud.
- Remote control: lock, windows, trunk, panoramic roof, climate, find car, battery preheat.
- Two-step setup wizard: app certificate + account login, with EU model/battery auto-detect.
- Configurable polling (parked/driving), bilingual UI (EN/IT).
- Installs leapmotor-mate `v1.0.0` from the main repository.
