# RTSP Viewer for Ignition — Free Edition v1.0.1

## What's new
- **Fixed live-latency drift** on long-running sessions. Feeds left open for many hours no longer
  slowly fall behind real time — playback now stays locked to the live edge automatically.
- Includes the earlier long-session self-healing (frozen/choppy tiles auto-recover without a
  page refresh).

_Recommended update for anyone running always-on camera walls (kiosks, control rooms)._

---

Native live IP-camera **RTSP** viewing inside **Ignition Perspective**. Configure cameras on the
Gateway, drop the **RTSP Camera Grid** component into a view, and you have a live camera wall — no
browser plugins, no extra ports, credentials never leave the Gateway.

**Free Edition — up to 6 camera feeds.** Perpetual, no time limit.

## Requirements
- Standard **Ignition 8.3+** (unlicensed trial mode is fine; **not** supported on Maker Edition —
  Maker doesn't allow third-party modules)
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
