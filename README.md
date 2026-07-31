# RTSP Viewer for Ignition — Free Edition

View live IP-camera **RTSP** streams natively in **Ignition Perspective**. A gateway-managed
converter turns each camera's RTSP feed into browser-friendly video and plays it in an
**RTSP Camera Grid** component — no browser plugins, no extra ports.

This repo distributes the **free, limited edition** (up to **6 camera feeds**). Paid tiers lift
the limit — see [Editions](#editions).

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
- **Ignition 8.3+**
- Cameras providing an **H.264** RTSP stream (H.265 must be switched to H.264 on the camera)
- View the camera wall in a normal browser (Chrome/Edge). *Perspective Workstation lacks the
  H.264 codec — use a browser.*

## Install (Gateway)
1. Gateway web UI → **Config → Modules** → **Install or Upgrade a Module…**
2. Choose the downloaded `.modl` → **Install** → accept the certificate prompt once.
3. Module shows **Running**. No restart needed.

## Add cameras (Gateway)
1. **Config → Connections → RTSP Cameras** → **+ Create new Camera**.
2. Enter a **Name**, the **RTSP URL** (with any credentials), optional substream/zone.
3. Save. Camera URLs/credentials stay on the Gateway — never sent to a browser.
4. Free edition allows **6 enabled cameras**; the 7th is blocked until you upgrade.

## Add the wall (Designer)
1. Open a **Perspective** view.
2. From the **Central Valley Ignition** palette category, drag **RTSP Camera Grid** onto the view.
3. Leave `cameras` empty to show all, or list cameras by **name**. Save and open a Session.

Full guide: **[HOWTO.pdf](https://github.com/CVISupport/RTSP/releases)** (attached to the release).

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
