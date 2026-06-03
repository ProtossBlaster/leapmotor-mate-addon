# Changelog

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
