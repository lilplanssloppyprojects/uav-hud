# ARGOS GCS — UAV Operations Console

A single-file UAV ground control station for the browser: mission planning on a
real map, live vehicle telemetry, and flight commands — designed to an
industry-standard GCS layout with Apple/Anthropic-grade visual restraint.

## Run

Open `index.html` in any browser (internet needed for Leaflet, map tiles, and
the Inter font). No build step. Live demo: the repo's GitHub Pages deployment.

## Layout

- **Top bar** — vehicle selector and state, flight mode switch (HOLD / MISSION /
  RTL), LAND / TAKEOFF / ARM commands with proper enable-disable logic
- **Left rail** — flight instruments (attitude indicator, heading tape, ALT /
  GS / V-S), power (battery, voltage, current, endurance), GNSS and datalink,
  systems health, vehicle info, message feed
- **Center** — full-bleed map (CARTO dark + Esri satellite layers), plan mode,
  follow mode, fit-mission tools
- **Right rail** — mission plan (waypoint list with per-waypoint altitude,
  distance, ETE), survey coverage estimate
- **Status bar** — cursor coordinates, zoom, EKF state, UTC

## Mission planning

Toggle plan mode (`P` or the pencil tool) and click the map to drop waypoints.
Drag markers to refine; set each waypoint's altitude in the list. START MISSION
flies the route at 18 m/s cruise; progress shows on the map and in the
waypoint list.

## Flight logic

Commands validate preconditions and emit SENT → ACK toasts. Landing disarms.
RTL triggers automatically at 15% battery. Vehicle motion respects turn-rate
limits, bank angle, and climb rates, so the attitude instrument and telemetry
behave like a real fixed-wing VTOL.

## Wiring a real vehicle

All vehicle state lives in the `st` object and is mutated only by `simTick()`.
Replace `simTick` with a MAVLink/telemetry websocket feed (or ROS bridge) that
writes the same fields — every instrument, the map, and the command logic will
work unchanged. Command functions (`setMode`, arm/takeoff/land handlers) are
the hooks to forward to your flight stack.
