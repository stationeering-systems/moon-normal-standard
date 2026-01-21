# System Documentation

This directory contains operational documentation for key infrastructure used in Power Systems.

## Available Manuals
- **[Power Grid Readiness Checklist](#readiness-checklist)**
- **[Region Control System Operations Manual](./region_operations_manual.md)**
- **[Zone Control System Operations Manual]()**

### Probes
- **[(6) Grid Probe Operations Manager](../../alert/docs/grid_probe_operations_manual.md)**

## Readiness Checklist

This checklist must be completed before full system integration.  It ensures that all power systems are flashed, wired, labeled, and verified.

---

### Zone Control

1. Power on controller
   - Verify that the IC `Setting` shows the sum of all transformers assigned to the network plus uncharacterized loads (`PowerActual` sum of all APCs)
   - Verify that the total does not exceed zone transformer `Maximum`
2. Set the Zone transformer setting to 0
   - Verify that all transformers are off
3. Set the Zone transformer setting to less than requested amount
   - Verify that critical transformers are on and that non-critical loads are shed first
4. Set the Zone transformer setting to greater than or equal the requested amount
   - Verify that all transformers are on

### Region Control

1. Power on controller
   - Verify the IC `Setting` displays a number greater than 0
   - Verify that load assignments are allocated to zones in priority order.  `Setting` >= 1 fulfills all zone requests.