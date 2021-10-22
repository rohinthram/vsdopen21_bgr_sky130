# VSDOpen21 Bandgap Reference Circuit Workshop
![VSDOpen21](/assets/vsdopentutorial_banner.png)


![AIM](/assets/aim_banner.png)
![BGR](/assets/bgr.png)

This is the report for two day workshop on 
"Analog Bandgap IP design using Sky130 PDK"


# Contents
- [Theory](#Theory)
- [Specification](#Specification)
- [Open Source Tools Used](#Open-Source-Tools-Used)
- [Pre Layout Simulations](#Pre-Layout-Simulations)
- [Layout Design Using Magic](#Layout-Design-Using-Magic)
- [Post Layout Simulations](#Post-Layout-Simulations)
- [LVS Check using Netgen](#LVS-Check-using-Netgen)
- [Report By](#Report-By)
- [Acknowledgements](#Acknowledgements)

# Theory
- Requirement of *reference voltage* independent of 
    - Process
    - Supply Voltage
    - Temprature

** PVT Independent Biasing
- Typical Temperature coefficient : 10-50 ppm/&deg;C
- Typical Power Supply Rejection : 40-60 db 

- Introduction to BGR
    - what is BGR
    - why BGR
    - Applications
    - Principle
        - CTAT (Complementary to Absolute Temperature) circuit compensates PTAT(Proportional to Absolute Temperature)
    - Types
    - Components
        - CTAT
        - PTAT
        - Self-biased current mirror
        - Reference branch circuit
        - Start-up circuit

 ** Self Biased Current Mirror Based BGR

 # Specification
![Spec](assets/spec.png)

# Model Used
![](assets/device_datasheet_1.png)
![](assets/device_datasheet_2.png)


# Circuit
![Circuit](assets/circuit.png)


# Open-Source-Tools-Used

- eSim - For schematic design (not necessary)(netlist can be written as such)
    - https://esim.fossee.in/home

- Ngspice - For simulation
    - http://ngspice.sourceforge.net/


- Magic - For Layout Design 
    - http://opencircuitdesign.com/magic/

- Netgen - For LVS (Layout vs Schematic)
    - http://opencircuitdesign.com/netgen/

- Skywater 130nm PDK
    - https://github.com/google/skywater-pdk-libs-sky130_fd_pr

# Pre Layout Simulation
## CTAT Circuit

![PTAT Plot](/assets/pre_layout/ctat.png)
![PTAT Plot](/assets/pre_layout/ctat_slope.png)

## PTAT Circuit
![PTAT](/assets/ptat_ckt.png)
- PTAT is achieved by subracting two different CTATs with different slopes
![PTAT Plot](/assets/pre_layout/ptat.png)
![PTAT Plot](/assets/pre_layout/ptat_slope.png)


## Self Biased Current Mirror

## Start-up Circuit


## BGR Circuit with Ideal Opamp

## BGR Circuit with Self Biased Current Mirror(SBCM)


# Layout Design Using Magic

# Post Layout Simulation

# LVS Check using Netgen

# Report By
- R.V.Rohinth Ram

# Acknowledgements
- Dr. Saroj Rout, Adjunct Prof., SIT Bhubaneswar
- Dr. Santunu Sarangi, Asst Prof., SIT Bhubaneswar
- Kunal Ghosh, Co-founder, VLSI System Design (VSD) Corp. Pvt. Ltd. - kunalpghosh@gmail.com


---
 - Thanks to entire team of this workshop
---