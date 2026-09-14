# System Documentation

This directory contains operational documentation for key infrastructure used in Fuel Systems.

## Available Manuals
- **[Fuel Production Systems Readiness Checklist](#readiness-checklist)**
- **[Fuel Manifest Resolver Operations Manual](./fuel_resolver_operations_manual.md)**
- **[Fuel Demand Tracker Operations Manual](./fuel_demand_tracker_operations_manual.md)**
- **[Fuel Order Operations Manual](./fuel_order_operations_manual.md)**
- **[Trade Demand EMA Operations Manual](../../trade/docs/trade_demand_ema_operations_manual.md)**
- **[Fuel Pad Pump Operations Manual](./fuel_pad_pump_operations_manual.md)**
- **[Fuel Mixer Operations Manual](./fuel_mixer_operations_manual.md)**
- **[Fuel Filtration Operations Manual](./fuel_filtration_operations_manual.md)**
- **[Fuel Distill Operations Manual](./fuel_distill_operations_manual.md)**
- **[Fuel Quench Operations Manual](./fuel_quench_operations_manual.md)**

### Probes
- **[(5) VCU Probe Operations Manual](../../alert/docs/vcu_probe_operations_manual.md)**

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

### Fuel Production (VCU)
*Requires a [Gas Trader] and a [Fuel Buyer]*

1. Turn on the Fuel Pad Controller
2. [Gas Trader] Ensure that the pump direction is set to outward (0)
3. [Gas Trader] Purchase oxygen, ensure gas is routed to the correct pipe
4. [Gas Trader] Purchase dirty volatiles, ensure gas is routed to the correct pipe
5. [Gas Trader] Purchase pollutant, ensure gas is routed to the correct pipe
6. Turn on the Filtration
   1. Ensure the quench pump turns on
   2. Remove both filters
   3. Ensure the quench pump turns off
   4. Replace filters
7. Turn on the Quench and Distill Controllers, ensure pipe analyzers are on and locked
8. Turn on volatiles pipe analyzer, ensure that the pressure regulator turns on
9. The quench might stall as the system starts up.  Refer to [system recovery steps](./fuel_quench_operations_manual.md#known-issues).
10. Monitor throughput, ensure:
    1. No pollutant condensation in the dew pipe (hcl condensation ok)
    2. The bubble pipe processes gas faster than the dew pipe pressurizes
    3. The blend cooling pipe processes gas faster than the bubble pipe processes
11. Turn on the gas mixer, ensure fuel pipe (and/or terminal contains): Minimum 65% methane, 32% oxygen, 0% liquid, 20-30 C
12. [Fuel Buyer] Ensure the fuel pump direction is inward (1) when demand is greater than 0
13. [Fuel Buyer] Change the fuel pump direction to outward (0)
    1. Ensure gas is routed to the fuel pipe
    2. Ensure the landing pad is empty
    3. Change the fuel pump direction to inward (1)
14. [Fuel Buyer] Ensure that no more gas is added once the requested amount is available
15. [Fuel Buyer] Sell fuel
16. Ensure that mixing is inactive when,
    1. Either input pipe is empty
    2. The filtration mode is active
    3. Any of the oxygen connectors are on