# EXCHANGE CAPTURE LINE - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Captures waste gases from base subsystems and delivers them to the Thermal Exchange Core (TEC) for purification and processing.

## FUNCTIONAL OVERVIEW
* Aggregates mixed exhaust gases from various discharge sources.
* Buffers incoming gases for downstream intake by the TEC-V filtration system.
* Controls pressure buildup via a back-pressure regulator (set to 80% pipe capacity), to regulate pressure buildup.
* Protects the pipe network from condensation damage using passive drains.

## PIPE CONNECTIONS
* **Input:** Active vents, exhaust lines, or manual discharge ports.
* **Output:** TEC-V Input
* **Auxiliary:** Passive drain segment connected to a back-pressure regulator and optional meter.

## POWER DOMAIN
* The back-pressure regulator is connected to the ARU-CRT line (Red), allowing pressure venting to continue even during power outages.

## NOTES
* The ECL is **logic-agnostic**: it contains not logical or programmable components.
* All regulation and operational state transitions are handled downstream by the TEC-V controller.
* Pressure in the ECL may spike briefly if the TEC is actively conditioning gases--this is expected behavior.
  
---

> For gas conditioning and active filtration behavior, see the [TEC System Operations Manual](tec_system_operations_manual.md).