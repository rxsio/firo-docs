**1. Main Assembly**  
`00-name` - Where name is the name of the project. Write in lowercase only. Use `_` instead of space  

**Example:**  
```yaml
project: # Top folder of the project
	- 00-project # Main Assembly
```

**2. Subassembly**  
`AA_..._XX_YY_00-name` - Where:  
- `AA`, ..., `XX` are numbers of the parent subassemblies  
- `YY` is the number of the current subassembly  
- `name` is a descriptive name of the subassembly. Write in lowercase only. Use `_` instead of space  

Each subassembly is placed in its own dedicated folder  

**3. Subassembly folder**  
`AA_..._XX_YY-name` - Where:  
- `AA`, ..., `XX` are numbers of the parent subassemblies  
- `YY` is the number of the current subassembly  
- `name` is a descriptive name of the subassembly. Write in lowercase only. Use `_` instead of space  

**Example:**  
```yaml
project: # Top folder of the project
	- 00-project # Main Assembly
    - 01-subassembly1: # Folder for subassembly
	    - 01_00-subassembly1 # Subassembly file
	    - 01_01-sub_subassembly: # Folder for subassembly in a subbassembly
		    - 01_01_00-sub_subassembly # Subassembly file
    - 02-subassembly2: # Folder for another subassembly
	    - 02_00-subassembly2 # Subassembly file
```

**4. Part**  
`AA_..._XX_YY_ZZ-name` - Where:  
- `AA`, ..., `XX` are numbers of the parent subassemblies  
- `YY` is the number of the current subassembly  
- `ZZ` is the number of the part  
- `name` is a descriptive name of the part. Write in lowercase only. Use `_` instead of space  

Each part is placed in its (sub)assembly folder  

**Example:**
```yaml
project: # Top folder of the project
	- 00-project # Main Assembly
    - 01-subassembly1: # Folder for subassembly
	    - 01_00-subassembly1 # Subassembly file
	    - 01_01-sub_subassembly: # Folder for subassembly in a subbassembly
		    - 01_01_00-sub_subassembly # Subassembly file
		    - 01_01_01-part1 # Part (file) of the (sub)subassembly
	    - 01_02-part1 # Part (file) of the subassembly
	    - 01_03-part2 # Another part (file) of the subassembly
    - 02-subassembly2: # Folder for another subassembly
	    - 02_00-subassembly1 # Subassembly file
	    - 02_01-part1 # Part (file) of the subassembly
	    - 02_02-part2 # Another part (file) of the subassembly
```

**5. Commercial and Standardized Elements:**  
`[Standard|Manufacturer]-name` - Where:  
- `[Standard|Manufacturer]` is the standard of a standardized part or name of the  manufacturer of the not standardized part. Write in lowercase only. Use `_` instead of space.  
- `name` is a descriptive name of the part. It may but doesn't have to be name used by the manufacturer. Write in lowercase only. Use `_` instead of space.  

All external parts such as commercial parts from manufacturers and standardized elements (e.g., fasteners) should be stored only in the  folder "external" which is in the top folder of the project.  

**Example:**  
```yaml
project: # Top folder of the project
	- 00-project # Main Assembly
    - 01-subassembly1: # Folder for subassembly
	    - 01_00-subassembly1 # Subassembly file
	    - 01_01-sub_subassembly: # Folder for subassembly in a subbassembly
		    - 01_01_00-sub_subassembly # Subassembly file
		    - 01_01_01-part1 # Part (file) of the (sub)subassembly
	    - 01_02-part1 # Part (file) of the subassembly
	    - 01_03-part2 # Another part (file) of the subassembly
    - 02-subassembly2: # Folder for another subassembly
	    - 02_00-subassembly1 # Subassembly file
	    - 02_01-part1 # Part (file) of the subassembly
	    - 02_02-part2 # Another part (file) of the subassembly
	- external:
		- standard-standarized_part # Standarized part
		- standard2-another_part # Another standarized part
		- manufacturer-commercial_part # Catalog part from manufacturer
```

**6. Exported files:**  
- Exported from (sub)assembly:  
	`AA_..._XX_YY_00-name`	- Where `AA_..._XX_YY_00-name` is the name of the (sub)assembly  
- Exported from part:  
	`AA_..._XX_YY_ZZ-name` - Where `AA_..._XX_YY_ZZ-name` is the name of the part  

All exported files should have their dedicated folders within each subassembly folder. The name of the folder should match the exported file extension (e.g., "pdf" for pdf files).  

**Example:**  
```yaml
project: # Top folder of the project
	- 00-project # Main Assembly
    - 01-subassembly1: # Folder for subassembly
	    - 01_00-subassembly1 # Subassembly file
	    - 01_01-sub_subassembly: # Folder for subassembly in a subbassembly
		    - 01_01_00-sub_subassembly # Subassembly file
		    - 01_01_01-part1 # Part (file) of the (sub)subassembly
	    - 01_02-part1 # Part (file) of the subassembly
	    - 01_03-part2 # Another part (file) of the subassembly
	    - dwg:
			- 01_00-subassembly1.dwg
		    - 01_03-part2.dwg
		- pdf:
			- 01_00-subassembly1.pdf
		    - 01_03-part2.pdf
    - 02-subassembly2: # Folder for another subassembly
	    - 02_00-subassembly1 # Subassembly file
	    - 02_01-part1 # Part (file) of the subassembly
	    - 02_02-part2 # Another part (file) of the subassembly
	    - stl:
		    - 02_01-part1.stl
		    - 02_02-part2.stl
	- external:
		- standard-standarized_part # Standarized part
		- standard2-another_part # Another standarized part
		- manufacturer-commercial_part # Catalog part from manufacturer
		- stp:
			- manufacturer-commercial_part.stp
	- stp:
		- 00-project.stp
```
