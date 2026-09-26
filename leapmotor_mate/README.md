# LeapMotor Mate

[![Version](https://img.shields.io/github/v/release/ProtossBlaster/leapmotor-mate?label=version&color=14b8a6)](https://github.com/ProtossBlaster/leapmotor-mate/releases)
[![Project stage](https://img.shields.io/badge/project%20stage-production%20ready-brightgreen)](https://github.com/ProtossBlaster/leapmotor-mate)
[![Maintained](https://img.shields.io/badge/maintained-yes-success)](https://github.com/ProtossBlaster/leapmotor-mate/commits/main)
[![Arch](https://img.shields.io/badge/arch-amd64%20%7C%20aarch64-lightgrey)](https://github.com/ProtossBlaster/leapmotor-mate)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](https://github.com/ProtossBlaster/leapmotor-mate/blob/main/LICENSE)

**Trip tracking, charge logging and remote control for Leapmotor vehicles** — a self-hosted,
privacy-first companion. Think *TeslaMate*, for Leapmotor.

Supported models: **B05 · B10 · C10 · T03** — full-electric (BEV) only, European spec (the Leapmotor lineup distributed by Stellantis/Leapmotor). Not for REEV / range-extender versions.

⚠️ **Use a Leapmotor account dedicated to Mate only** — never signed into another app, add-on, Docker or integration at the same time (Leapmotor allows ~one session per account → concurrent clients evict each other → the car goes offline → missing/inconsistent data). See the **Documentation** tab.

## Updating to Mate 4

Update this existing add-on normally. Its `leapmotor_mate` slug, configuration,
account and persistent data remain in place. No extra installation, certificate
upload, account setup, export/import or migration command is needed. Mate
qualifies the independent API automatically and retains the legacy compatibility
API for the whole account when qualification or model coverage is unavailable,
including mixed-model accounts. This does not add stable REEV support.

## Highlights

- 🚗 **Trips** — automatic detection with GPS track, distance, energy, efficiency and regen
- 🔌 **Charges** — sessions with energy and cost (flat prices or time-of-use bands), wallbox
  pairing and optional automatic "Home" tagging
- 🔋 **Battery health (SoH)** — usable capacity over time, measured from your real charge data
- 🎛️ **Remote control** — climate, locks, windows, seat heating, charge limit, schedules and
  one-touch *prepare car*
- 🏠 **MQTT Discovery** — the car appears in Home Assistant as native entities (sensors,
  binary sensors, GPS tracker, command buttons)
- 🌍 English · Italiano · Français · Deutsch — metric & imperial units

Open the **Web UI** from the sidebar (Ingress — no extra ports needed). Setup and configuration
are described in the **Documentation** tab.

## Links

- 📦 [Project page & full README](https://github.com/ProtossBlaster/leapmotor-mate) — code, screenshots, details
- 📝 [Release notes](https://github.com/ProtossBlaster/leapmotor-mate/releases)
- 🐞 [Report an issue](https://github.com/ProtossBlaster/leapmotor-mate/issues)

## ☕ Support

LeapMotor Mate is free and open-source, developed in my spare time. If it's useful to you, you
can support its development with a coffee — thank you!

<a href="https://www.buymeacoffee.com/protossblaster" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="48"></a>

---

*Unofficial project — not affiliated with or endorsed by Leapmotor.*
