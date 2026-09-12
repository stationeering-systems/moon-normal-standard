# FUEL PAD PUMP - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Regulates the flow of gas into and out of the landing pad.

## FUNCTIONAL OVERVIEW
* Monitors the occupancy of the pad and writes 0=vacant, 1=occupied into its `Setting` register
* Checks the pipe direction switch:
  * 0 - Outward: gas detected in the pad will be routed to the appropriate gas line
  * 1 - Inward: Reads the Demand device input (x 100 mols) and pressurizes the pad with the specified amount of fuel.

## HARDWARE INTERFACE
* **d0:** Demand (any device with `Setting`)
* **d1:** Landing Pad
* **d2:** Fuel Pipe (pipe analyzer)
* **d3:** Pump Direction (logic switch)

## CONFIGURATION PARAMETERS
| Variable             | Description | Setting                |
|----------------------|-------------|------------------------|
| `FuelConnector`      | (label)     | `"FuelConnector"`      |
| `VolatilesConnector` | (label)     | `"VolatilesConnector"` |
| `OxygenConnector`    | (label)     | `"OxygenConnector"`    |

## SUPPORTED GAS TYPES
| Pump      | Mixture (@ 100%)                           |
|-----------|--------------------------------------------|
| Fuel      | Methane, Oxygen, Pollutant                 |
| Volatiles | Methane, Carbon Dioxide, Hydrochloric Acid |
| Volatiles | Pollutant                                  |
| Oxygen    | Oxygen                                     |

Note: Pad must be empty before loading additional gas types

## KNOWN ISSUES
* **Operators using dish stack for demand retrieval: demand signal may not always reflect trader intent after order fulfillment.** The dish stack value read at the pad may retain the pre-fulfillment demand quantity after a trade completes, causing the pad controller to pressurize for a quantity the trader no longer requires.  In that case, the flow direction switch can be toggled manually to depressurize.

## MAINTENANCE AND TROUBLESHOOTING

### Trader won't buy fuel

**STEP 1: Check pad**

1.1 Is there at least 100 moles of gas in the pad?  
* IF NO  - Traders only buy gas in 100 mol increments.  Refer to [Insufficient fuel pumped into pad](#insufficient-fuel-pumped-into-the-pad).
* IF YES - Ensure the mixture is at least 65% methane and 32% oxygen

### Insufficient fuel pumped into the pad

**STEP 1: Check power**

1.1 Is the `TERMINAL` powered?  
* IF NO  - Check system power
* IF YES - Continue to Step 2 

**STEP 2: Check pad**

2.1 Is the Demand Setting greater than 0?  
* IF NO  - System Normal
* IF YES - Continue to Step 2.2

2.2 Is the Pump direction set to 1 (inward)?  
* IF NO  - Change pump direction
* IF YES - Continue to Step 3

**STEP 3: Check fuel pipe**  

3.1 Is there fuel in the pipe?  
* IF NO  - Continue to Step 3.2
* IF YES - Further investigation is required

3.2 Is there fuel in other pads?  
* IF NO  - Refer to fuel production system guides for further troubleshooting
* IF YES - Change pump direction on other pads to redirect inventory

### Gas is not pumped out of the pad

**STEP 1: Check Power**

1.1 Is the `TERMINAL` powered?  
* IF NO  - Check system power
* IF YES - Continue to Step 2 

**STEP 2: Check pad**

2.1 Does the composition match one of the [Supported Gas Types](#supported-gas-types)?  
* IF NO  - Further investigation is required
* IF YES - Ensure that pump direction is set to 0 (outward)