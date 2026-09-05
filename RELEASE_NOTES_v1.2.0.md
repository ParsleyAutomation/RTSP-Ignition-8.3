# RTSP Viewer for Ignition — Free Edition v1.2.0

## What's new

- **Paid license keys now activate.** Pro, Unlimited and Integrator tiers work on this build.
  Paste a key into the License card — no reinstall, no Gateway restart, no internet needed.
  Time-limited keys lapse on their expiry date on their own.
- **Parsley Automation splash** when the Designer loads.

Free Edition behaviour is unchanged. Upgrading from v1.1.x changes nothing about how your cameras
behave.

> Running an earlier build? Keys are ignored there — upgrade to v1.2.0 before applying one.

## Requirements
- Ignition **8.3+** — standard, Maker Edition, or unlicensed trial mode
- Cameras providing an **H.264** RTSP stream (switch H.265 cameras to H.264)
- View camera feeds in a normal browser (Chrome/Edge) — the supported configuration
- *For the optional WebRTC mode:* viewers on the same network as the Gateway

## Install
1. Gateway → **Config → Modules → Install or Upgrade a Module…** → choose the `.modl`.
2. This build is **self-signed** — accept the one-time certificate prompt (verify the fingerprint in
   the README).
3. **Restart the Gateway** — on Ignition 8.3+ a module install or upgrade only takes effect after a
   restart.

**Free Edition — up to 6 camera feeds.** Perpetual, no time limit.
