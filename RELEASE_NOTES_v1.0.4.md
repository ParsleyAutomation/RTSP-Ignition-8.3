# RTSP Viewer for Ignition — Free Edition v1.0.4

## What's new
- **Lay out your full wall on the free tier.** You can now add more cameras than the feed limit —
  the licensed number stream live, and any beyond the limit show as a locked **"Upgrade to unlock
  this feed"** tile (visible in the Designer too). No more being blocked from configuring extra cameras.
- **Reboots self-heal.** When a camera is rebooted (manual button, low-FPS auto-reboot, or last-resort
  recovery), the module now waits for it to come back, **re-acquires its new RTSP address** (UniFi
  rotates the alias on reboot), and re-points the feed automatically — no manual URL fix.
- **Edited camera URLs apply live.** Changing a camera's RTSP URL and saving now re-pulls the new
  source immediately; views no longer keep showing the old stream.
- **`objectFit: contain` top-aligns the wall.** Feeds keep their aspect and pack at the top (dead
  space at the bottom) instead of letterboxing every tile. `fill`/`cover` still cover the whole window.

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
