
Rover wiring is shown below on two separate schematics:

Power management lines:
![[power_wiring_schematic.png.png]]
Data management lines:
![[data_wiring_schematic.png.png]]

Data and power cables use different connectors to prevent short-circuits and assembly mistakes. The scheme follows general rule that all sources of voltage have female connectors. Does not matter if they are on board or on a wire. This setup minimalizes risk of short-circuit caused by loose metal objects dropped inside connectors. Idea is shown on the picture below.

Please note that male connector is one that has **metal** pin that goes inside **metal** shield of female connector. Non conductive parts of a connectors **do not matter**. In case of any doubt, reference the connector tables below.

![[Connectors_idea.drawio.png]]

Connectors are signed as follows:   

- Phoenix – battery voltage,  

|       | Male (reciver)         | Female (source)       |
|-------|------------------------|-----------------------|
| Wire  | ![[phoenix_wire_male_connection.png]]  [IC 2,5/ 2-ST-5,08](https://www.phoenixcontact.com/en-us/products/pcb-plug-ic-25-2-st-508-1786174)    | ![[phoenix_wire_female_connection.png]]  [MSTB 2,5/ 2-ST-5,08](https://www.phoenixcontact.com/en-us/products/pcb-plug-mstb-25-2-st-508-1757019) |
| Board | ![[phoenix_pcb_male_connection.png]]  [MSTBVA 2,5/ 2-G-5,08](https://www.phoenixcontact.com/en-us/products/pcb-header-mstbva-25-2-g-508-1755736) | ![[phoenix_pcb_male_connection.png]]  [ICV 2,5/ 2-G-5,08](https://www.phoenixcontact.com/en-us/products/pcb-header-icv-25-2-g-508-1785942)   |

All stranded (multiple thin wires inside one coating) wires cooperating with Phoenix connectors should end with end sleeves. This prevents wires from falling of the connectors and making short-circuits on circuits boards. It also boosts durability of the wire. When applying new end sleeves pay attention not to bend or twist wires. They would not fit correctly. Metal part of sleeve should not be longer than wires inside. It is also a good idea to check after assembly if wires stay firm inside connectors.

- USB C – control voltage 5V,  
- micro USB – control voltage 5V,  
- micro-match – CAN, supply side,  
- IDC 4 pin – CAN, reciver side,  

|       | Male (reciver) | Female (source) |
|-------|----------------|-----------------|
| Wire  | [Micro-MaTch](https://www.te.com/usa-en/product-7-215083-4.html)  | [IDC](https://www.amphenol-cs.com/quickie-71600104lf.html)           |
| Board | [IDC](https://www.amphenol-cs.com/quickie-75869330lf.html)          | [Micro-MaTch](https://www.te.com/usa-en/product-7-215079-4.html)   |

- USB A – USB, 
- 8P8C (usually called RJ45) – Ethernet.   
