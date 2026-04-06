# System Documentation

This directory contains operational documentation for key infrastructure used in Trade Systems.

## Available Manuals
- **[Trade Systems Readiness Checklist](#readiness-checklist)**

### Tracking
- **[Tracking Registry System Operations Manual](./tracking_registry_operations_manual.md)**
- **[Tracking Control System Operations Manual](./tracking_operations_manual.md)**

### Pad Clearance
- **[Pad Registry System Operations Manual](./pad_registry_operations_manual.md)**
- **[Pad Resolver System Operations Manual](./pad_resolver_operations_manual.md)**

### Opportunity Alignment
- **[Manifest Registry System Operations Manual](./manifest_registry_operations_manual.md)**

### Dispatch
- **[Movement Calculator System Operations Manual](./movement_calculator_operations_manual.md)**
- **[Power Calculator System Operations Manual](./power_calculator_operations_manual.md)**
- **[Dispatch Control System Operations Manual](./dispatch_control_operations_manual.md)**

### Probes
- **[(2) Trade Probe Operations Manual](../../alert/docs/trade_probe_operations_manual.md)**

## Readiness Checklist

This checklist must be completed before full system integration.  It ensures that all power systems are flashed, wired, labeled, and verified.

---

### Tracking Control

1. Power on controller
   - Verify the assigned dish turns on
   - Verify the dish moves to the starting position, if not already aligned.
   - Verify the dish's power level is set based on the scan detection threshold
2. Contact Acquisition
   - Verify the dish's power setting is set to max
   - Verify the locked signal strength is less than 2

### Movement calculator

1. Turn on movement calculator
2. Modify the controller to write the computed result to `Setting`
   - Verify that the sign matches the direction of the shortest horizontal distance between the two dishes for a slot request
3. Restore the original programming
   - Verify that the `Setting` displays the index of the requested slot

### Power Calculator

1. Turn on power calculator
2. Cycle through each slot index
   - Verify that unresolved signals return -1
   - Verify that resolved signals return the index of the requested slot 
3. Modify the controller to write the computed result to `Setting`
   - Verify that resolved signals display a value >= 0
   - Verify that infeasible signals display infinity
   - Verify that all other signals display a numerical result
4. Restore the original programming
   - Verify the output displays between -1 to 4

### Dispatch Control

1. Turn on dispatch calculator
2. Verify that a contact is selected
3. Verify the call dish and correct landing dish moves into the target position
4. Verify that the contact lands