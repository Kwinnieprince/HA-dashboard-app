# Changelog

## 1.1.0

- Adopt the tested focus-mode image from kwintend on Docker Hub, pinned by digest.
- Add per-browser Hide sidebar and Hide top bar preferences with a corner menu.
- Keep port 7654, the existing app ID, and persistent dashboard storage unchanged.

## 1.0.0

- Promote the packaging to stable following confirmed Raspberry Pi 5 operation.
- Change the default external port to 7654; keep internal port 8095.
- Translate repository and installation documentation into English.
- Document the port migration for existing installations and Retro Panel conflicts.
- Keep the same app slug, persistent storage and pinned upstream application.

## 0.1.0

- Initial experimental Home Assistant app packaging.
- ARM64 (including Raspberry Pi 5) and AMD64 support.
- Direct local access on port 8095 and persistent Supervisor storage.
- Pin upstream container by digest to source commit `77c998fc988795e6647160bced029f0f750152b4`.
