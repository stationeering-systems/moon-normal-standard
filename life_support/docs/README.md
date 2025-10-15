# System Documentation

This directory contains operational documentation for key infrastructure used in Life Support Systems.

## Available Manuals

- **[Life Support Readiness Checklist](#readiness-checklist)**
- **[Mix-Press System Operations Manual](mixpress_operations_manual.md)**
- **[Interconnect System Operations Manual](interconnect_operations_manual.md)

## Readiness Checklist

This checklist must be completed before full system integration.  It ensures all life support control systems are flashed, wired, labeled, and verified.

---

### Mixture-Pressure Control

1. Power on controller
2. Monitor pressure on `Pressure Display` console
3. Verify pressure within target thresholds

4. Switch gas ratios on `Gas Ratio Display` console
5. Compare against baseline measurements
6. Observe gas selection behavior:
   - Pressure: First available activates
   - Composition: Deficient gas priority

### Waste Management Validation

1. Monitor exhaust pressure levels
2. Assert pumps inactive during normal operation
3. If exhaust pressure > safety threshold:
   - Verify pump activation
   - Check throughput rates

### Ventilation System Test

1. Inward vents powered/pulsing (1-sec)?
2. Outward vents powered/pulsing (1-sec)?
3. Target vents pulsing (max 2-sec)?
4. Verify inward precedence over outward

### Operational Validation

Monitor first few atmospheric cycles:
1. Pressure regulation stable
2. Gas ratios trending/maintaining targets
3. Pumps inactive (normal operation)
4. Energy utilization within load leveling limits

### System Integration Check

1. Main/local gas/ line pressure >= 144 kPa?
2. No pipe ruptures detected?
3. Valve positions correct?

### Interconnect Control

1. Power on controller
2. Verify the interconnect valve is open
3. Wait for the valve to close
   - Verify full pressurization
4. Open the boundary wall between compartments
5. Integrate sensor and ventilation equipment into the data network
   - Gas Sensor: `"Sector"`
   - Active Vents: `"SectorExhaust"`, `"SectorCarbonDioxide"`, `"SectorNitrogen"`, `"SectorOxygen"`
6. Remove interconnect plumbing
7. Update the Size Setting dial to include the added compartment volume

> Note: Full verification may take up to 15 minutes to confirm target stabilization.