# RTSP Viewer for Ignition — Free Edition v1.0.5

## What's new
- **Now runs on Ignition Maker Edition.** The module opts into Maker compatibility, so home-lab and
  hobbyist installs can run it too — great fit for the free tier. (Standard and trial-mode gateways
  work as before. **Edge** is not supported — Inductive Automation requires Edge modules to be whitelisted.)

---

Native live IP-camera **RTSP** viewing inside **Ignition Perspective**. Configure cameras on the
Gateway, drop the **RTSP Camera Grid** component into a view, and you have a live camera wall — no
browser plugins, no extra ports, credentials never leave the Gateway.

**Free Edition — up to 6 camera feeds.** Perpetual, no time limit.

## Requirements
- **Ignition 8.3+** — standard, **Maker Edition**, or unlicensed trial mode (Edge not supported)
- Cameras providing an **H.264** RTSP stream (switch H.265 cameras to H.264)
- View the wall in a normal browser (Chrome/Edge) — Perspective Workstation lacks the H.264 codec

## Install
1. Gateway → **Config → Modules → Install or Upgrade a Module…** → choose the `.modl`.
2. Self-signed build — accept the one-time certificate prompt (fingerprint in the README).
3. Configure cameras under **Config → Connections → RTSP Cameras**, then add **RTSP Camera Grid**
   to a Perspective view.

Full walkthrough: **HOWTO.pdf** (attached below).

## Upgrade
More feeds are a license key — no reinstall. After purchasing a paid tier, send your Gateway ID
(shown on the License card) to **Support@parsleyautomation.com** and we'll issue your key.
www.parsleyautomation.com
