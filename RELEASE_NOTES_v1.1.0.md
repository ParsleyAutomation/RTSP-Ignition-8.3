# RTSP Viewer for Ignition — Free Edition v1.1.0

## What's new

### Low-latency mode (WebRTC) — optional, free while in preview
The camera wall can now deliver video over **WebRTC** instead of HLS, cutting latency from roughly
**2–6 seconds to under a second**.

Turn it on per view: set the **RTSP Camera Grid**'s new **`transport`** property to `webrtc`.
HLS remains the default, so **upgrading changes nothing** until you opt in.

The trade-off is how the video travels. With HLS, everything goes through the Gateway's normal web
port. With WebRTC, only the handshake does — the video is sent **straight from the Gateway machine to
each browser over a UDP port** (default `18189`), and viewers must be on the **same network**. It does
not work over the internet or most VPNs.

Many networks need no firewall change: the Gateway reaches out to each viewer first, and the reply
returns through the same opening. If viewers can't connect, allowing that UDP port inbound on the
Gateway machine resolves it.

**If it can't get through, it falls back to HLS on its own.** A blocked port means lower-latency video
is unavailable, not that the camera goes dark — and the Gateway tells you it happened rather than
leaving you to guess.

> Low-latency mode is free in this release. It may move to a paid tier in a future version; existing
> installs will be given notice.

### New Connectivity page
**Config → Connections → RTSP Cameras → Connectivity — video delivery** shows:
- the **UDP port** to open, and the exact **addresses** browsers will be told to connect to
  (so you can tell whether viewers can actually reach this Gateway);
- live **viewer counts per transport**, straight from the media server;
- any cameras that **fell back to HLS**, and why;
- a **Test from this browser** button that opens a real connection and reports whether video arrived.

### Also in this release
- **New `showTransport` property** — a per-tile badge naming the transport actually in use
  (`WEBRTC`, `HLS`, or an amber `HLS` when a tile fell back). Useful while setting low-latency mode up.
- **Faster tile expand/collapse.** Clicking a tile to enlarge it no longer tears down and rebuilds the
  player, so switching between the wall and a single camera is now instant.
- Tiles no longer request an audio stream when muted (which is the default), saving bandwidth on a
  wall of cameras.

---

Native live IP-camera **RTSP** viewing inside **Ignition Perspective**. Configure cameras on the
Gateway, drop the **RTSP Camera Grid** component into a view, and you have a live camera wall — no
browser plugins, credentials never leave the Gateway.

**Free Edition — up to 6 camera feeds.** Perpetual, no time limit.

## Requirements
- **Ignition 8.3+** — standard, **Maker Edition**, or unlicensed trial mode (Edge not supported)
- Cameras providing an **H.264** RTSP stream (switch H.265 cameras to H.264)
- View the wall in a normal browser (Chrome/Edge) — Perspective Workstation lacks the H.264 codec
- *For low-latency mode only:* viewers on the same network, and one **UDP port** open on the Gateway

## Upgrading from v1.0.5
Install over the top — camera configuration, license keys and existing views carry across unchanged,
and every view keeps using HLS exactly as before until you set `transport` yourself.

Three things to know:
- **Restart the Gateway after installing.** On Ignition 8.3+ a module upgrade only takes effect after a
  restart; until then the previous version keeps running.
- **Close and reopen the Designer** so it picks up the new `transport` / `showTransport` properties.
- **Hard-refresh** open Perspective sessions (Ctrl+Shift+R) so browsers load the new component code.

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
