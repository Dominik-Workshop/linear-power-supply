# Linear power supply

> [!CAUTION]
> This project was initiated in 2021, when my skills were significantly more limited. As a result, there might be areas for great improvement. I occasionally enhance both the performance and readability of project files for better understanding.

## Overview

**Linear power supply** capable of delivering up to **250W** (`0-28V`, `0.01-10A`).

<img align="center" src="images/pictures/psu_front.png"> 

### Key Features

- **Adjustable voltage and current limit**, controlled by 10-turn potentiometers.
- **On/off switch** for convenient power output control.
- **Relay transformer-tab switching** circuit for minimizing power losses by reducing the voltage differential across the linear regulator.
- **Temperature-controlled fan**.

### Learn More

[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)](https://youtu.be/JCxF-o6tLgA)

## Key design improvement

> [!IMPORTANT]
> The `Q1` transistor was changed from an `IRF9530` (**P-MOSFET**) to a `BD912` (**PNP-BJT**). This significantly **improved the power supply's stability and eliminated oscillations** in the constant current mode. Their pinouts are compatible, making it a **drop-in replacement**.
> <details>
> <summary>Click for simulation details</summary>
>
> Simulations in **LTspice** demonstrated a significant improvement in the output step response after replacing the `Q1` MOSFET with a BJT:
>
> Before (with **MOSFET**):
> <image src="images/screenshots/old_step.png">
> After (with **BJT**):
> <image src="images/screenshots/new_step.png">
> (The Bode plot also showed better characteristics with the BJT)
> </details>

## Output Measurements

For detailed output voltage waveforms before the `Q1` transistor was changed to a BJT, please see the [measurements.pdf](measurements.pdf) file.

## Project Details

### Mains Transformer

A `12V`, `300VA` transformer was modified for this project. The secondary winding, originally consisting of 4 parallel wires, was reconfigured. These wires were split into two sets and connected in series to achieve `24V` with a center tap. An additional winding of approximately `8V` was also added.
![Modified transformer](https://user-images.githubusercontent.com/100617381/183007895-9f96c52b-03fa-483e-87bb-669523269e95.png)

### Heatsink

An old graphics card heatsink is used for cooling the series pass power transistors.

![Heatsink](https://user-images.githubusercontent.com/100617381/183007879-ed8218c8-d9f7-4f5c-a0ad-9686e3b1729e.png)

### Original inspiration

The design was initially based on the **SN1534** power supply. Schematics and further details related to the original design can be found [here](Schemat%20ideowy%20SN1534.pdf).

## Used Tools

- [Autodesk EAGLE](https://www.autodesk.com/products/eagle/) - Schematic and PCB design
- [Autodesk Fusion 360](https://www.autodesk.com/products/fusion-360/) - 3D modeling
- [Arduino](https://www.arduino.cc/) - Firmware development
- [LTspice](https://www.analog.com/ltspice) - SPICE circuit simulation
