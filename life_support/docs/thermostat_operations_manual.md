# THERMOSTAT CONTROLLER - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
The thermostat controller manages cooling capacity through two distinct operating modes selectable via manual logic switch.  The controller monitors local temperatures and modulates the cooling system's response based on the active mode selected.

## FUNCTIONAL OVERVIEW
* Monitors PID Controller output to determine required cooling capacity
* Manages the circulation of gas into and out of the radiation pipe segment

**Mode 0 - Thermal tracking mode**
* Maintains precise temperature control around a setpoint.
* Modulates pump speed with respect to required cooling capacity

**Mode 1 - Thermal pulse mode**
* Operates as a bang-bang controller with upper and lower temperature thresholds
* Opens valve when temperature exceeds upper threshold
* Closes valve and evacuates radiation pipe when the temperature drops below the lower threshold

## HARDWARE INTERFACE
* **d0:** PID Controller
* **d1:** Temperature Setting K
* **d2:** Operating Mode (0/1)

## CONFIGURATION PARAMETERS
| Variable   | Description                               | Setting    |
|------------|-------------------------------------------|------------|
| `PGainTTM` | Thermal Tracking Mode - Proportional Gain | `-0.0106`  |
| `IGainTTM` | Thermal Tracking Mode - Integral Gain     | `-0.00003` |
| `DGainTTM` | Thermal Tracking Mode - Derivative Gain   | `0.05`     |
| `MinTTM`   | Thermal Tracking Mode - Minimum           | `-1`       |
| `MaxTTM`   | Thermal Tracking Mode - Maximum           | `1`        |
| `PGainTPM` | Thermal Pulse Mode - Proportional Gain    | `0.2`      |
| `IGainTPM` | Thermal Pulse Mode - Integral Gain        | `0`        |
| `DGainTPM` | Thermal Pulse Mode - Derivative Gain      | `0`        |
| `MinTPM`   | Thermal Pulse Mode - Minimum              | `0`        |
| `MaxTPM`   | Thermal Pulse Mode - Maximum              | `1`        |

## MAINTENANCE AND TROUBLESHOOTING

### Temperature is high

**STEP 1: Check power**

1.1 Is the PID powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 1.2

1.2 Is the controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 2

**STEP 2: Check circulation**

2.1 Is there gas in the radiation/convection segments?
* IF NO - Check for gas leaks
* IF YES - Continue to STEP 2.2

2.2 Is the valve on/opened?
* IF NO - Continue to STEP 2.3
* IF YES - Continue to STEP 2.4

2.3 Is the valve powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 3

**STEP 3: Check controller output**

3.1 Is the local sensor temperature high?
* IF NO - More capacity needed
* IF YES - System recalibration needed

### Temperature is low

**STEP 1: Check power**

1.1 Is the `THERM-LL` network powered?
* IF NO - Further investigation required
* IF YES - Continue to STEP 1.2

1.2 Is the controller powered?
* IF NO - Verify system settings and connections
* IF YES - Continue to STEP 2

**STEP 2: Check circulation**

2.1 Is the valve on/opened?
* IF NO - Further investigation required
* IF YES - System recalibration needed