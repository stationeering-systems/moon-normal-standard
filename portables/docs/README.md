# System Documentation

This directory contains operational documentation for key infrastructure used in Portable Systems.

## Available Manuals

- **[Portables Readiness Checklist](#readiness-checklist)**
- **[Port-Suit System Operations Manual](portsuit_operations_manual.md)**
- **[Port-Can System Operations Manual](portcan_operations_manual.md)**

## Readiness Checklist

This checklist must be completed before full system integration.  It ensures all portable systems are flashed, wired, labeled, and verified.

---

### Port-Suit Control

1. Power on controller
2. Attach partially empty suit:
   - Verify suit storage turns on
   - Verify that battery charges to 100%
   - Verify that waste tank is emptied
   - Verify that breathing and propellant tanks are topped off to pressure regulator setting
   - Verify that suit storage and pressure regulators turn off when operations are complete
3. Attach multiple partially empty suits and verify that only one suit is charged at a time.

### Waste Management Validation

1. Monitor exhaust pressure levels
2. Assert pumps inactive during normal operation
3. If exhaust pressure > safety threshold:
    - Verify pump activation
    - Check throughput rates

### Port-Can Control

1. Power on controller
2. Attach smart canister to outward feed:
   - Verify that canister is pressurized to smart fill max
   - Remove canister from feed
   - Verify that pressure regulator is active only when canister is not full
3. Attach regular canister to the same feed:
   - Verify that canister is pressurized to standard fill max
   - Remove canister from feed
4. Attach pressurized canister to exhaust feed: 
   - Verify that canister is emptied
   - Verify that volume pump is active only when canister is not empty