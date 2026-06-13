# System Documentation

This directory contains operational documentation for key infrastructure used in Fuel Systems.

## Available Manuals
- **[Fuel Production Systems Readiness Checklist](#readiness-checklist)**
- **[Fuel Manifest Resolver Operations Manual](./fuel_resolver_operations_manual.md)**
- **[Fuel Demand Tracker Operations Manual](./fuel_demand_tracker_operations_manual.md)**
- **[Fuel Order Operations Manual](./fuel_order_operations_manual.md)**
- **[Trade Demand EMA Operations Manual](../../trade/docs/trade_demand_ema_operations_manual.md)**

## Readiness Checklist

This checklist must be completed before full system integration.  It ensures that all power systems are flashed, wired, labeled, and verified.

---

### Fuel Manifest Resolver

1. Turn off the dispatch
2. Flash the manifest resolver to all manifest resolver ICs
3. Adjust the slot index dial to verify expected inputs and outputs:
    - Contact Slot Index matches the contact slot index on the dish
    - The maximum result reflects the opportunity availability and the matching slot state
4. Reset the dispatch (remove and re-insert the IC)
5. Turn the dispatch back on

### Fuel Demand Tracker

1. Turn on the IC
2. Ensure that the Setting value matches the fuel demand quantity
3. Ensure that the Demand Reader only turns on when the Dish's Activation signal is set to 1.

### Trade Demand EMA

1. Turn on the IC
2. Verify that the stop watch is on and active
3. Wait for incoming trades
4. Verify that the EMA value updates at the end of the window

### Fuel Order Monitor

1. Turn on the IC
2. Ensure that EMA=0 returns zero for Volatiles, Oxygen, and Pollutant order registers
3. Ensure that EMA > 0 returns the integer unit purchase amount of each commodity