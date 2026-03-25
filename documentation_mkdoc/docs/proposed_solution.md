# Proposed Solution

Lacerta proposes an open hardware platform designed to simplify the creation of graphical interfaces for embedded systems by moving the interface generation process from software to dedicated hardware. The platform introduces a configurable interface rendering engine implemented as a custom ASIC integrated within the Caravel SoC user project area.

Instead of requiring developers to manually program complex graphical interfaces in firmware, Lacerta allows the interface to be **visually designed using a graphical configuration tool**. This tool enables users to place graphical elements such as buttons, bars, numeric indicators, and status displays within a virtual layout that represents the final interface.

Once the interface is designed, the configuration is exported as a description file that can be loaded into the Lacerta hardware engine. The ASIC interprets this configuration and generates the graphical output in real time.

## Hardware-Based Interface Rendering

The Lacerta ASIC includes a hardware rendering engine capable of generating graphical interface components directly in hardware. This approach significantly reduces the computational burden typically placed on embedded processors.

By implementing the interface generation logic in dedicated hardware, Lacerta provides several advantages:

- deterministic graphical rendering  
- reduced firmware complexity  
- lower processor utilization  
- improved system responsiveness  
- simplified integration with sensors and control systems

The generated interface is transmitted to a display through a **VGA video output**, enabling the system to drive standard monitors or embedded displays without requiring external graphics processors.

## Integration with Embedded Systems

Lacerta is designed to interact with both **analog and digital signal sources**, allowing real-world system data to be directly visualized through the graphical interface.

Analog signals originating from sensors such as temperature, pressure, voltage, or current sensors can be connected through external signal conditioning or analog-to-digital conversion stages. Digital signals produced by microcontrollers, communication peripherals, or control logic can be connected directly through digital interfaces.

These signals are interpreted by the Lacerta interface engine and mapped to graphical elements such as bars or numeric indicators, enabling real-time visualization of system parameters.

<p align="center">
<img src="../img/flow_inputs.svg">
</p>
<p align="center">
<b>Figure 3.</b> Example of heterogeneous input signals connected to the Lacerta platform. Sensor data, digital signals, and external controller outputs are processed by the Lacerta engine to update graphical interface elements in real time.
</p>

## Interface Design Workflow

The Lacerta platform introduces a streamlined workflow for creating embedded graphical interfaces:

1. **Interface Design**  
   A graphical design tool allows users to create a custom interface layout using predefined visual components.

2. **Configuration Generation**  
   The tool exports a configuration file describing the interface structure and graphical element parameters.

3. **Hardware Deployment**  
   The configuration is loaded into the Lacerta hardware engine integrated in the Caravel platform.

4. **Runtime Visualization**  
   Incoming sensor or system data dynamically updates the graphical elements rendered by the hardware.

This workflow allows developers to design complex interfaces without writing extensive display control firmware.

<p align="center">
<img src="../img/Flow_interface.drawio.svg">
</p>
<p align="center">
<b>Figure 4.</b> Lacerta interface creation workflow. A graphical editor is used to design custom interface layouts, which are translated into configuration data interpreted by the Lacerta hardware engine to generate the graphical display.
</p>


## Open and Reproducible Architecture

Lacerta is designed as a **fully open-source reference architecture**. The project includes all required design artifacts to reproduce the system, including:

- RTL source code for the ASIC implementation  
- OpenLane physical design flow integration  
- verification testbenches  
- PCB design files  
- firmware examples  
- documentation and interface design tools

By providing an open and reproducible platform, Lacerta enables developers, researchers, and educators to build customizable embedded human–machine interfaces for industrial, commercial, and edge-IoT applications.