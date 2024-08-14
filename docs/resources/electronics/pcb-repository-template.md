---
title: PCB Repository Tempalte
---

## Repository Description

In `README.md`, give a short summary of the project and guide users to the full documentation at [https://rxsio.github.io/firo-docs/](https://rxsio.github.io/firo-docs/) for details. 

## Repository Structure

```yaml
- Project Name:
	- Gerber:
		- Gerber.gbr
	- Layout:
		- layout.pdf
		- layout.pcb
	- Reference Documentation:
		- Datasheet1.pdf
		- Datasheet2.pdf
		- ApplicationNote.pdf
	- Schematic:
		- schematic.pdf
		- schematic.sch
    - BOM:
        - bom.csv
    - Firmware:
	    - apps:
		    - main.c
        - include:
            - module1.h
            - module2.h
        - src:
            - module1.c
            - module2.c
		- extern:
			- library1
    - Project:
	    - project.pro
    - README.md
```