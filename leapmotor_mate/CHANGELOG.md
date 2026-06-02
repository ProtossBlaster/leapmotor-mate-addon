# Changelog

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
