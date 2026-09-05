# RTSP Viewer for Ignition — Free Edition

Native live IP-camera **RTSP** viewing inside **Ignition Perspective**. Configure cameras on the
Gateway, drop the **RTSP Camera Grid** component into a view, and you have live cameras on screen —
one or many — with no browser plugins, and credentials that never leave the Gateway.

**Free Edition — up to 6 camera feeds.** Perpetual, no time limit.

## Highlights
- **Any RTSP camera** (H.264), delivered two ways:
  - **HLS** (default) — reverse-proxied over the Gateway's own web port (TLS + auth, **no extra
    ports**), works anywhere the Gateway is reachable, a few seconds behind live.
  - **WebRTC** (optional) — **under a second** of latency for same-network viewers. Video goes
    direct over a UDP port; a tile that can't get through falls back to HLS on its own.
- **RTSP Camera Grid component** — Grid / Single / 2-Up / Quad / Hero layouts, rotation, patrol tours,
  bindable full-screen focus + picture-in-picture.
- **Self-healing feeds** — a frozen or choppy tile auto-recovers without a page refresh; long
  kiosk sessions stay live.
- **UniFi Protect extras** (optional) — auto stream-restart and camera reboot when a feed degrades,
  plus a manual per-camera Reboot button.
- **Upgrade by license key** — paste it into the License card. Validated offline on the Gateway, so
  no internet and no reinstall.

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
   in the README).
3. **Restart the Gateway** — on Ignition 8.3+ a module install or upgrade only takes effect after a
   restart.
4. Configure cameras under **Config → Connections → RTSP Cameras**, then add **RTSP Camera Grid**
   to a Perspective view.

Full walkthrough: **HOWTO.pdf** (attached below).

## Assets
- `RtspViewer-<version>.modl` — the module
- `HOWTO.pdf` — install + configuration guide

## Upgrade
More feeds are a license key — no reinstall. Contact **Support@parsleyautomation.com** with
your Gateway ID (shown on the License card) — www.parsleyautomation.com.

_Module version reports as shown in Config → Modules. Use governed by the EULA in this repo._
