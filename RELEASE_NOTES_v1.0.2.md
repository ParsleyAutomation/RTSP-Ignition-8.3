# RTSP Viewer for Ignition — Free Edition v1.0.2

## What's new
- **Designer preview no longer tries to load feeds.** In the Ignition Designer, camera tiles now
  show a labeled placeholder ("Live video appears in a browser session") instead of endless
  "Connecting…" tiles. The Designer's embedded browser can't decode the video, so this removes the
  wasted connections and the piled-up/duplicated tiles some layouts showed while designing.
- Includes the v1.0.1 fix for live-latency drift on long-running sessions, and the long-session
  self-healing for frozen/choppy feeds.

_Camera feeds display normally in a Perspective Session (browser) — this only changes the Designer._

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
