# moon-normal-standard

**Modular engineering systems for Stationeers -- Moon, Normal Difficulty, Standard Kit**

These systems aim to demonstrate sound systems design practices through the lens of *Stationeers*, offering modular and efficient infrastructure for Moon-based progression.  Each module is built to balance clarity, reliability, and scalability--engineered to be both practical in-game and illustrative of broader architectural thinking.

---

## Included Modules

* **[Alerts (ALERT)](./alert)**  
  Monitoring and notification systems for facility management.
* **[Atmospheric Recovery Unit (ARU)](./aru)**  
  An intake and recycling system designed to recover waste atmosphere and restore it to usable internal mix.
* **[Life Support (LS)](./life_support)**  
  Atmospheric control systems for sector regulation.
* **[Portables (PORT)](./portables)**  
  Automated fill, evacuation, and resource management systems for portable storage devices.

## Repository Organization

Each module resides in its own top-level folder and includes:

* `ic10/` - Programmable chip scripts
* `docs/` - Markdown-based deployment and operations guides

Modules without control logic are excluded from this repository but are available on the [Stationeering Systems Substack](https://stationeering.substack.com/s/moon).

## Contributing

This repository serves as a curated, practical reference supporting the [Stationeering Systems Substack](https://stationeering.substack.com).  Contributions are encouraged, but must follow conventions established in the Substack.  Substantial departures in logic, layout, or architecture are out of scope for this repository.
