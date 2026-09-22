# RTSP Viewer for Ignition 8.3 — v2.0.0

The module is now published by **Parsley Automation** and licensed through **Ignition's own licensing**.
Because both the publisher and the licensing changed, this is a new major version and a **new module**
on the Gateway rather than an in-place upgrade of v1.x — see [Upgrading from v1.x](#upgrading-from-v1x),
which takes a few minutes and keeps your cameras and your existing views.

## What changed

- **Licensing is Ignition's.** There are no license keys to paste any more. The Gateway's own license
  decides what you get, and a change takes effect immediately, without a restart:
  - **Free** — up to **3 cameras**, perpetual, nothing to install or activate.
  - **Maker Edition** — **unlimited** cameras, free.
  - **Unlimited** — buy *RTSP Viewer Unlimited* from **Parsley Automation** (https://www.parsleyautomation.com),
    then activate it on the Gateway's **Licensing** page like any other Ignition license. Offline
    activation works for air-gapped sites.
- **Perspective is now optional.** Cameras, the configuration page and the new standalone viewer all
  work on a Gateway without the Perspective module installed.
- **Standalone camera wall** at `/res/pa-rtsp/viewer.html` — a plain browser page showing your cameras,
  with no Perspective view to build. Useful for a kiosk, a wall display, or a Vision-only site.
- **New publisher and signing certificate.** The Gateway asks you to trust it once on install; the
  fingerprints are in the README.
- **Camera credentials are protected.** The configuration page no longer shows camera passwords
  (they appear as `***`, and saving a camera back keeps the stored one), and they are encrypted
  in the Gateway's settings files instead of sitting there in plain text - so a screenshot, a
  support bundle or a Gateway backup no longer hands them over. Existing cameras are encrypted
  automatically on first start.
- **Clearer video-server failures.** If another program already holds one of the module's local ports —
  most often a second Gateway on the same machine also running RTSP Viewer — the Gateway log now says
  exactly which port, what it is for and how to move it, instead of silently retrying forever. The
  configuration page shows the same reason while cameras are offline, and everything recovers on its
  own once the port is free.
- **Survives a hard Gateway crash.** A video server left running by a killed Gateway is cleaned up at
  startup instead of blocking every camera.

## Requirements
- **Ignition 8.3+** — standard, **Maker Edition**, or unlicensed trial mode. *(Edge is not supported.)*
  On **Ignition 8.1**, use the [8.1 build](https://github.com/ParsleyAutomation/RTSP-Ignition-8.1).
- Cameras providing an **H.264** RTSP stream (switch H.265 cameras to H.264)
- A normal browser (Chrome/Edge) for viewing
- **Perspective** only if you want the RTSP Camera Grid component in a Perspective view

## Install (new installs)
1. Gateway → **Config → Modules → Install or Upgrade a Module…** → choose the `.modl`.
2. Accept the one-time certificate prompt (verify the fingerprint against the README) and the
   license agreement shown with it. Until both are accepted the Gateway holds the module inactive.
3. **Restart the Gateway** — on 8.3 a module install only takes effect after a restart.
4. Add cameras under **Config → Connections → RTSP Cameras**.

## Upgrading from v1.x

v1.x was published under a different module ID, so the Gateway sees v2.0.0 as a separate module.
**Install the new one first, check it, then remove the old one** — in that order, so your settings can
be carried over.

1. Install `RtspViewer-2.0.0.*.modl` as above and accept the new certificate **and** the license
   agreement (v1.x shipped no agreement, so this prompt is new). Do **not** uninstall v1.x yet.
2. **Restart the Gateway.** On startup the new module copies your v1.x cameras, UniFi NVR settings and
   WebRTC settings across. Nothing is deleted or changed on the v1.x side.
3. Check **Config → Connections → RTSP Cameras**: your cameras should be listed.
4. **Uninstall the old RTSP Viewer** under Config → Modules, then restart the Gateway again.

Notes:
- **Existing Perspective views keep working.** Views built with v1.x refer to the old component type,
  which this version still answers to. You do not need to edit or rebuild any view. New components
  dragged from the palette use the current one.
- **While both are installed**, the two modules compete for the same local video ports, so the Gateway
  log may report a busy port and cameras may stay offline until the old module is removed. That is
  expected, and it clears as soon as the old module is uninstalled and the Gateway restarts.
- **License keys from v1.x are no longer used.** If you were on a paid v1.x tier, see Support below
  before upgrading.
- Cameras beyond the free 3 stay configured but do not stream until the Gateway is licensed; they show
  as locked tiles.

## Assets
- `RtspViewer-2.0.0.<build>.modl` — the module
- `HOWTO.md` — install + configuration guide (in the repo, not attached)

## Support
**Support@parsleyautomation.com** — www.parsleyautomation.com

_Module version reports as shown in Config → Modules. Use governed by the EULA in this repo._
