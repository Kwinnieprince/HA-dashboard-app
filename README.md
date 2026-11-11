# HA Dashboard Apps

A Home Assistant app repository providing **Ancient Home Assistant**, a lightweight
web dashboard for older iPads. This is independent packaging of the
[upstream project](https://github.com/leodenglovescode/ancienthomeassistant),
not an official release from its author or Home Assistant.

## Installation

Add this repository through the repositories menu in the Home Assistant app store:

```text
https://github.com/Kwinnieprince/HA-dashboard-app
```

Install **Ancient Home Assistant**, start it, and open `http://YOUR_HA_IP:7654`.
The setup wizard asks for your Home Assistant URL, an access token, and a separate
dashboard password. See the [installation guide](ancient-dashboard/DOCS.md).

## Release status

**1.1.0 — stable packaging release with focus mode.** Initial installation and operation were
confirmed by the repository owner on a Raspberry Pi 5. ARM64 and AMD64 are
supported by the pinned upstream image; AMD64 and backup restoration have not
been tested on actual Home Assistant installations.

Supervisor builds the wrapper locally. This repository maintains only the
packaging; upstream application source is not copied. The application version is
pinned separately from the packaging version.

## Updating from 1.0.0

Refresh the app store and update the existing app to **1.1.0**. Do not uninstall it.
The app ID, storage and port 7654 are unchanged. Create a backup before updating.
In **Settings → This browser**, enable **Hide sidebar** and/or **Hide top bar**.
Use the corner menu button to restore navigation. Preferences are per browser.

This release pins the tested Docker Hub image by immutable digest; future changes
to its `focus-test` tag do not silently change installed app builds.

## Updating from 0.1.0

Upload/push the updated repository, refresh the Home Assistant app store, and
update the existing app to 1.0.0. Do not uninstall it. Existing installations may
retain their previous port mapping: in the app's **Network** settings, set the
host port for **8095/tcp** to **7654**, then restart the app. Stop Retro Panel or
change its port first if it still occupies 7654. Update the iPad bookmark to the
new address. Dashboard data remains in the same persistent directory.

## Maintenance

The Dockerfile references an immutable multi-platform upstream image digest.
See [UPSTREAM.md](UPSTREAM.md) for provenance and the update procedure.
Ingress and automatic Supervisor API access are not included; configuration uses
the existing Ancient setup wizard.

Run the packaging checks locally:

```sh
python3 -m unittest discover -s tests -v
```
