# System Documentation

This directory contains operational documentation for key infrastructure used in the ARU.

## Available Manuals

- **[ARU Readiness Checklist](#readiness-checklist)**
- **[ECL System Operations Manual](ecl_system_operations_manual.md)**
- **[TEC System Operations Manual](tec_system_operations_manual.md)**
- **[TEC Cooler Operations Manual](tec_cooler_operations_manual.md)**
- **[PGL System Operations Manual](pgl_system_operations_manual.md)**

### Probes

- **[(5) ARU Probe Operations Manual](../../alert/docs/aru_probe_operations_manual.md)**

## Readiness Checklist

This checklist must be completed before full system integration.  It ensures all atmospheric control systems are flashed, wired, labeled, and verified.

---

### Failsafe Control

1. Verify that there is no pressure on the TEC line
2. Power **on** `TEC-FS`
3. Power **on** `Failsafe Control`
4. Assert `TEC-FS` shuts off
5. Power **off** `Failsafe Control`
6. Power **on** `TEC-FS`

7. Confirm **Volatiles filters** are installed on `TEC-V`
8. Power **on** `TEC-V` (unflashed)
9. Load gas (> 6.3 kPa) from the ECL
10. Power **on** `Failsafe Control`
11. Assert `TEC-FS` remains **on**.
12. Power **off** `Failsafe Control`
13. Power **off** `TEC-V`

### TEC-C Cooling Loop

1. Flash the `TEC-C` controller
2. Power on `TEC-C`
3. Assert `TEC-C` is **IDLE**

4. Power on the **Thermal Regulator** valve
5. Verify gas is present in the cooling pipe and `TEC-C` remains **IDLE**
6. Power off the **Thermal Regulator** valve
7. Assert:
   - `TEC-C` is **ACTIVE** while gas is flushed
   - Cooling pipe is empty at completion

---

### TEC-V Filtration Controller

1. Flash the `TEC-V` controller
2. Power **on** `TEC-V`
3. Remove filters
4. Assert `TEC-V` is **IDLE**

6. In case of volatiles contamination:
   - Open **manual release valve**
   - Confirm pipe is cleared

7. Restore filters
8. Assert:
   - `TEC-V` activates and begins pressurizing **if**:
   - Intake pressure ≥ 6.3 kPa
   - TEC pipe pressure < Max threshold (48,636 kPa)

9. If pipe pressurization exceeds 85% (51,675 kPa):
   - Immediately shut down
   - Investigate controller logic
  
> Note: Full validation may take several minutes due to intake limitations.

---

### Thermal Activation Check

1. Set TEC pipe temperature:
   - Below minimum (293.15 K) → Assert **heating is active**
   - Above maximum (298.15 K) → Assert **cooling is active**
   - Within target range → Assert **no active heating/cooling**

---

### PGL Filtration Control

1. Flash PGL logic controller
2. Confirm **activation** triggers when:
   - Temperature is within target range
   - Input Pressure × Volume meets threshold (10,000 kPa*L)
   - Gas type ratio ≥ minimum ratio
3. Remove filter during **activation**
4. Assert PGL unit is **IDLE**
5. Restore filter

> Note: Full validation may require extended runtime or favorable gas mix.