<img src="https://raw.githubusercontent.com/ProtossBlaster/leapmotor-mate-addon/main/leapmotor_mate/logo.png" alt="LeapMotor Mate" width="400"/>

# LeapMotor Mate — Home Assistant Add-on

[![Version](https://img.shields.io/github/v/release/ProtossBlaster/leapmotor-mate?label=version&color=14b8a6)](https://github.com/ProtossBlaster/leapmotor-mate/releases)
[![Maintained](https://img.shields.io/badge/maintained-yes-success)](https://github.com/ProtossBlaster/leapmotor-mate/commits/main)
[![Arch](https://img.shields.io/badge/arch-amd64%20%7C%20aarch64-lightgrey)](https://github.com/ProtossBlaster/leapmotor-mate)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](https://github.com/ProtossBlaster/leapmotor-mate/blob/main/LICENSE)

Home Assistant add-on for [**LeapMotor Mate**](https://github.com/ProtossBlaster/leapmotor-mate) — trip tracking, charge logging, charge scheduling, navigation and remote control for Leapmotor vehicles (B10 · C10 · T03).

[![Open your Home Assistant instance and show the LeapMotor Mate add-on.](https://my.home-assistant.io/badges/supervisor_addon.svg)](https://my.home-assistant.io/redirect/supervisor_addon/?addon=5e44ad0d_leapmotor_mate&repository_url=https%3A%2F%2Fgithub.com%2FProtossBlaster%2Fleapmotor-mate-addon)

> 🇮🇹 Versione italiana più sotto.

## Updating an existing installation to Mate 4

Use the normal **Update** action on your existing **LeapMotor Mate** add-on.
The same `leapmotor_mate` slug, configuration and persistent `/data` are retained.
No separate candidate installation, certificate upload, account setup, database
export/import or migration command is required.

Mate checks the independent API automatically before selecting it. Accounts that
cannot qualify, including unsupported REEV or mixed-model accounts, keep the
legacy compatibility API for the whole account. This preserves existing behavior;
it does not add REEV support to the stable add-on. Vehicle commands never cause
fallback or replay through another API.

## Install

**One-click:** click the **My Home Assistant** badge above — it opens *your* Home Assistant, adds this repository and jumps straight to the add-on. Then click **Install** → **Start**.

Or add it manually:

1. In Home Assistant go to **Settings → Apps → Install app** (before 2026.2: **Settings → Add-ons → Add-on Store**).
2. Click the **⋮** menu (top right) → **Repositories**.
3. Add this URL:

   ```
   https://github.com/ProtossBlaster/leapmotor-mate-addon
   ```

4. Find **LeapMotor Mate** in the store, click **Install**, then **Start**.
5. Open the add-on panel (car icon in the sidebar) and follow the setup wizard.

During setup you will:
- upload the Leapmotor **app certificate** (`app.crt` + `app.key`, from [markoceri/leapmotor-certs](https://github.com/markoceri/leapmotor-certs));
- log in with a **dedicated** Leapmotor account (not the one on your phone — the cloud binds one session per device).

See the add-on **Documentation** tab for details.

The database and certificate are stored in the add-on's persistent `/data`, surviving restarts and updates.

---

## 🇮🇹 Add-on Home Assistant

Add-on per [**LeapMotor Mate**](https://github.com/ProtossBlaster/leapmotor-mate) — tracciamento viaggi, registro ricariche, navigazione e controllo remoto per veicoli Leapmotor (B10 · C10 · T03).

### Aggiornare un'installazione esistente a Mate 4

Usa il normale pulsante **Aggiorna** dell'add-on già installato. Slug,
configurazione, account e dati restano gli stessi: non servono una nuova
installazione, certificati, login, esportazioni/importazioni o comandi manuali.
Se l'account non supera la verifica della nuova API, Mate mantiene automaticamente
l'API compatibile precedente per tutte le sue auto.

### Installazione

**Un clic:** clicca il badge **My Home Assistant** in alto — apre *il tuo* Home Assistant, aggiunge questo repository e ti porta direttamente all'add-on. Poi **Installa** → **Avvia**.

Oppure manualmente:

1. In Home Assistant vai su **Impostazioni → Applicazioni → Installa app** (prima della 2026.2: **Impostazioni → Add-on → Store**).
2. Menu **⋮** (in alto a destra) → **Archivi digitali** (prima della 2026.2: **Repository**).
3. Aggiungi questo URL:

   ```
   https://github.com/ProtossBlaster/leapmotor-mate-addon
   ```

4. Trova **LeapMotor Mate** nello store, **Installa**, poi **Avvia**.
5. Apri il pannello (icona auto nella barra laterale) e segui il wizard.

Durante il setup dovrai:
- caricare il **certificato app** Leapmotor (`app.crt` + `app.key`, da [markoceri/leapmotor-certs](https://github.com/markoceri/leapmotor-certs));
- accedere con un account Leapmotor **dedicato** (non quello del telefono — il cloud lega una sessione per dispositivo).

Database e certificato sono salvati nella `/data` persistente dell'add-on (sopravvivono a riavvii e aggiornamenti).

## ☕ Support

LeapMotor Mate is free and open-source. If it's useful to you, you can support its development with a coffee — thank you! · *Se ti è utile, puoi offrirmi un caffè per sostenerne lo sviluppo — grazie!* ☕

<a href="https://www.buymeacoffee.com/protossblaster" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="48"></a>

## License

[GNU AGPL-3.0](./LICENSE) © Silvio Bressani.
