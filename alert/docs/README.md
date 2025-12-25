# System Documentation

This directory contains operational documentation for key infrastructure used in Vigil Alert Systems.

## Available Manuals

- **[Vigil Alerts Readiness Checklist](#readiness-checklist)**
- **[Sentinel System Operations Manual](./sentinel_operations_manual.md)**
- **[Gateway System Operations Manual](./gateway_operations_manual.md)**
- **[Haven System Operations Manual](./haven_operations_manual.md)**

### Status and Notification Systems

- **[Beacon System Operations Manual](./beacon_operations_manual.md)**
- **[Console System Operations Manual](./console_operations_manual.md)**

### Probes

- **[ARU Probe System Operations Manual](./aru_probe_operations_manual.md)**
- **[Habitat Probe System Operations Manual](./habitat_probe_operations_manual.md)**
- **[Water Probe System Operations Manual](./water_probe_operations_manual.md)**

## Readiness Checklist

This checklist must be completed before full system integration. It ensures that the Vigil Alert control systems are flashed, wired, labeled, and verified.

---

### Sentinel and Beacon Control
_Must have at least one gateway installed_
1. Power on controllers
2. Verify that Sentinel output is 0
3. Verify that Beacon pulses white every 4 seconds

### Gateway Control
1. Power on controller
2. Verify output is 00LLLL

### Probe Control
1. Power on controller
2. Verify output > 0
3. Verify that gateway displays max value when probe > 10
4. Verify that sentinel displays max value when probe > 10
5. Verify beacon state matches max value: [Pulse Rate Guide](https://stationeering.substack.com/i/182428013/pulse-rate-guide)

### Haven Control
1. Power on controller
2. Verify that output reflects [local conditions]()

### Display Control
1. Power on controller
2. Verify target displays show the correct frames: [Display Frame Sequence](https://stationeering.substack.com/i/182428013/display-frame-sequence)