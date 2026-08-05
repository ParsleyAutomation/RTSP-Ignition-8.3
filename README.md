# RTSP Viewer for Ignition — Free Edition

View live IP-camera **RTSP** streams natively in **Ignition Perspective**. A gateway-managed
converter turns each camera's RTSP feed into browser-friendly video and plays it in an
**RTSP Camera Grid** component — no browser plugins.

This repo distributes the **free, limited edition** (up to **6 camera feeds**). Paid tiers lift
the limit — see [Editions](#editions).

**Two delivery modes.** **HLS** (the default) rides the Gateway's own web port — no extra ports, works
anywhere the Gateway is reachable, a few seconds behind live. **WebRTC** is optional and gets you
**under a second** of latency, but sends video direct over a UDP port you must open and only works on
the **same network**. See [Low-latency mode](#low-latency-mode-webrtc).

![Live camera wall in a Perspective session](images/camera-wall.png)

*A camera wall running live in a browser Perspective session.*

---

## Download

Get the latest `.modl` from the **[Releases](https://github.com/CVISupport/RTSP/releases)** page.

> This build is **self-signed**. On install, the Gateway shows a one-time certificate prompt —
> review the fingerprint below and accept it. Nothing else is affected.

**Signing certificate — SHA-256 fingerprint** (verify before trusting):
```
FC:62:F4:68:A5:0D:AA:57:D4:6E:B6:05:BE:C0:5E:C9:C4:C3:DE:79:A5:14:02:20:C8:9B:92:07:CD:6A:A1:DF
Subject: CN=Central Valley Ignition, O=Central Valley Ignition, L=Fresno, S=CA, C=US
```

---

## Requirements
- **Ignition 8.3+** — standard, **Maker Edition**, or unlicensed trial mode. *(Edge is not supported —
  IA requires Edge modules to be whitelisted.)*
- Cameras providing an **H.264** RTSP stream (H.265 must be switched to H.264 on the camera)
- View the camera wall in a normal browser (Chrome/Edge). *Perspective Workstation lacks the
  H.264 codec — use a browser.*

## Install (Gateway)
1. Gateway web UI → **Config → Modules** → **Install or Upgrade a Module…**
2. Choose the downloaded `.modl` → **Install** → accept the certificate prompt once.
3. **Restart the Gateway** — on Ignition **8.3+** a module install or upgrade only takes effect after a
   restart. The module then shows **Running** under Config → Modules.

## Add cameras (Gateway)
1. **Config → Connections → RTSP Cameras** → **+ Create new Camera**.
2. Enter a **Name**, the **RTSP URL** (with any credentials), optional substream/zone.
3. Save. Camera URLs/credentials stay on the Gateway — never sent to a browser.
4. Free edition allows **6 enabled cameras**; the 7th is blocked until you upgrade.

![RTSP Cameras config page with the license tier](images/gateway-config.png)

## Add the wall (Designer)
1. Open a **Perspective** view.
2. From the **Central Valley Ignition** palette category, drag **RTSP Camera Grid** onto the view.
3. Leave `cameras` empty to show all, or list cameras by **name**. Save and open a Session.

*In the Designer, tiles show a placeholder — live video only renders in a browser Session:*

![RTSP Camera Grid in the Ignition Designer](images/designer-preview.png)

Full guide: **[HOWTO.pdf](https://github.com/CVISupport/RTSP/releases)** (attached to the release).

---

## Low-latency mode (WebRTC)

By default the wall uses **HLS**, roughly **2–6 seconds** behind live — fine for monitoring, not for
someone reacting to what they see. Switching the grid's `transport` property to `webrtc` drops that to
**under a second**.

What it costs you:

| | HLS *(default)* | WebRTC |
|---|---|---|
| Latency | ~2–6s | **< 1s** |
| Works over internet / VPN | **Yes** | No — same network only |
| Setup | Nothing | Set one property; open a UDP port only if needed |

Only the initial handshake goes through the Gateway; the video itself is sent straight from the
Gateway machine to each browser over a UDP port (default `18189`). Many networks need no firewall
change for this, since the Gateway initiates the connection and the reply returns through the same
opening — but if viewers can't get through, allowing that port inbound fixes it.

A tile that can't establish a connection **falls back to HLS automatically**, so a blocked port means
higher latency rather than a black screen — and the Gateway reports which cameras fell back and why.

Configure it under **Config → Connections → RTSP Cameras → Connectivity**, which also shows the
addresses browsers will be told to use and includes a **Test from this browser** button.

> **Free while in preview.** Low-latency mode is included at no cost in this release. It may move to a
> paid tier in a future version; existing installs will be given notice.

---

## Editions

| Edition | Camera feeds | Notes |
|---------|-------------|-------|
| **Free** | 6 | This download. Perpetual. |
| **Pro** | 24 | Single gateway. |
| **Unlimited** | Unlimited | Single gateway, scales to 100+ feeds. |
| **Integrator** | Unlimited | Multi-gateway + resale/OEM. |

Upgrading is a license key — no reinstall. **[Contact us](#support)** with your Gateway ID
(shown on the License card in the config page) to purchase.

## Support
- Issues / questions: open an **[Issue](https://github.com/CVISupport/RTSP/issues)** or email **Support@CentralValleyIgnition.com**.
- Include your Ignition version and, for camera problems, the camera make/model + stream codec.

## License
Proprietary. Free edition use is governed by **[EULA.md](EULA.md)**. Not open source.

This module bundles two open-source components, used under their own licenses:
[MediaMTX](https://github.com/bluenviron/mediamtx) (MIT) and
[hls.js](https://github.com/video-dev/hls.js) (Apache-2.0). See
**[THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt)** (full license texts also included in the
module). React/React-DOM are provided by the Ignition Perspective runtime and are not bundled.
