# LeapMotor Mate Candidate — 4.0.0-rc.1

An explicitly installed release candidate for Mate's independent API migration.
It has a separate slug and persistent data directory. Installing it neither
upgrades stable **LeapMotor Mate** nor copies stable data.

Back up stable before testing. Stop stable and disable its watchdog and
start-on-boot. Never run both cloud pollers on the same account, including any
Desktop, Docker, phone app, or other integration using that account.

Install **LeapMotor Mate Candidate** explicitly, start it manually, and open its
separate sidebar panel. Follow candidate setup/readiness instructions and the
[backup, import, and rollback procedure](DOCS.md).

To return to stable, stop candidate first, then start the original stable add-on.
Do not restore a migrated candidate database over stable. Candidate-only history
is not merged back automatically.

Image: `ghcr.io/protossblaster/leapmotor-mate:4.0.0-rc.1`, for `amd64` and `aarch64`.
Stable's folder, version, and update channel remain unchanged. Real Home Assistant
ingress, Supervisor access, and startup validation remain pending.
