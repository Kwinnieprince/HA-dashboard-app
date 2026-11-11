# Upstream and maintenance

- Project: https://github.com/leodenglovescode/ancienthomeassistant
- Image source: https://github.com/Kwinnieprince/ancienthomeassistant
- Source commit: `f8d1756f9883a8e407f105320ec18a7c1fe8ed09`
- Published image tag: `docker.io/kwintend/ancienthomeassistant:focus-test`
- Multi-platform digest: `sha256:c814a4247e4d3504134389b761708fc9d8c87ce29d2c8d5fa4b428441066b49e`
- Registry manifest verified to include `linux/arm64` and `linux/amd64`.

The base application originates from the project above. This release uses the
contributor's focus-mode fork and the image published to their Docker Hub account.
The wrapper does not copy application source. The original project's licensing
still needs clarification before a contribution is merged or further distribution
arrangements are made.

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
