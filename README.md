# Simple_Elevator

This repository contains a **simple elevator control project** developed in **CODESYS**.  
The system controls **one elevator serving four floors (L0–L3)** and demonstrates basic PLC control logic using **Ladder Diagram (LD)** and **Structured Text (ST)**.

---
## System Description
- **L0 – L3**  
  Floor request buttons, either pressed **inside the cabin** or **from each floor**.
- **at_L[ ]**  
  Boolean array indicating the **current floor position** of the elevator.
- **go_L[ ]**  
  Boolean array storing the **target floor requests**.
- A `go_L` coil is activated only when:
  - the corresponding floor button is pressed
  - the elevator is not moving
- Floor requests remain active until:
  - the elevator reaches the selected target floor
---
## Control Logic

- At the beginning of each PLC cycle: all movement commands are reset
- The controller:
  - detects the **current floor** using the `at_L[ ]` array
  - determines the **target floor** from the active `go_L[ ]` request
- Elevator movement is decided inside a **POU action block**:
  - **Current floor < Target floor** → elevator moves **up**
  - **Current floor > Target floor** → elevator moves **down**
  - **Current floor = Target floor** → elevator **stops**
- If no valid floor position is detected:
  - the elevator enters a **safe stop state**
---
## Implementation
- **Ladder Diagram (LD)** : Handles floor request detection and latching

- **Structured Text (ST)** : Implements the decision logic for:
    - current floor
    - target floor
    - movement direction (up / down / stop)
---
- Programming languages:
  - Ladder Diagram (LD)
  - Structured Text (ST)
