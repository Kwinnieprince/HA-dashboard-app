# Upstream and maintenance

- Project: https://github.com/leodenglovescode/ancienthomeassistant
- Source commit: `77c998fc988795e6647160bced029f0f750152b4`
- Published image tag: `ghcr.io/leodenglovescode/ancienthomeassistant:sha-77c998fc988795e6647160bced029f0f750152b4`
- Multi-platform digest: `sha256:c3aa8fa5f2012779c41114a09ca5275ec2df37c4334b22f48fe02dfb5c12b011`
- Registry manifest verified to include `linux/arm64` and `linux/amd64`.

No explicit LICENSE file was found in the upstream checkout at this commit.
This repository therefore does not vendor the application source, assert a license
for it, or publish rebuilt container images. It references the image published by
its author. Confirm the author's licensing and contribution preferences before
redistributing application code/images or opening an upstream packaging PR.

## Updating

1. Review the new upstream source, Dockerfile and release notes.
2. Verify its published manifest supports ARM64 and AMD64.
3. Update the pinned digest and source commit in the Dockerfile and this document.
4. Confirm the upstream user is still UID/GID 10001, Python is available, and
   `/app/server.py`, `--data-dir`, and `/api/status` retain their behavior.
5. Run wrapper tests, then build and run the container for the target platform.
6. Test setup, existing data, restart, camera snapshots and actual legacy Safari.
7. Bump the add-on version and changelog. Upload the repository only after review.

A minimal container smoke test (with Docker installed):

```sh
docker build -t ancient-ha-addon ./ancient-dashboard
docker run --rm -p 8095:8095 -v ancient-ha-addon-test:/data ancient-ha-addon
```

Open port 8095, finish setup with a test HA user, stop/restart with the same volume,
and confirm the layout persists. A real Supervisor install is still required to
validate repository discovery, watchdog, backups and restore.
