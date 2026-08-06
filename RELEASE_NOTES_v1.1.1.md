# RTSP Viewer for Ignition — Free Edition v1.1.1

A housekeeping release. **No changes to video delivery, licensing, or the Perspective component** —
this is the Gateway configuration page, made considerably simpler to read, plus documentation for
running in Perspective Workstation.

Upgrading from v1.1.0 changes nothing about how your cameras behave.

## Simpler configuration pages

Both cards on **Config → Connections → RTSP Cameras** had grown into walls of explanation. They now
lead with the controls and keep the detail one hover away.

**UniFi Protect NVR**
- The **Enabled** switch moved into the card header, so you can see whether NVR recovery is on
  without expanding the card.
- Credentials, then a clearly separated **Permission to** section listing exactly what the module may
  do — restart a stream, reboot a camera, verify TLS.
- Explanatory paragraphs became tooltips.

**Connectivity — video delivery**
- Three paragraphs of WebRTC background reduced to one line.
- The advertised addresses now mark which are actually reachable by other machines and which are
  loopback-only, instead of leaving you to work it out from the numbers.
- **UDP port** and **Advertised hosts** sit side by side, with an **ⓘ** carrying the firewall detail.

## Account login for UniFi Protect

The NVR card no longer offers an API key. The account login can do strictly more — in particular, a
UniFi API key **cannot reboot a camera**, and a physical reboot is what clears most FPS and connection
faults. Offering both steered people toward the option that usually couldn't fix their problem.

**If you already configured an API key, it keeps working.** The Gateway still honors a stored key; it
just can't be set from the page anymore.

## Documentation: Perspective Workstation

The README now has a **Perspective Workstation** section. In short: the module works there, but
Workstation's embedded browser ships with H.264 playback disabled, so tiles stay black until you
enable it in your own Workstation installation.

The module ships no codec, performs no transcoding, and modifies no Inductive Automation software. If
you choose to enable H.264 playback, any licensing obligations that come with it are yours to
determine and meet. Read the section before doing so.

## Fixes

- **Number fields were unstyled** on the configuration page — the UDP port box used browser defaults
  and didn't line up with the field beside it.
- Documentation no longer describes the component as a "camera wall". It does Single, 2-Up, Quad and
  Hero layouts as well as Grid, and plenty of views hold exactly one camera.

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
