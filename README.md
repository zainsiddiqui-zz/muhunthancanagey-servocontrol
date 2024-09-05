# PCB Design for Servo Motor Control Board
#### Client Name: Muhunthan Canagey

## Project Requirements
### Project Summary: 6-Axis Cartesian Robot Control PCB Design
### Project Description:
Create a printed circuit board (PCB) to control a 6-axis Cartesian robot using six servo motors. The PCB will be powered by a 220V AC input and will provide 24V DC to the servo motors (ranging from 150w to 1.5kw), as well as 5V and 3.3V DC for other electronic components. The ESP32 microcontroller (suitable Module) will be used to control the servo motors via PWM signals.

### General Description
The PCB design will require an ESP32 board to be fitted for the purpose of controlling the functionality of the Cartesian Robot, as when coordinates are passed from external software, the cartesian functionality must be performed, such as the servo motor being activated for movement to those specific coordinates. You will also be required to ensure safety control mechanisms are in place using sensor data from Reed Switches distance sensors and anti-coalition sensors.

The 6th axis will also have a gripper, which will work with pneumatic solenoid valves controlled electronically.

For the functions listed below, need to write the software logic/control as code to be executed on the ESP32 board.

Software will send instructions (through USB), such as
1. move to coordinates, (X,Y, Z axis)
2. move to coordinates (4th axis, 5th axis, 6th axis)
3. gripper lock/release
4. rotate gripper (6th axis)

The board will be divided into 3 PCBs each having appropriate and properly rated interconnects to facilitate connections:
#### Power PCB
This PCB should only contain the power circuit

#### Logic PCB
This PCB should only contain ESP32 and all logical circuitry (motor drivers etc)

#### Control PCB
This PCB should only contain control components (relays high power FETs etc)

###### Note: Logic and Control PCB can be same if not feasible to separate them. Discussion needed first!

### Key Requirements:
#### Power Supply:
- Input: 220V AC
- Output: 24V DC (high current) for servo motors
- 5V DC for ESP32 and other logic circuits
- 3.3V DC (optional) for specific components

##### Motor Drivers:
- High-power H-bridge or specialized servo motor drivers
- Current rating to handle peak motor currents
- Overcurrent and overtemperature protection
- PWM control compatibility with ESP32

##### ESP32 Interface:
- GPIO pins for PWM control signals
- Serial communication (UART or SPI) for external interfaces
- Stable 5V / 3V3 power supply

##### PCB Layout:
- Separate power planes for high and low currents
- Short PWM signal traces
- Solid ground plane and proper grounding techniques
- Heat sinking for voltage regulators and motor drivers

##### Connectors:
- 220V AC input with strain relief
- Servo motor connectors (e.g., screw terminals)
- Headers for ESP32 programming and debugging
- Optional connectors for external sensors, buttons, etc.

##### Additional Considerations:
- Safety: Implement emergency stop and other safety features
- Testing: Thoroughly test the PCB before high-power motor connection
- Software: (Optional) Firmware for ESP32 servo control


### Schematic Design (Key Components)
#### Power Supply:
- Transformer: 220V AC to 24V AC step-down (e.g., Toroidal transformer)
- Rectifier: Bridge rectifier (e.g., GBPC3510)
- Filtering Capacitors: Bulk capacitor (e.g., 4700uF, 50V electrolytic)
- Decoupling capacitors (e.g., 0.1uF ceramic) across ICs
##### Voltage Regulators:
- Switching regulator for 24V (e.g., LM2596-ADJ)
- Linear regulator for 5V (e.g., LM7805)
- Linear regulator for 3.3V (e.g., LD1117V33)

#### Motor Drivers:
##### Consider (Suggestion):
1. Integrated H-Bridges: (e.g., L298N, BTS7960) - easier to use, but may have lower current capacity
2. Discrete MOSFET H-Bridges: (e.g., IRF540N, IRF9540N) - higher current capacity, but require more external components
- Current Rating: Ensure drivers can handle peak motor currents
##### Protection:
- Overcurrent protection (fuses or PTCs)
- Overtemperature protection (thermal shutdown)
- Flyback diodes across motor terminals
###### Servo Details
- Servo Motor for axis 1 is 1kW
- Servo Motor for axis 2 is 1kW
- Servo Motor for axis 3 is 1kwW
- Servo Motor for axis 4 is 750W
- Servo Motor for axis 5 is 750W
- Servo Motor for axis 6 is 750W

#### ESP32:
- Decoupling Capacitors: 0.1uF ceramic across power pins
- Headers: For programming and communication

#### Additional Components:
- Status LEDs: For power, motor activity, etc.

#### Connectors:
- 220V AC input (with strain relief)
- Servo motor connectors (e.g., screw terminals)
- Optional: external communication, sensors, etc.

### PCB Layout (Key Considerations)
- Power Planes: Separate for 24V, 5V, and 3.3V (if used)
- Signal Routing: Short, direct PWM traces away from power
- Ground Plane: Solid ground plane under the whole board
#### Heat Dissipation:
- Thermal vias under power components
- Adequate spacing for airflow
#### Component Placement:
- Group related components together
- Place high-power components near board edges for easier heat-sinking

### Important Notes:
- Power Requirements: Verify that the transformer, rectifier, and voltage regulators are rated for the appropriate power levels to handle all six servo motors simultaneously.
- Safety: Implement appropriate safety measures, such as emergency stop circuits, fuse protection, and proper grounding.
- Testing: Thoroughly test the PCB before connecting the high-power motors to ensure the functionality and safety of the design.




### Deliverables:
- Detailed schematic diagram
- Complete PCB layout
- Gerber files (RS-274X format) for manufacturing
- Bill of materials (BOM)
- Software for control logic on ESP32 board.
