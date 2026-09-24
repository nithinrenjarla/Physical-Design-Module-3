# Physical-Design-Module-3
## CMOS Inverter Design,Characterization,SKY130A Standard-Cell Layout & 16-Mask CMOS Fabrication

# Overview
This module introduces the complete transition from RTL description to physical chip layout. It explains how a digital circuit described using Verilog is converted into a gate-level representation and subsequently transformed into the physical geometrical layout of the chip.
The module begins with the fundamentals of CMOS inverter design and characterization, which are important for understanding digital standard cells. It then introduces the SKY130A open-source CMOS technology, including standard-cell concepts, layout structures and fabrication layers.
Students will also study the major stages of the RTL-to-GDSII flow, including synthesis, floorplanning, placement, clock tree synthesis, routing and physical verification. Practical exposure to tools such as Yosys and OpenLane helps students understand how an RTL design can be converted into a manufacturable physical layout.
# Objectives
- Understand the overall RTL-to-physical-design flow.

- Explain the operation and characteristics of a CMOS inverter.

- Understand basic CMOS fabrication steps and mask layers.
  
- Describe the structure of standard cells.
 
- Understand the significance of the SKY130A technology.
 
- Generate and examine a synthesized gate-level netlist.
 
- Explain the purpose of floorplanning and power planning.
 
- Understand placement and optimization of standard cells.
 
- Explain the requirement of Clock Tree Synthesis.
 
- Understand routing and interconnection between cells.
 
- Identify the purpose of Design Rule Checking (DRC) and Layout Versus Schematic (LVS).
 
- Understand the generation of the final GDSII layout.
 
- Gain practical familiarity with an open-source RTL-to-GDSII flow.

  # Tools and Technologies Used

| Tool / Technology | Purpose |
|---|---|
| Yosys | RTL synthesis and netlist generation |
| OpenLane | Automated RTL-to-GDSII implementation |
| SKY130A PDK | CMOS technology and standard-cell information |
| OpenROAD | Physical-design implementation |
| OpenSTA | Static timing analysis |
| Magic | Layout viewing and physical verification |
| Netgen | LVS comparison |
| GTKWave | Waveform analysis |
| Verilog HDL | RTL hardware description |
| GDSII | Final physical layout representation |

# Table of Contents
-Introduction to RTL-to-GDSII Flow

-CMOS Technology Fundamentals

-CMOS Inverter Design

-CMOS Inverter Characterization

-Standard-Cell Concept

-SKY130A Technology

-CMOS Fabrication Process

-Standard-Cell Layout

-RTL Design and Verification

-Logic Synthesis

-Gate-Level Netlist

-Floorplanning

-Power Distribution Planning

-Placement

-Placement Optimization

-Clock Tree Synthesis

-Routing

-Static Timing Analysis

-Physical Verification

-Design Rule Checking

-Layout Versus Schematic

-GDSII Generation

-RTL-to-GDSII Flow Using OpenLane

-Practical Implementation

-Summary and Key Takeaways

# 1. CMOS Inverter SPICE Simulation and Characterization

  # 1.1 CMOS Inverter and SPICE Model Setup
The first stage of the module focuses on setting up the CMOS inverter for transistor-level simulation. A CMOS inverter consists of a PMOS transistor connected to the supply voltage and an NMOS transistor connected to ground.

The SPICE model provides the electrical characteristics of the MOS devices and allows the inverter to be analyzed under realistic device parameters. The transistor dimensions, supply voltage and input waveform are selected before performing the simulation.

The simulation setup is important because the accuracy of the output waveform and delay measurements depends on the correct device models and circuit parameters. The NMOS and PMOS dimensions are selected according to the required inverter design.

 # 1.2 Simulation Environment and Device Parameters
The next stage involves configuring the simulation environment and defining the required transistor parameters. The width-to-length ratio of the PMOS and NMOS devices has a direct effect on the switching behavior of the inverter.

The selected dimensions determine the relative drive strengths of the pull-up and pull-down networks. Proper sizing is required to obtain balanced rise and fall characteristics. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/553b06c1-9dcf-4bfa-8bb1-46a96b34f02e" />


 # 1.3 SPICE Simulation Execution
After defining the circuit and device parameters, the SPICE simulation is executed. The simulator solves the electrical behavior of the inverter as the input voltage changes with time.

The input signal is applied to the common gate terminal of the PMOS and NMOS transistors. Depending on the input voltage, one transistor turns ON while the other turns OFF, producing the inverted output. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/11d943f4-a08b-4dbf-9fda-49ee458a7e10" />


Figure 3: Execution of CMOS inverter SPICE simulation

This step verifies that the inverter operates correctly before detailed timing and static characterization are performed.

 # 1.4 Input and Output Waveforms
The transient simulation produces both the input and output waveforms. The output waveform is complementary to the input waveform, demonstrating the fundamental operation of the CMOS inverter.

When the input is LOW, the PMOS transistor conducts and the output is pulled towards the supply voltage. When the input becomes HIGH, the NMOS transistor conducts and the output is pulled towards ground.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/d89150ee-6607-409f-a5da-3b91f4c47fbf" />


Figure 4: CMOS inverter input and output waveforms

The waveform confirms the correct logical inversion operation and also provides the information required for measuring propagation delay and transition times.

 # 1.5 Transient Response Analysis
The transient response is examined to understand how quickly the inverter responds to changes in the input signal.

The transition of the output does not occur instantaneously because the transistor network and load capacitance require a finite amount of time to charge or discharge. This delay is an important performance parameter in digital circuits. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/72fe74b3-6d3b-4226-8f17-be082399ec4d" />


Figure 5: Transient response of the CMOS inverter

The measured waveform is used to determine parameters such as rise time, fall time and propagation delay.

 # 1.6 Detailed Waveform Observation
The simulation waveform is further examined over a selected time interval. This allows the transition points of the input and output signals to be identified accurately.

The time difference between corresponding input and output transitions represents the propagation delay of the inverter. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/2c623326-b80e-4340-b7b1-98f10d0d5354" />


Figure 6: Detailed observation of the transient waveform

Accurate waveform observation is necessary for obtaining reliable timing measurements and comparing different transistor sizing conditions.

 # 1.7 Effect of PMOS/NMOS Sizing
The performance of a CMOS inverter strongly depends on the relative sizing of the PMOS and NMOS transistors. Different width ratios are therefore simulated and compared.

Increasing transistor width increases the available drive current and can reduce the time required to charge or discharge the load. However, excessive sizing also increases capacitance and may affect overall performance. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/99e258a2-4e0f-430c-9013-acc192373eea" />


Figure 7: Effect of transistor sizing on inverter behavior

The comparison helps identify a suitable PMOS-to-NMOS sizing ratio for achieving balanced inverter operation.

 # 1.8 Static Behavior Evaluation
Static characterization is performed using the Voltage Transfer Characteristic (VTC) of the CMOS inverter.

The VTC represents the relationship between the input voltage and output voltage. It shows three important operating regions: the logic HIGH region, the transition region and the logic LOW region.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/47346d1f-ca49-4676-bc84-91a06d2443b4" />


Figure 8: Static voltage-transfer characteristic

The steep transition region indicates the switching behavior of the inverter. A well-designed CMOS inverter provides clear logic levels and good noise margins.

# 1.9 CMOS Inverter Robustness
The VTC curves for different transistor sizing ratios are compared to study the robustness of the inverter.

The switching point changes when the relative strength of the PMOS and NMOS devices changes. By comparing these curves, the effect of sizing on the logic threshold and inverter symmetry can be understood. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/c3db69a2-0e7f-4418-bc8f-22d974ce3556" />


Figure 9: CMOS inverter robustness evaluation

This analysis is useful for selecting a device ratio that provides stable switching behavior and acceptable noise margins.

# 1.10 Switching Threshold Voltage
The switching threshold voltage is the input voltage at which the inverter changes from its HIGH-output state to its LOW-output state.

The threshold voltage is affected by the transistor characteristics, device sizing, body voltage and fabrication parameters. The body effect is particularly important when the source-to-body voltage is not zero.
The calculated and simulated values are compared to understand the relationship between the theoretical equations and the actual device behavior.

# 1.11 Voltage Transfer Characteristic Analysis
The voltage-transfer curve provides a complete static representation of the CMOS inverter.

At low input voltage, the PMOS is ON and the NMOS is OFF, so the output remains close to the supply voltage. At high input voltage, the NMOS is ON and the PMOS is OFF, causing the output to approach ground. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/0c0da82e-7c5c-416b-bad8-e4875ece2a90" />


Figure 11: CMOS inverter VTC

The sharp transition in the VTC demonstrates the high voltage gain of the CMOS inverter around the switching region.

# 1.12 Comparison of Different Sizing Conditions
A second sizing condition is evaluated to observe how changing the transistor dimensions affects the inverter's switching characteristics.

Changing the PMOS/NMOS ratio modifies the balance between the pull-up and pull-down networks. This can shift the switching threshold and change the rise and fall delays. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/470f5959-f5ab-45bb-abb7-641dd312ace9" />


Figure 12: Comparison of inverter sizing conditions

The simulation demonstrates why transistor sizing is an important step in standard-cell design.

# 1.13 Verification of Calculated Value
The values obtained from the simulation are verified using the calculated result. This provides an additional check on the measurements obtained from the waveform and characterization process.

The numerical verification helps ensure that the extracted parameter is consistent with the theoretical calculation. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/4d51fb51-8503-4a26-9e54-19746bf1bd87" />


Figure 13: Verification of calculated simulation parameter

Such verification improves confidence in the extracted timing and electrical characteristics.

# 1.14 Final Inverter Characterization
The final characterization summarizes the behavior of the selected CMOS inverter configuration.

The voltage-transfer characteristic, switching behavior and timing response are used together to evaluate whether the chosen transistor sizing provides the desired performance. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/72cd24be-9050-4618-8767-b34db7fb9838" />


Figure 14: Final CMOS inverter characterization

The characterization results provide the basis for proceeding towards the physical implementation of the standard cell.


# 2. SKY130A Standard-Cell Design Flow

# 2.1 Cloning the Design Repository
The standard-cell design environment is prepared by cloning the required repository into the OpenLane working directory.

Git is used to obtain the required source files, configuration files, technology information and supporting resources. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/8efa10f4-6cf3-4d8c-acdd-8782e537eae5" />


Figure 15: Cloning the standard-cell design repository

Repository cloning ensures that the design environment contains all the files required for subsequent layout and physical-design activities.

# 2.2 Preparing the SKY130A Technology File
After cloning the repository, the required SKY130A technology file is copied into the appropriate standard-cell design directory.

The technology file contains important information required by the layout and physical-design tools to interpret the process layers and device structures correctly.
Correct placement of the technology file is essential for opening and processing the standard-cell layout using the SKY130A technology.

# 2.3 CMOS Inverter Layout
The CMOS inverter layout is opened using the layout editor. The physical arrangement of the PMOS and NMOS devices, contacts, diffusion regions, polysilicon and metal layers can be observed.

The layout represents the physical implementation of the transistor-level CMOS inverter designed during the simulation stage. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/b59bce4e-84e7-40b5-8217-df5ca96948ea" />


Figure 17: SKY130A CMOS inverter layout

A well-designed layout must satisfy the technology design rules while maintaining compact area and proper electrical connectivity.

# 3. 16-Mask CMOS Fabrication Process
The next part of the module explains the major stages involved in manufacturing a CMOS integrated circuit using a 16-mask process.

The fabrication sequence consists of repeated steps of oxidation, photolithography, implantation, deposition, etching and metallization. Each mask defines a specific physical region required to build the CMOS devices.

# 3.1 Selecting the Silicon Substrate
The fabrication process begins with the selection of a P-type silicon substrate.

The substrate provides the mechanical and electrical foundation on which the CMOS devices are fabricated. The substrate is selected with a controlled doping concentration, resistivity and crystal orientation. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/7f26f19d-31cf-4977-8647-3a2210c64899" />


Figure 18: Selection of P-type silicon substrate

Starting with a controlled substrate is important because the substrate properties directly influence device characteristics such as threshold voltage, junction behavior and leakage.

# 3.2 Formation of Active Regions – Mask 1
The first mask is used to define the active regions in which transistors will eventually be formed.

Field oxide is grown over the regions that must be electrically isolated. The LOCOS process, or Local Oxidation of Silicon, is used to separate active device areas. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/f468a309-c815-4a68-bbf2-529c374bbedd" />


Figure 19: Active region formation using Mask 1

The field oxide prevents unwanted conduction between neighboring devices and provides electrical isolation.

The LOCOS structure also produces the characteristic bird's-beak region near the boundary of the field oxide.

# 3.3 P-Well Formation – Boron Implantation
The next stage forms the required well regions for complementary MOS devices.

Boron is a P-type dopant and is implanted into the selected region to form the P-well. The implantation energy and dose are controlled to obtain the required doping profile. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/c3243c47-9730-4eac-ad25-aa6973b8e8c2" />


Figure 20: P-well formation using boron implantation

The P-well provides the body region in which the NMOS transistor will be fabricated. Proper well formation is essential for achieving the required threshold voltage and isolation.

# 3.4 N-Well Formation – Phosphorus Implantation
Phosphorus, which is an N-type dopant, is implanted into the selected region to form the N-well.

The N-well provides the body region required for the PMOS transistor in a CMOS process.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/41fb7314-e654-4bee-91e1-6ecc4c186630" />


Figure 21: N-well formation using phosphorus implantation

The combination of N-well and P-well regions enables both PMOS and NMOS transistors to be fabricated on the same silicon substrate.

# 3.5 Gate Formation – Initial Structure
After the well regions are formed, the process moves towards gate formation.

The gate is one of the most important parts of a MOS transistor because it controls the formation of the conducting channel between source and drain. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/e0dd9c35-015d-44aa-80ec-fd912742ccfa" />


Figure 22: Initial stage of gate formation

The gate structure separates the control terminal from the semiconductor using a thin insulating oxide layer. This allows the MOS transistor to be controlled using an electric field.

# 3.6 Threshold Voltage and Body Effect
The threshold voltage of a MOS transistor is not constant under all operating conditions. It depends on the manufacturing process, substrate doping, oxide capacitance and source-to-body voltage.

The threshold-voltage equation includes the body-effect term, which represents the change in threshold voltage when the source and body are at different potentials.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/c21e1f49-b5da-4905-b2b1-2457c7b5811b" />


Figure 23: Threshold voltage and body-effect analysis

The body effect becomes particularly important when the source-to-body voltage changes. Understanding this effect is necessary for accurate transistor modeling and CMOS circuit design.

# 3.7 Gate Patterning – Mask 4
Photolithography is used to define the required gate pattern. A photoresist layer is deposited and exposed according to the mask pattern.

Mask 4 defines the region that is retained or removed during the subsequent processing step. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/35757ea9-4823-48fc-87a5-1b9a3b7ba382" />


Figure 24: Gate formation using Mask 4

Accurate gate patterning is critical because the gate length directly affects important transistor characteristics such as drive current, delay and short-channel behavior.

# 3.8 Gate Patterning – Mask 5
The next mask is applied to further define the required gate-related structure.

The photoresist acts as a temporary protective layer, allowing selected regions to undergo etching or processing while protecting the remaining regions.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/ca65e8aa-a87f-47ba-b440-168682864371" />


Figure 25: Gate processing using Mask 5

This stage refines the physical gate structure and prepares the transistor regions for subsequent implantation steps.

# 3.9 Gate Patterning – Mask 6
Mask 6 is used during the continuation of the gate-processing sequence.

The patterned structure now provides the physical definition required for controlling the later source/drain implantation regions.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/8e631db6-31ea-4389-a479-1b2ec4ff6f3f" />


Figure 26: Gate formation using Mask 6

The gate acts as the self-aligned reference for forming the source and drain regions, which is a key feature of modern MOS fabrication.


# 4. Lightly Doped Drain Formation

# 4.1 LDD Formation – Mask 7
The Lightly Doped Drain (LDD) process introduces lightly doped regions close to the transistor channel.

These regions reduce the electric field near the drain and help improve device reliability. The LDD structure is particularly important for reducing hot-carrier effects. 
The lightly doped extension provides a gradual transition between the heavily doped source/drain region and the channel.

# 4.2 LDD Formation – Mask 8
The complementary LDD implantation is performed for the opposite transistor type.

The correct dopant type is selected depending on whether the region belongs to the NMOS or PMOS device. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/8f353b30-cac6-48bf-ad5b-1dd91e7d80a4" />


Figure 28: Complementary LDD implantation using Mask 8

The LDD process provides a balance between transistor drive capability and reliability by controlling the electric field near the drain.

# 5. Source and Drain Formation

# 5.1 Source and Drain Formation – Mask 9
After LDD formation, heavily doped source and drain regions are created.

The implantation is aligned with the gate structure so that the source and drain are positioned on either side of the channel. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/61bc1b69-0417-4487-b0b8-bfaf5d5b06b5" />


Figure 29: Source and drain formation using Mask 9

The heavily doped regions provide low-resistance electrical terminals for the MOS transistor while the region underneath the gate remains available for channel formation.

# 5.2 Source and Drain Formation – Mask 10
The complementary source/drain implantation is then performed for the opposite transistor type.

The NMOS and PMOS require opposite conductivity types for their source and drain regions. 
At this stage, the essential transistor structures are present: wells, gate, source and drain. These structures form the basic building blocks of the CMOS inverter.

# 6. Contacts and Interconnect Formation

# 6.1 Local Contacts and Interconnects
Once the transistor regions are completed, electrical contacts are created to connect the device terminals to the interconnect layers.

The contact process provides a low-resistance electrical path from the source, drain and gate regions to the metal interconnect system. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/da43931d-ac4b-4216-89a3-564e54c515a0" />


Figure 31: Formation of local contacts and interconnects

The process includes cleaning and etching steps to ensure that the contact regions are properly prepared before metal deposition.

Proper contact formation is important because defects or high contact resistance can significantly affect circuit performance.

# 7. Higher-Level Metal Formation

# 7.1 Higher-Level Metal Interconnections
The final stage shown in this module is the formation of higher-level metal interconnections.

Metal layers are used to electrically connect different transistor terminals and different parts of the integrated circuit. Contact holes are opened where connections between different layers are required. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/6be891f7-f0ed-4446-9440-6c0fa2d89a42" />


Figure 32: Higher-level metal formation

The final metallization stage converts the isolated transistor structures into a complete electrically connected circuit. Higher-level metal layers are essential for routing signals, power and ground throughout the chip.

# 8. Complete CMOS Design and Fabrication Flow
The overall workflow covered in this module can be summarized as:
```text
CMOS Inverter Design
        ↓
SPICE Model Setup
        ↓
Transient Simulation
        ↓
Waveform Analysis
        ↓
Rise/Fall Delay Measurement
        ↓
Voltage Transfer Characteristic
        ↓
Switching Threshold Analysis
        ↓
Transistor Sizing Optimization
        ↓
SKY130A Standard-Cell Setup
        ↓
Repository and Technology File Setup
        ↓
CMOS Inverter Layout
        ↓
Silicon Substrate
        ↓
Active Region Formation
        ↓
N-Well / P-Well Formation
        ↓
Gate Formation
        ↓
LDD Formation
        ↓
Source / Drain Formation
        ↓
Local Contacts
        ↓
Metal Interconnects
        ↓
Higher-Level Metal
        ↓
Completed CMOS Structure
```

# 9. Layout and Abstract View
The first stage of the design flow is the creation of the standard-cell layout using the SKY130A technology.

The layout represents the physical implementation of the CMOS circuit using the required layers such as:

- Metal layers
  
- Polysilicon
  
- Diffusion
  
- Contacts
  
- Well regions
  
- Power and ground connections
The corresponding abstract view represents the simplified physical information of the cell that can be used by the digital implementation flow.
The layout and abstract views are checked to ensure that the cell has the required physical structure and proper connectivity.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/86413d01-40f7-4621-a6ee-e167aae14306" />


Figure 1: Layout and abstract representation of the standard cell

# 10. Defining the Cell Boundary
After creating the layout, a proper cell boundary is defined.

The boundary determines the physical area occupied by the standard cell. It is important because standard cells must follow a well-defined height and width so that they can be placed together during physical design.

The cell boundary also helps maintain:

- Consistent cell dimensions
  
- Proper placement
  
- Alignment with neighbouring cells
  
- Correct power and ground rail positions
  
- Compatibility with the standard-cell library
The layout is therefore organized inside the defined cell boundary.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/e95abd32-a9a4-44e6-8ea7-0f348b14863a" />


Figure 2: Defined standard-cell boundary

# 11. Power and Ground Connectivity
The next step is to establish the power and ground connections of the cell.

For the CMOS standard cell:

- VDD provides the positive supply voltage.
  
- GND provides the reference/ground connection.
- 
The power and ground segments are connected to the appropriate transistor terminals and are routed through the required layout layers.

Correct power and ground connectivity is essential for reliable circuit operation and for maintaining compatibility with the standard-cell architecture.

# 12. Layout Extraction
Once the physical layout is completed, the layout information is extracted to obtain the electrical representation of the circuit.

The extraction process identifies:

- Devices present in the layout
  
- Electrical connections
  
- Nodes
  
- Parasitic elements
  
- Device dimensions
  
- Power and ground connections
  
The extracted information is used to generate a SPICE-compatible representation of the physical layout.
This step is important because simulation of the extracted circuit provides a more realistic representation of the implemented layout than an ideal schematic-level simulation. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/eb02a2cf-1cb3-41a5-bace-d9fbe1789f46" />


Figure 4: Extraction of the layout

# 13. Generating the Extracted Netlist
After extraction, the generated files are checked in the working directory.

The extracted netlist contains the electrical information obtained from the physical layout. It provides the connectivity and device information required for circuit simulation.

The generated files are verified before proceeding to the SPICE simulation stage.

Typical files generated during this stage include the extracted layout information and SPICE-compatible netlist files.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/3bcaefed-e3d4-4527-954f-6ac970864dc6" />


Figure 5: Generated extracted files and netlist

# 14. Creating the SPICE File
The extracted circuit information is then used to prepare the SPICE simulation file.

The SPICE file contains:

- Technology/model information
  
- Cell subcircuit definition
  
- Input and output nodes
  
- Power supply connections
  
- Ground connections
  
- Transistor information
  
- Simulation parameters
  
The standard-cell subcircuit is defined using the extracted device parameters so that the physical implementation can be simulated using NGSPICE. 

<img width="700" alt="S" src="https://github.com/user-attachments/assets/84dfea15-8ac5-45e1-9151-b3ebda041bba" />


Figure 6: SPICE file generated for simulation

# 15. Transient Simulation using NGSPICE
The extracted SPICE circuit is simulated using NGSPICE.

Transient analysis is performed to observe how the output voltage changes with time when the input signal is applied.

The simulation setup applies a changing input signal while the cell is powered using the required supply voltage.

During simulation, the important nodes such as:

- Input
  
- Output
  
- VDD
  
- GND
  
are observed.

The initial simulation output confirms that the extracted circuit is electrically connected and can be simulated successfully.

<img width="700" alt="S" src="https://github.com/user-attachments/assets/818c71f2-49f3-4f52-8530-25657a50d42d" />


# 16. Input and Output Waveforms
The final simulation result is observed using the generated transient waveform.

The input signal changes between logic LOW and logic HIGH. The CMOS inverter responds by producing the complementary output.

Therefore:

- When the input is LOW, the output becomes HIGH.
- When the input is HIGH, the output becomes LOW.
The waveform confirms the expected inverter functionality.

The simulated voltage levels are close to the expected supply and ground levels, demonstrating correct operation of the extracted standard cell.

<img width="700" alt="s" src="https://github.com/user-attachments/assets/01448e21-f1a4-4976-ae17-689507aa2de5" />


Figure 8: Simulated input and output transient waveforms

# 17. Physical Verification and Layout Analysis
After completing the basic layout, the physical implementation is examined carefully to ensure that the required layers and connections are present.

The layout is checked for correct transistor formation, diffusion regions, polysilicon structures, contacts, metal routing, and power connections.

The purpose of this stage is to make sure that the physical representation corresponds to the intended CMOS circuit.

A properly constructed layout should maintain:

- Correct device connectivity
  
- Correct power distribution
  
- Proper cell boundary
  
- Valid layer usage
  
- Proper transistor arrangement
  
# 18. Standard Cell Layout Structure
The standard cell follows the conventional CMOS standard-cell arrangement.

The PMOS network is placed towards the upper portion of the cell and is associated with the VDD rail, while the NMOS network is placed towards the lower portion and is associated with the GND rail.

The input connection controls the gates of the transistors, while the output is obtained from the common connection between the pull-up and pull-down networks.

This arrangement allows the cell to provide complementary logic operation while maintaining a regular physical structure suitable for standard-cell libraries.

# 19.Overall Design Flow
The complete design flow followed in this work is:
```text
SKY130A Technology
        ↓
Standard Cell Layout
        ↓
Define Cell Boundary
        ↓
Power & Ground Connections
        ↓
Layout Verification
        ↓
Parasitic Extraction
        ↓
SPICE Netlist Generation
        ↓
SPICE Simulation Setup
        ↓
NGSPICE Transient Analysis
        ↓
Input / Output Waveform
        ↓
Functional and Timing Analysis
```

# Overall Result
The CMOS inverter design was successfully implemented, simulated, characterized, and taken through the physical design flow using the SKY130A technology. The complete process demonstrated the relationship between the transistor-level circuit, physical layout, extracted netlist, and post-layout SPICE simulation.

The major results obtained from the work are:

- The CMOS inverter circuit was designed using complementary PMOS and NMOS transistors.
  
- SPICE simulation was performed to verify the functional behaviour of the CMOS inverter.
  
- Transient analysis was used to observe the input and output voltage waveforms.
  
- The inverter's logic operation was verified for both LOW and HIGH input conditions.
  
- Rise and fall behaviour, propagation characteristics, switching behaviour, and voltage transfer characteristics were studied.
  
- Different transistor sizing conditions were analysed to understand their effect on inverter performance.
  
- The inverter was implemented as a physical standard-cell layout using the SKY130A technology.
  
- The cell boundary, power and ground connections, diffusion regions, polysilicon, contacts, and metal interconnects were established.
  
- The physical layout was extracted to generate an electrical representation of the implemented circuit.
  
- The extracted netlist was used to prepare the SPICE simulation setup.
  
- NGSPICE transient simulation was performed on the extracted circuit to verify the post-layout behaviour.
  
- The obtained waveform confirmed the expected CMOS inverter operation.
  
- The CMOS fabrication process was studied through the complete 16-mask fabrication sequence, including well formation, gate formation, LDD formation, source/drain formation, contacts, and metal interconnections.
  
Overall, the results establish a clear connection between circuit design → SPICE simulation → transistor characterization → physical layout → extraction → post-layout simulation → CMOS fabrication.

# Conclusion
This module provided a complete understanding of CMOS inverter design from the circuit level to the physical implementation and fabrication level. The CMOS inverter was first analysed using SPICE to understand its electrical and switching behaviour. Its transient response, voltage transfer characteristics, switching threshold, rise and fall behaviour, and the influence of transistor sizing were studied in detail.

The design was then implemented as a SKY130A standard-cell layout. Important physical-design elements such as the cell boundary, PMOS and NMOS regions, power and ground rails, contacts, polysilicon, diffusion, and metal interconnects were considered during layout implementation.

The completed layout was extracted to obtain the corresponding electrical netlist. This extracted representation was simulated using NGSPICE, and the resulting waveforms were compared with the expected CMOS inverter behaviour. This step demonstrated how physical layout information affects the electrical representation of the circuit and how post-layout simulation can be used for verification.

In addition, the 16-mask CMOS fabrication process was studied to understand how the designed transistor structures are physically fabricated on a silicon wafer through multiple masking, implantation, deposition, etching, and metallization steps.

Thus, the module successfully demonstrated the complete RTL-to-physical-design and CMOS implementation concept, while providing practical exposure to SPICE, NGSPICE, Magic VLSI, SKY130A PDK, layout extraction, standard-cell design, and CMOS fabrication technology.
