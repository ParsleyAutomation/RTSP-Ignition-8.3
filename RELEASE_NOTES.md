# RTSP Viewer for Ignition — Free Edition

Native live IP-camera **RTSP** viewing inside **Ignition Perspective**. Configure cameras on the
Gateway, drop the **RTSP Camera Grid** component into a view, and you have a live camera wall — no
browser plugins, no extra ports, credentials never leave the Gateway.

**Free Edition — up to 6 camera feeds.** Perpetual, no time limit.

## Highlights
- **Any RTSP camera** (H.264). Gateway converts RTSP → HLS and reverse-proxies it over the
  Gateway's own web port (TLS + auth, no extra ports).
- **Camera wall component** — Grid / Single / 2-Up / Quad / Hero layouts, rotation, patrol tours,
  bindable full-screen focus + picture-in-picture.
- **Self-healing feeds** — a frozen or choppy tile auto-recovers without a page refresh; long
  kiosk sessions stay live.
- **UniFi Protect extras** (optional) — auto stream-restart and camera reboot when a feed degrades,
  plus a manual per-camera Reboot button.

## Requirements
- Ignition **8.3+**
- Cameras providing an **H.264** RTSP stream (switch H.265 cameras to H.264)
- View the wall in a normal browser (Chrome/Edge) — Perspective Workstation lacks the H.264 codec

## Install
1. Gateway → **Config → Modules → Install or Upgrade a Module…** → choose the `.modl`.
2. This build is **self-signed** — accept the one-time certificate prompt (verify the fingerprint
   in the README).
3. Configure cameras under **Config → Connections → RTSP Cameras**, then add **RTSP Camera Grid**
   to a Perspective view.

Full walkthrough: **HOWTO.pdf** (attached below).

## Assets
- `RtspViewer-<version>.modl` — the module
- `HOWTO.pdf` — install + configuration guide

## Upgrade
More feeds are a license key — no reinstall. Contact **Support@CentralValleyIgnition.com** with
your Gateway ID (shown on the License card) — www.CentralValleyIgnition.com.

_Module version reports as shown in Config → Modules. Use governed by the EULA in this repo._
