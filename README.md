# VSDOpen21 Bandgap Reference Circuit Workshop
![VSDOpen21](/assets/vsdopentutorial_banner.png)


![AIM](/assets/aim_banner.png)
![BGR Umbrella](/assets/pre_layout/bgr_umbrella_curve_with_ideal_opamp.png)

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
![BGR](/assets/bgr.png)
- Requirement of *reference voltage* independent of 
    - Process
    - Supply Voltage
    - Temprature

** PVT Independent Biasing
- Typical Temperature coefficient : 10-50 ppm/&deg;C
- Typical Power Supply Rejection : 40-60 db 

## Introduction to BGR
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
        - Zero current biasing to desired biasing

** Self Biased Current Mirror Based BGR

 # Specification
![Spec](assets/spec.png)

# Model Used
- MOSFET
<table>
    <tr>
        <td></td>
        <td>NFET</td>
        <td>PFET</td>
    </tr>
    <tr>
        <td>Type</td>
        <td>LVT</td>
        <td>LVT</td>
    </tr>
    <tr>
        <td>Voltage</td>
        <td>1.8V</td>
        <td>1.8V</td>
    </tr>
    <tr>
        <td>Threshold Voltage</td>
        <td>~0.4V</td>
        <td>~0.6V</td>
    </tr>
    <tr>
        <td>Name of Model</td>
        <td>sky130_fd_pr__nfet_01v8_lvt</td>
        <td>sky130_fd_pr__pfet_01v8_lvt</td>
    </tr>
</table>



- BJT
<table>
    <tr>
        <td></td>
        <td>PNP</td>
    </tr>
    <tr>
        <td>Current Rating</td>
        <td>1&mu;A-10&mu;A/&mu;<sup>2</sup></td>
    </tr>
    <tr>
        <td>Beta</td>
        <td>~12</td>
    </tr>
    <tr>
        <td>Emitter Area</td>
        <td>11.56 &mu;m<sup>2</sup></td>
    </tr>
    <tr>
        <td>Name of Model</td>
        <td>sky130_fd_pr__pnp_05v5_W3p40l3p40</td>
    </tr>
</table>


- Resistor
<table>
    <tr>
        <td></td>
        <td>RPOLYH</td>
    </tr>
    <tr>
        <td>Sheet Resistance</td>
        <td>~350&Omega;</td>
    </tr>
    <tr>
        <td>Temperature Coefficient</td>
        <td>2.5&Omega;/&deg;C</td>
    </tr>
    <tr>
        <td>Bin Width</td>
        <td>0.35&mu;, 0.69&mu;, 1.41&mu;, 5.73&mu;</td>
    </tr>
    <tr>
        <td>Name of Model</td>
        <td>sky130_fd_pr__res_high_po</td>
    </tr>
</table>

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
![CTAT Plot](/assets/pre_layout/ctat_i.png)
![CTAT Plot](/assets/pre_layout/ctat_slope.png)

## PTAT Circuit
![PTAT](/assets/ptat_ckt.png)
- PTAT is achieved by subracting two different CTATs with different slopes
![PTAT Plot](/assets/pre_layout/ptat.png)
![PTAT Plot](/assets/pre_layout/ptat_slope.png)


## Self Biased Current Mirror

## Start-up Circuit


## BGR Circuit with Ideal Opamp
![BGR Plot](/assets/pre_layout/bgr_with_ideal_opamp.png)

## BGR Circuit with Self Biased Current Mirror(SBCM)


# Layout Design Using Magic
![BGR](/assets/layout/bgr_top.png)

- Points to note
    - Design of resistor involves 4 dummy resistors to make circuit symmetric and stable
    - Use of gauard ring
    - Use of many dummy pnp bjts

The subcells used for the design are
- PNP
![](/assets/layout/pnp.png)
- NFETs
![](/assets/layout/nfets.png)
- PFETs
![](/assets/layout/pfets.png)
- Resistors
![](/assets/layout/resistors.png)
- Starter NFET
![](/assets/layout/starter_nfet.png)


# Post Layout Simulation

# LVS Check using Netgen
- Note: Remove parasitics during LVS or else LVS will fail

To do lvs in netgen window execute
```
lvs pre_layout.spice post_layout.spice <netgen_rule.tcl>
```

# Report By
- R.V.Rohinth Ram

# Acknowledgements
- Dr. Saroj Rout, Adjunct Prof., SIT Bhubaneswar
- Dr. Santunu Sarangi, Asst Prof., SIT Bhubaneswar
- Kunal Ghosh, Co-founder, VLSI System Design (VSD) Corp. Pvt. Ltd. - kunalpghosh@gmail.com


---
 - Thanks to entire team of this workshop
---