# ARGUS // STRATOFORGE-7 — Hypersonic UAV Control HUD

A single-file 3D web experience: a classified military command terminal for the
SR-72 "Stratoforge" hypersonic unmanned aerial vehicle. Retro phosphor-green
CRT aesthetic, modern real-time 3D graphics (Three.js).

## Run

Open `index.html` in any modern browser (internet required for the Three.js CDN
and the terminal font — everything else is self-contained). No build step.

## Features

- **Boot / auth sequence** — typed secure-uplink handshake before the HUD arms
- **3D scene** — wireframe holographic globe with fresnel atmosphere glow,
  a delta-wing UAV flying a closed Catmull-Rom orbital track with an additive
  plasma trail, starfield, dashed flight path, engine glow that scales with heat
- **Live telemetry** — Mach, velocity, altitude, heading, pitch/roll, AoA,
  G-load, lat/lon, throttle, fuel, skin thermal load, coolant flow
- **Propulsion stages** — PRE-FLIGHT → BOOST → CRUISE → DASH → RTB
  (`[L]` or the ignition button); DASH pushes Mach 9.6 and triggers
  THERMAL CRITICAL alerts with camera shake
- **Tactical radar** — sweeping canvas radar with fading contacts (hostiles in red)
- **Systems toggles** — ECM jammer, stealth skin (dims airframe edge glow),
  weapons arm (red alert LED), autopilot (`[1]`–`[4]`)
- **Waypoint sequencing** — nav waypoints count down and auto-advance
- **UI extras** — draggable-orbit / zoomable camera, mouse tracking reticle,
  encrypted system log feed, mission clock + UTC, FPS readout, scanlines,
  vignette, CRT flicker, rolling sweep line, WebAudio blips
