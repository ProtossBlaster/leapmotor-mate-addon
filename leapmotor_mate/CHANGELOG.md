# Changelog

## 1.8.2

- **Fix: shared cars now report live data.** A car *shared* to your account (the recommended setup — a separate account from your phone, with the car shared to it) could leave the poller stuck on *"Vehicle returned no live data"* forever, even while driving, because the Leapmotor cloud needs the `carId` in the status request for shared cars. Mate now sends it automatically when a shared car comes back empty, and the log shows `shared: true/false` so this is diagnosable. (Reported on the T03 in #9.)
- **Encrypted credentials at rest.** Your Leapmotor password/PIN and the other stored secrets (Home Assistant, ABRP, MQTT, geocoder) are now encrypted in the local database with a per‑install key (`/data/secret.key`, auto‑generated). Existing installs migrate transparently on the next start — no re‑login. **Keep `secret.key` with your backups**: a database restored without it will ask you to re‑enter the credentials.
- **Optional database pruning** (Settings → Database) — cap raw GPS‑sample storage to 6/12/18/24 months; old non‑charging samples are pruned daily while trips and charge curves are always kept. Off by default. The page also shows the current database size.
- **Data export & backup** (Settings → Export) — download Trips and Charges as CSV and a full database backup; each trip page now has a GPX download of its GPS track.
- **Health endpoint** `/healthz` (+ Docker HEALTHCHECK) — a wedged poller is now visible instead of data silently stopping.
- **Faster charge/Wallbox history** as the database grows over the years (new telemetry index).
- **Fix: regen energy** now scales with the configured driving poll interval instead of a hardcoded 10 s; **trip efficiency** is no longer stored as a negative value after a regen / cloud SOC blip.
- **Hardening:** stored secrets are masked (not rendered back) in the Settings page; MQTT commands are thread‑safe; a clear warning is shown if the encryption key is missing/wrong at startup.
- Installs leapmotor-mate `v1.8.2`.

## 1.8.1

- **Climate over MQTT is now four buttons** — *Quick Cool*, *Quick Heat*, *Defrost* and *A/C Off* — instead of a single on/off switch (which only ran the ventilation fan and whose OFF did nothing). Turning the A/C fully **off** is best-effort: the vehicle cloud doesn't reliably honour it (an open issue with the Leapmotor API). The old switch is removed from Home Assistant automatically; the read-only *Climate* state sensor stays. (Reported in #14)
- **Malaysian Ringgit (MYR)** added to the display currencies. (Requested in #13)
- **Fix: Recent Trips on the Overview showed UTC** instead of your local time; it now matches the Trips page. (#12)
- **Quieter logs when the car is asleep** — the deep-sleep back-off is logged once instead of every cycle with a climbing "after N tries" count.
- Installs leapmotor-mate `v1.8.1`.

## 1.8.0

- **Customizable display currency.** The euro is no longer hardcoded — pick your currency from **30 world currencies** (€, $, £, CHF, kr, zł, Ft, ¥, …) in **Settings → Language & Currency**. Every cost (Overview, Charges, Wallbox, totals) reformats to it, with the correct symbol placement (`$12.50` vs `12,50 €`) and decimal digits per currency (2 for most, 0 for yen/forint/won). The number format follows the selected UI language. _(Requested in #10.)_
- Installs leapmotor-mate `v1.8.0`.

## 1.7.1

- **Fix the alarming `Poll error: 'signal'` when the car is asleep.** If the cloud returned a status without live data (car in deep sleep / not reporting, or a brief cloud hiccup), the poller logged a scary error that looked like a crash. It's now handled cleanly — a clear "vehicle not reporting (asleep/unavailable)" message, a couple of retries, then a back-off — and recovers on its own once the car reports again. (#9)
- Installs leapmotor-mate `v1.7.1`.

## 1.7.0

- **New Charge Prices page with time-of-use tariffs.** Choose flat (24h) pricing or **time-of-use bands**: add time windows, pick the **days of the week** each applies to (All / Weekdays / Weekend), and set a price per charge type (Home/AC/DC/HPC) for each. Blank = base price, `0` = free. Each session is costed by splitting its energy across the bands it spans. Cost changes apply to **new charges only** (a charge's cost is frozen when you confirm its type). _(Requested in #7.)_
- **MQTT: state now syncs right after a command.** Lock/unlock/trunk/climate sent over MQTT now update in Home Assistant immediately instead of waiting for the next poll (up to 30 s when parked).
- **MQTT: fixed inverted lock state** — a locked car showed as "Unlocked" in Home Assistant; now correct.
- **MQTT: "Test connection" button** in Settings → MQTT to verify the broker before saving.
- **MQTT: topic prefix scopes the HA device** — run a second instance on a different prefix without clashing with the first (default prefix unchanged).
- Installs leapmotor-mate `v1.7.0`.

## 1.6.3

- Vehicle page redesigned with **Material Design icons** (doors, trunk, windows, roof, tyres, temperatures) instead of emoji — windows even switch between open/closed icons.
- Panoramic roof shows its **real state** (read live from the car, like the Commands page) instead of "no data".
- Version number now visible on mobile (top bar).
- Installs leapmotor-mate `v1.6.3`.

## 1.6.2

- **Fix wrong clock times for users outside Italy** — the UI now uses your Home Assistant timezone instead of a hardcoded Europe/Rome fallback. Recommended update if you're not in Italy.
- Overview "State" follows the gear (a stop in traffic = "Driving", not "Parked").
- Panoramic roof shows "Operate first" instead of "No data" when its position is unknown (B10 limitation).
- Installs leapmotor-mate `v1.6.2`.

## 1.6.1

- **Fix poller regression (since 1.5.1):** the charge-detection setting was applied with a wrong call that errored every cycle, so the poller stopped collecting data. Polling/trip/charge detection restored — **update strongly recommended** if you were on 1.5.1 or 1.6.0.
- Fix the setup PIN field: the Leapmotor operation PIN is **4 digits**, not 6.
- Installs leapmotor-mate `v1.6.1`.

## 1.6.0

- **Responsive layout for phones and tablets** — on small screens the sidebar becomes a slide-out drawer with a hamburger menu and the content reflows to full width. Desktop layout unchanged. Contributed by @hubcasale (#6) — thanks!
- Installs leapmotor-mate `v1.6.0`.

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
