# RTSP Viewer — v1.2.1 (Free Edition)

Maintenance release. Camera limit handling has been updated so the Gateway applies the edition's feed
allowance consistently when cameras are added or enabled.

No changes to streaming, the Perspective component, or the configuration page layout. Upgrading is a
straight module install over v1.2.0; existing cameras and settings are preserved.

## Requirements
- **Ignition 8.3+** — standard, **Maker Edition**, or unlicensed trial mode
- Cameras providing an **H.264** RTSP stream
- A normal browser (Chrome/Edge) for viewing

## Install
1. Gateway → **Config → Modules → Install or Upgrade a Module…** → choose the `.modl`.
2. Accept the one-time certificate prompt if this is a first install (fingerprint is in the README).
3. **Restart the Gateway** — on Ignition 8.3+ a module install or upgrade takes effect after a restart.

## Editions
The Free edition streams up to **6 cameras**. Paid tiers raise the limit — see the README for details.

> Running **Ignition 8.1**? Use the separate 8.1 build (`RTSPViewer-8.1-Free-*.modl`) instead. License
> keys work on either edition.
