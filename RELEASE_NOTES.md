# RTSP Viewer for Ignition 8.3 — v2.0.0

Native live IP-camera **RTSP** viewing inside **Ignition Perspective**. Configure cameras on the
Gateway, drop the **RTSP Camera Grid** component into a view, and you have live cameras on screen —
one or many — with no browser plugins, and credentials that never leave the Gateway.

**Free — up to 3 camera feeds.** Perpetual, no time limit. **Maker Edition gets unlimited cameras**,
also free. To go beyond 3 on a standard Gateway, buy **RTSP Viewer Unlimited** from **Parsley
Automation** (https://www.parsleyautomation.com) and activate it on the Gateway's Licensing page — there are no
license keys to paste, and the new limit applies immediately.

## Highlights
- **Any RTSP camera** (H.264), delivered two ways:
  - **HLS** (default) — reverse-proxied over the Gateway's own web port (its TLS, **no extra
    ports**; viewing is open to anonymous sessions so a kiosk works without a login - set
    `-Drtsp.requireAuth=true` to require one), works anywhere the Gateway is reachable, a few seconds behind live.
  - **WebRTC** (optional) — **under a second** of latency for same-network viewers. Video goes
    direct over a UDP port; a tile that can't get through falls back to HLS on its own.
- **RTSP Camera Grid component** — Grid / Single / 2-Up / Quad / Hero layouts, rotation, patrol tours,
  bindable full-screen focus + picture-in-picture.
- **Self-healing feeds** — a frozen or choppy tile auto-recovers without a page refresh; long
  kiosk sessions stay live.
- **UniFi Protect extras** (optional) — auto stream-restart and camera reboot when a feed degrades,
  plus a manual per-camera Reboot button.
- **Camera credentials are protected.** The configuration page no longer shows camera passwords
  (they appear as `***`, and saving a camera back keeps the stored one), and they are encrypted
  in the Gateway's settings files instead of sitting there in plain text - so a screenshot, a
  support bundle or a Gateway backup no longer hands them over. Existing cameras are encrypted
  automatically on first start.
- **Standalone camera wall** at `/res/pa-rtsp/viewer.html` — a plain browser page for a kiosk or wall
  display, with no Perspective view to build. Perspective is optional; without it, everything else
  still works.

## Requirements
- Ignition **8.3+**
- Cameras providing an **H.264** RTSP stream (switch H.265 cameras to H.264)
- View camera feeds in a normal browser (Chrome/Edge) — the supported configuration. Perspective
  Workstation can display them too, but does not play H.264 out of the box; see the README section
  **Perspective Workstation** for what that involves and who is responsible for licensing it.
- *For the optional WebRTC mode:* viewers on the same network as the Gateway

## Install
1. Gateway → **Config → Modules → Install or Upgrade a Module…** → choose the `.modl`.
2. This build is **self-signed** — accept the one-time certificate prompt (verify the fingerprint
   in the README), and accept the license agreement shown beside it. The module will not start until
   both are accepted.
3. **Restart the Gateway** — on Ignition 8.3+ a module install or upgrade only takes effect after a
   restart.
4. Configure cameras under **Config → Connections → RTSP Cameras**, then add **RTSP Camera Grid**
   to a Perspective view.

Full walkthrough: **HOWTO.md** in the repo.

## Assets
- `RtspViewer-<version>.modl` — the module
- `HOWTO.md` — install + configuration guide (in the repo, not attached)

## More cameras
Buy **RTSP Viewer Unlimited** from **Parsley Automation** (https://www.parsleyautomation.com) and activate it on
the Gateway's **Licensing** page. No reinstall, no restart, nothing to paste into the module. Questions:
**Support@parsleyautomation.com** — www.parsleyautomation.com.

## Upgrading from v1.x
v1.x used a different module ID, so v2.0.0 installs alongside it rather than over it. Install v2.0.0,
restart (your cameras and settings are carried over automatically), check them, then uninstall the old
module and restart again. Existing Perspective views keep working untouched. Full steps:
**RELEASE_NOTES_v2.0.0.md**.

_Module version reports as shown in Config → Modules. Use governed by the EULA in this repo._
