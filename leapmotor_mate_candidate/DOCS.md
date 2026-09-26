# Testing Mate 4 safely

## Back up stable first

1. In stable Mate, use **Settings → Export** to download the full database
   (`leapmotor_mate.db.gz`). Keep the file outside Home Assistant.
2. Stop stable. Disable its start-on-boot and watchdog during testing.
3. Create and download a Home Assistant backup including the stable add-on.
   Keep any encryption/recovery information needed to restore it. The database
   export does not contain the matching `secret.key`, certificates, or private
   material; retain the complete add-on backup for recovery.
4. Keep stable installed and preserve its data. Do not replace its database with
   the migrated candidate database.

## Opt in and import history

Install **LeapMotor Mate Candidate** from this repository. Its unique slug is
`leapmotor_mate_candidate`; its `/data` belongs to this add-on alone. Startup is
manual by default. Do not enable simultaneous startup of stable and candidate.

Start candidate and open **Mate Candidate** in the sidebar. Follow its setup and
readiness instructions for application/account material and your dedicated
account. Do not assume the old application certificate alone satisfies readiness.
Never run both cloud pollers on one account. Also stop Desktop/Docker, phone apps,
and other integrations using it; separate data directories do not isolate sessions.

After setup, import the stable export through the database restore control in
candidate **Settings → Export**. Restore replaces candidate's database and
restarts its services. Verify trips, charges, settings, readiness, and polling.
Check MQTT and wallbox settings before allowing candidate to publish or control
devices.

Mate 4 creates a one-time backup under `/data/migration-backups/mate-4.0.0` before
first non-demo startup. For a fresh candidate it may contain no historical
database. It does not replace your stable backup and is not refreshed for each
subsequent UI database import.

## Return to stable

1. Stop candidate and disable its watchdog/start-on-boot settings if enabled.
2. Start the original stable add-on; its data remains separate.
3. If stable data was lost or changed outside this procedure, restore stable
   from the pre-test Home Assistant backup. Restore the original database with
   its matching secrets, then start stable.
4. Re-enable stable's usual startup settings after confirming it works.

Records created during testing remain in candidate. There is no automatic reverse
migration or history merge into stable. Preserve a candidate backup before removing
it if those records are needed.

## Publication and platform validation

Supervisor combines `image: ghcr.io/protossblaster/leapmotor-mate` with
`version: 4.0.0-rc.1`. The Mate repository must publish that exact tag for both
`amd64` and `aarch64` before this folder is distributed. There is no local Docker
build here. See the [Home Assistant configuration reference](https://developers.home-assistant.io/docs/apps/configuration/).

Real Home Assistant testing remains pending: validate image pull, ingress,
persistent data, Supervisor API access, restart, backup restore, and return to
stable on target hardware.
