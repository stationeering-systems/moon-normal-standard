# TRADE DEMAND EMA - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Accumulates demand of a tradeable item and calculates the average opportunity rate.

## FUNCTIONAL OVERVIEW
* Iterates over multiple demand readers and accumulates demand over the time window.
* Only accumulates value when demand reader is powered
* When the window elapses it
  * Resets the stopwatch
  * Incorporates the current accumulation into the EMA value
  * Sets the accumulation to zero
* Tracks the exponential moving average of incoming demand over a designated time window.

## HARDWARE INTERFACE
* **d0:** Stopwatch
* **d1..d5:** Demand Readers

## CONFIGURATION PARAMETERS
| Variable         | Description                               | Setting |
|------------------|-------------------------------------------|---------|
| `WindowDuration` | Time period which demand is evaluated (s) | `1200`  |
| `WindowAlpha`    | Demand decay rate                         | `0.125` |