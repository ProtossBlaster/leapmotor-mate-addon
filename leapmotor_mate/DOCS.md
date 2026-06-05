# LeapMotor Mate

Trip tracking, charge logging and remote control for Leapmotor vehicles (B10 · C10 · T03), running inside Home Assistant.

## Before you start

**Use a dedicated Leapmotor account — not the one on your phone.** The Leapmotor
cloud binds a session per device, so a second client can evict your phone (and
vice-versa). Create a separate account in the Leapmotor app and share the car
with it.

You also need the Leapmotor **app TLS certificate** (the same for everyone, it
identifies the app, not you): the files `app.crt` and `app.key`, available at
**https://github.com/markoceri/leapmotor-certs**. You upload them once in the
setup wizard.

## Setup

1. Start the add-on and open its panel (car icon in the sidebar).
2. **Step 1 — Certificate:** upload `app.crt` and `app.key` (or paste their PEM
   text).
3. **Step 2 — Login:** enter your Leapmotor account email, password and
   operation **PIN**. Your model and battery are auto-detected.

The poller then starts and data begins to appear: overview, trips, charges,
statistics, remote commands and navigation.

## Configuration

The add-on options only expose the log level:

```yaml
log_level: info
```

Everything else (polling interval, charge price, language, currency) is configured
from the web UI under **Settings** — no YAML required.

- **Polling** — parked (default 30 s) and driving (default 10 s). Polling the
  Leapmotor cloud does **not** wake or drain the car.
- **Language & currency** — under **Settings → Language & Currency**, choose the UI
  language and your display currency (€, $, £, CHF… 30 currencies). Every cost
  reformats to it, with the right symbol placement and decimals; the number format
  follows the selected language.

### Charge prices

Set what each kWh costs on the dedicated **Charge Prices** page (💰 in the sidebar).
Pick **Fixed (24h)** — one price per charge type (Home/AC/DC/HPC) — or **Time-of-use
bands**: add time windows, choose the **days of the week** each covers (All / Weekdays
/ Weekend shortcuts), and set a price per charge type for every band. Leave a price
blank to use the base price, or `0` if it's free in that band. A session that spans
two bands is split by its real power curve. Cost changes apply to **new charges
only** — a charge's cost is frozen when you confirm its type.

### Wallbox (optional)

If you charge at home and have a **wallbox already in Home Assistant** (Wallbox
Pulsar, Easee, go-e, Keba, OCPP, …), Mate can pair with it. Enable it in
**Settings → Wallbox present** — as an add-on it connects to Home Assistant
**automatically** (no URL or token needed), regardless of how HA is exposed
(HTTP, HTTPS, Nabu Casa). Then expand **Entity mapping** to assign your wallbox
sensors (Mate pre-selects them and lists only your wallbox's own entities).

You get a dedicated **Wallbox** page with a live panel (power, status, session
energy, charging speed, max available power), a control to set the wallbox max
charging current, and an **AC-vs-DC comparison** per charge session — what the
wallbox delivers (AC) vs what the car receives into the battery (DC), with the
charging efficiency, as a year/month/day history.

### Navigation

The **Navigation** page lets you search an address (street + city), preview it on
the map, and **send the destination straight to the car's built-in navigation** —
it appears in the vehicle's nav system, no PIN required. The page also shows the
car's **current address** (reverse-geocoded from its GPS).

Address lookup works out of the box with a free OpenStreetMap-based provider (no
key). For better street/house-number coverage you can optionally choose a provider
and paste an API key under **Settings → Address lookup**:

- **Geoapify** — recommended (free, no credit card, includes house numbers)
- **LocationIQ** or **TomTom**

If a keyed provider errors, Mate automatically falls back to the keyless lookup.

### MQTT → Home Assistant (optional)

Publish the car to Home Assistant as **native entities** (alongside the Mate UI)
via MQTT Discovery. In **Settings → MQTT**, enable it and enter your broker (host,
port, username/password; TLS optional) — use **Test connection** to verify it before
saving. Home Assistant auto-creates a *Leapmotor Mate* device with sensors, binary
sensors (doors/windows/lock/charging), a GPS tracker, command buttons (lock/unlock,
trunk, find car) and climate buttons — Quick Cool / Quick Heat / Defrost / A/C Off
(turning the A/C fully off is best-effort; the cloud doesn't always honour it). After
a command the state updates immediately.
The **topic prefix** scopes the device, so a second instance on a different prefix
won't clash with this one.

## Data & persistence

The SQLite database and the uploaded certificate live in the add-on's
persistent `/data` directory, so they survive restarts and updates.

Your stored secrets (Leapmotor password/PIN, and any Home Assistant / ABRP /
MQTT / geocoder tokens) are **encrypted at rest** with a per-install key at
`/data/secret.key`, generated automatically on first start. **Keep `secret.key`
with your backups** — a database restored without it can't be decrypted and the
add-on will ask you to re-enter your credentials.

## Notes

This is an unofficial project, not affiliated with Leapmotor. It uses
reverse-engineered cloud APIs and may break if Leapmotor changes them. Use at
your own risk.

Source & full docs: https://github.com/ProtossBlaster/leapmotor-mate
