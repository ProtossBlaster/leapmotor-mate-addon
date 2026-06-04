# LeapMotor Mate — Home Assistant Add-on

Home Assistant add-on for [**LeapMotor Mate**](https://github.com/ProtossBlaster/leapmotor-mate) — trip tracking, charge logging, navigation and remote control for Leapmotor vehicles (B10 · C10 · T03).

> 🇮🇹 Versione italiana più sotto.

## Install

1. In Home Assistant go to **Settings → Add-ons → Add-on Store**.
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

### Installazione

1. In Home Assistant vai su **Impostazioni → Add-on → Store**.
2. Menu **⋮** (in alto a destra) → **Repository**.
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
