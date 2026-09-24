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

IIIIII

# 1.3 SPICE Simulation Execution
After defining the circuit and device parameters, the SPICE simulation is executed. The simulator solves the electrical behavior of the inverter as the input voltage changes with time.

The input signal is applied to the common gate terminal of the PMOS and NMOS transistors. Depending on the input voltage, one transistor turns ON while the other turns OFF, producing the inverted output. 

IIIIII

Figure 3: Execution of CMOS inverter SPICE simulation

This step verifies that the inverter operates correctly before detailed timing and static characterization are performed.

# 1.4 Input and Output Waveforms
The transient simulation produces both the input and output waveforms. The output waveform is complementary to the input waveform, demonstrating the fundamental operation of the CMOS inverter.

When the input is LOW, the PMOS transistor conducts and the output is pulled towards the supply voltage. When the input becomes HIGH, the NMOS transistor conducts and the output is pulled towards ground.

IIIII

Figure 4: CMOS inverter input and output waveforms

The waveform confirms the correct logical inversion operation and also provides the information required for measuring propagation delay and transition times.

# 1.5 Transient Response Analysis
The transient response is examined to understand how quickly the inverter responds to changes in the input signal.

The transition of the output does not occur instantaneously because the transistor network and load capacitance require a finite amount of time to charge or discharge. This delay is an important performance parameter in digital circuits. 

IIIII

Figure 5: Transient response of the CMOS inverter

The measured waveform is used to determine parameters such as rise time, fall time and propagation delay.

# 1.6 Detailed Waveform Observation
The simulation waveform is further examined over a selected time interval. This allows the transition points of the input and output signals to be identified accurately.

The time difference between corresponding input and output transitions represents the propagation delay of the inverter. 

IIIIII

Figure 6: Detailed observation of the transient waveform

Accurate waveform observation is necessary for obtaining reliable timing measurements and comparing different transistor sizing conditions.

# 1.7 Effect of PMOS/NMOS Sizing
The performance of a CMOS inverter strongly depends on the relative sizing of the PMOS and NMOS transistors. Different width ratios are therefore simulated and compared.

Increasing transistor width increases the available drive current and can reduce the time required to charge or discharge the load. However, excessive sizing also increases capacitance and may affect overall performance. 

IIIIII

Figure 7: Effect of transistor sizing on inverter behavior

The comparison helps identify a suitable PMOS-to-NMOS sizing ratio for achieving balanced inverter operation.

# 1.8 Static Behavior Evaluation
Static characterization is performed using the Voltage Transfer Characteristic (VTC) of the CMOS inverter.

The VTC represents the relationship between the input voltage and output voltage. It shows three important operating regions: the logic HIGH region, the transition region and the logic LOW region.

IIII

Figure 8: Static voltage-transfer characteristic

The steep transition region indicates the switching behavior of the inverter. A well-designed CMOS inverter provides clear logic levels and good noise margins.

# 1.9 CMOS Inverter Robustness
The VTC curves for different transistor sizing ratios are compared to study the robustness of the inverter.

The switching point changes when the relative strength of the PMOS and NMOS devices changes. By comparing these curves, the effect of sizing on the logic threshold and inverter symmetry can be understood. 

IIIII

Figure 9: CMOS inverter robustness evaluation

This analysis is useful for selecting a device ratio that provides stable switching behavior and acceptable noise margins.

# 1.10 Switching Threshold Voltage
The switching threshold voltage is the input voltage at which the inverter changes from its HIGH-output state to its LOW-output state.

The threshold voltage is affected by the transistor characteristics, device sizing, body voltage and fabrication parameters. The body effect is particularly important when the source-to-body voltage is not zero. 

IIIII

Figure 10: Switching threshold analysis

The calculated and simulated values are compared to understand the relationship between the theoretical equations and the actual device behavior.

# 1.11 Voltage Transfer Characteristic Analysis
The voltage-transfer curve provides a complete static representation of the CMOS inverter.

At low input voltage, the PMOS is ON and the NMOS is OFF, so the output remains close to the supply voltage. At high input voltage, the NMOS is ON and the PMOS is OFF, causing the output to approach ground. 

IIIII

Figure 11: CMOS inverter VTC

The sharp transition in the VTC demonstrates the high voltage gain of the CMOS inverter around the switching region.

# 1.12 Comparison of Different Sizing Conditions
A second sizing condition is evaluated to observe how changing the transistor dimensions affects the inverter's switching characteristics.

Changing the PMOS/NMOS ratio modifies the balance between the pull-up and pull-down networks. This can shift the switching threshold and change the rise and fall delays. 

IIIII

Figure 12: Comparison of inverter sizing conditions

The simulation demonstrates why transistor sizing is an important step in standard-cell design.

# 1.13 Verification of Calculated Value
The values obtained from the simulation are verified using the calculated result. This provides an additional check on the measurements obtained from the waveform and characterization process.

The numerical verification helps ensure that the extracted parameter is consistent with the theoretical calculation. 

IIIII

Figure 13: Verification of calculated simulation parameter

Such verification improves confidence in the extracted timing and electrical characteristics.

# 1.14 Final Inverter Characterization
The final characterization summarizes the behavior of the selected CMOS inverter configuration.

The voltage-transfer characteristic, switching behavior and timing response are used together to evaluate whether the chosen transistor sizing provides the desired performance. 

IIII

Figure 14: Final CMOS inverter characterization

The characterization results provide the basis for proceeding towards the physical implementation of the standard cell.


# 2. SKY130A Standard-Cell Design Flow

# 2.1 Cloning the Design Repository
The standard-cell design environment is prepared by cloning the required repository into the OpenLane working directory.

Git is used to obtain the required source files, configuration files, technology information and supporting resources. 

IIII

Figure 15: Cloning the standard-cell design repository

Repository cloning ensures that the design environment contains all the files required for subsequent layout and physical-design activities.

# 2.2 Preparing the SKY130A Technology File
After cloning the repository, the required SKY130A technology file is copied into the appropriate standard-cell design directory.

The technology file contains important information required by the layout and physical-design tools to interpret the process layers and device structures correctly. 

IIII

Figure 16: Copying the SKY130A technology file

Correct placement of the technology file is essential for opening and processing the standard-cell layout using the SKY130A technology.

# 2.3 CMOS Inverter Layout
The CMOS inverter layout is opened using the layout editor. The physical arrangement of the PMOS and NMOS devices, contacts, diffusion regions, polysilicon and metal layers can be observed.

The layout represents the physical implementation of the transistor-level CMOS inverter designed during the simulation stage. 

IIII

Figure 17: SKY130A CMOS inverter layout

A well-designed layout must satisfy the technology design rules while maintaining compact area and proper electrical connectivity.

# 3. 16-Mask CMOS Fabrication Process
The next part of the module explains the major stages involved in manufacturing a CMOS integrated circuit using a 16-mask process.

The fabrication sequence consists of repeated steps of oxidation, photolithography, implantation, deposition, etching and metallization. Each mask defines a specific physical region required to build the CMOS devices.

# 3.1 Selecting the Silicon Substrate
The fabrication process begins with the selection of a P-type silicon substrate.

The substrate provides the mechanical and electrical foundation on which the CMOS devices are fabricated. The substrate is selected with a controlled doping concentration, resistivity and crystal orientation. 

IIII

Figure 18: Selection of P-type silicon substrate

Starting with a controlled substrate is important because the substrate properties directly influence device characteristics such as threshold voltage, junction behavior and leakage.

# 3.2 Formation of Active Regions – Mask 1
The first mask is used to define the active regions in which transistors will eventually be formed.

Field oxide is grown over the regions that must be electrically isolated. The LOCOS process, or Local Oxidation of Silicon, is used to separate active device areas. 

IIII

Figure 19: Active region formation using Mask 1

The field oxide prevents unwanted conduction between neighboring devices and provides electrical isolation.

The LOCOS structure also produces the characteristic bird's-beak region near the boundary of the field oxide.

# 3.3 P-Well Formation – Boron Implantation
The next stage forms the required well regions for complementary MOS devices.

Boron is a P-type dopant and is implanted into the selected region to form the P-well. The implantation energy and dose are controlled to obtain the required doping profile. 

IIIII

Figure 20: P-well formation using boron implantation

The P-well provides the body region in which the NMOS transistor will be fabricated. Proper well formation is essential for achieving the required threshold voltage and isolation.

# 3.4 N-Well Formation – Phosphorus Implantation
Phosphorus, which is an N-type dopant, is implanted into the selected region to form the N-well.

The N-well provides the body region required for the PMOS transistor in a CMOS process.

IIII

Figure 21: N-well formation using phosphorus implantation

The combination of N-well and P-well regions enables both PMOS and NMOS transistors to be fabricated on the same silicon substrate.

# 3.5 Gate Formation – Initial Structure
After the well regions are formed, the process moves towards gate formation.

The gate is one of the most important parts of a MOS transistor because it controls the formation of the conducting channel between source and drain. 

IIII

Figure 22: Initial stage of gate formation

The gate structure separates the control terminal from the semiconductor using a thin insulating oxide layer. This allows the MOS transistor to be controlled using an electric field.

# 3.6 Threshold Voltage and Body Effect
The threshold voltage of a MOS transistor is not constant under all operating conditions. It depends on the manufacturing process, substrate doping, oxide capacitance and source-to-body voltage.

The threshold-voltage equation includes the body-effect term, which represents the change in threshold voltage when the source and body are at different potentials.

IIII

Figure 23: Threshold voltage and body-effect analysis

The body effect becomes particularly important when the source-to-body voltage changes. Understanding this effect is necessary for accurate transistor modeling and CMOS circuit design.

# 3.7 Gate Patterning – Mask 4
Photolithography is used to define the required gate pattern. A photoresist layer is deposited and exposed according to the mask pattern.

Mask 4 defines the region that is retained or removed during the subsequent processing step. 

IIIII

Figure 24: Gate formation using Mask 4

Accurate gate patterning is critical because the gate length directly affects important transistor characteristics such as drive current, delay and short-channel behavior.

# 3.8 Gate Patterning – Mask 5
The next mask is applied to further define the required gate-related structure.

The photoresist acts as a temporary protective layer, allowing selected regions to undergo etching or processing while protecting the remaining regions.

IIII

Figure 25: Gate processing using Mask 5

This stage refines the physical gate structure and prepares the transistor regions for subsequent implantation steps.

# 3.9 Gate Patterning – Mask 6
Mask 6 is used during the continuation of the gate-processing sequence.

The patterned structure now provides the physical definition required for controlling the later source/drain implantation regions.

IIII

Figure 26: Gate formation using Mask 6

The gate acts as the self-aligned reference for forming the source and drain regions, which is a key feature of modern MOS fabrication.


# 4. Lightly Doped Drain Formation

# 4.1 LDD Formation – Mask 7
The Lightly Doped Drain (LDD) process introduces lightly doped regions close to the transistor channel.

These regions reduce the electric field near the drain and help improve device reliability. The LDD structure is particularly important for reducing hot-carrier effects. 

IIII

Figure 27: LDD formation using Mask 7

The lightly doped extension provides a gradual transition between the heavily doped source/drain region and the channel.

# 4.2 LDD Formation – Mask 8
The complementary LDD implantation is performed for the opposite transistor type.

The correct dopant type is selected depending on whether the region belongs to the NMOS or PMOS device. 

IIII

Figure 28: Complementary LDD implantation using Mask 8

The LDD process provides a balance between transistor drive capability and reliability by controlling the electric field near the drain.

# 5. Source and Drain Formation

# 5.1 Source and Drain Formation – Mask 9
After LDD formation, heavily doped source and drain regions are created.

The implantation is aligned with the gate structure so that the source and drain are positioned on either side of the channel. 

IIII

Figure 29: Source and drain formation using Mask 9

The heavily doped regions provide low-resistance electrical terminals for the MOS transistor while the region underneath the gate remains available for channel formation.

# 5.2 Source and Drain Formation – Mask 10
The complementary source/drain implantation is then performed for the opposite transistor type.

The NMOS and PMOS require opposite conductivity types for their source and drain regions. 

IIII

Figure 30: Complementary source and drain implantation

At this stage, the essential transistor structures are present: wells, gate, source and drain. These structures form the basic building blocks of the CMOS inverter.

# 6. Contacts and Interconnect Formation

# 6.1 Local Contacts and Interconnects
Once the transistor regions are completed, electrical contacts are created to connect the device terminals to the interconnect layers.

The contact process provides a low-resistance electrical path from the source, drain and gate regions to the metal interconnect system. 

IIII

Figure 31: Formation of local contacts and interconnects

The process includes cleaning and etching steps to ensure that the contact regions are properly prepared before metal deposition.

Proper contact formation is important because defects or high contact resistance can significantly affect circuit performance.

# 7. Higher-Level Metal Formation

# 7.1 Higher-Level Metal Interconnections
The final stage shown in this module is the formation of higher-level metal interconnections.

Metal layers are used to electrically connect different transistor terminals and different parts of the integrated circuit. Contact holes are opened where connections between different layers are required. 

IIII

Figure 32: Higher-level metal formation

The final metallization stage converts the isolated transistor structures into a complete electrically connected circuit. Higher-level metal layers are essential for routing signals, power and ground throughout the chip.

# 8. Complete CMOS Design and Fabrication Flow
The overall workflow covered in this module can be summarized as:
***/
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
***/
