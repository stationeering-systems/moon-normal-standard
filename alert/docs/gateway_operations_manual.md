# GATEWAY CONTROL - SYSTEM OPERATIONS MANUAL

## SYSTEM PURPOSE
Message bus that communicates local max and sector max between locations

## FUNCTIONAL OVERVIEW
* Monitors probe states through cable channels (1..7)
* Relays sector state back through cable channel 0

## HARDWARE INTERFACE
* **d0:** LocationID SSRR

## NOTES
* Gateway status is persisted even when the gateway is offline