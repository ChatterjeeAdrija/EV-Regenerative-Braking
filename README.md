# EV-Regenerative-Braking
Simulation and electrical design of a regenerative braking system using a PMDC motor, two-quadrant DC/DC converter and PI-based current control.
# Regenerative Braking System Using a PMDC Motor and Two-Quadrant DC/DC Converter

## Overview

This project presents the simulation and electrical design of a simplified regenerative braking system for an electric vehicle application.

A 24 V, 250 W Permanent Magnet DC (PMDC) motor is used as the reference motor. During regenerative braking, the motor operates as a generator and converts part of the mechanical energy of the rotating system into electrical energy. A two-quadrant DC/DC converter is used to control the electrical power flow, while a PI controller regulates the regenerative current.

The system was modelled and tested in MATLAB/Simulink and the corresponding electrical schematic was developed using AutoCAD Electrical.

## Objectives

- Model a PMDC motor for regenerative braking operation.
- Implement a two-quadrant DC/DC converter.
- Develop PI-based regenerative current control.
- Study the effect of different regenerative current references.
- Analyse motor speed, electromagnetic torque and armature current.
- Estimate recovered electrical energy and regenerative efficiency.
- Develop the corresponding power and control schematic in AutoCAD Electrical.

## System Specifications

| Parameter | Value |
|---|---:|
| Motor Type | PMDC Motor |
| Rated Voltage | 24 V |
| Rated Power | 250 W |
| Rated Speed | 3000 rpm |
| Rated Current | 13.4 A |
| Rated Torque | 0.80 N·m |
| Battery Voltage | 12 V |
| Battery Capacity | 5.4 Ah |
| Initial Battery SOC | 80% |
| PWM Frequency | 15 kHz |
| PI Controller | Kp = 0.5, Ki = 40 |

## Control Strategy

The regenerative current is controlled using a PI controller.

The current error is calculated as:

$$
e(t)=I_a-I_{ref}
$$

The PI controller generates the required duty-cycle command:

$$
u(t)=K_p e(t)+K_i\int e(t)\,dt
$$

The resulting PWM signal is used to control the two switching devices of the converter.

For the implemented gate-control scheme:

- **Q1:** Inverted PWM
- **Q2:** Direct PWM

Regenerative operation is identified by:

$$
\omega > 0,\qquad I_a < 0,\qquad T_e < 0
$$

where negative electromagnetic torque opposes the direction of rotation and produces the braking action.

## Simulation Cases

Three regenerative current references were investigated:

| Current Reference | Final Current | Final Speed | Final Torque |
|---:|---:|---:|---:|
| −5 A | −5.2 A | 203 rad/s | −0.26 N·m |
| −8 A | −8.0 A | 175 rad/s | −0.50 N·m |
| −13.4 A | −13.4 A | 140 rad/s | −0.77 N·m |

The results show that increasing the magnitude of the regenerative current produces greater braking torque and a faster reduction in motor speed.

## Energy Recovery

The mechanical energy removed from the rotating system was estimated using:

$$
\Delta E_k=
\frac{1}{2}J(\omega_i^2-\omega_f^2)
$$

The recovered electrical energy was estimated from the battery charging power:

$$
E_{rec}=\int -V_bI_b\,dt
$$

The approximate regenerative efficiency was calculated as:

$$
\eta_{regen} = \frac{E_{rec}}{\Delta E_k} \times 100\%
$$
### Comparative Results

| Current Reference | Kinetic Energy Removed | Recovered Energy | Approx. Efficiency |
|---:|---:|---:|---:|
| −5 A | 287.4 J | 126.0 J | 43.8% |
| −8 A | 340.4 J | 140.0 J | 41.1% |
| −13.4 A | 395.5 J | 170.3 J | 43.1% |

The recovered-energy values are based on the simulated battery SOC response and are treated as approximate values for this simplified model.

## Software Used

- MATLAB/Simulink
- AutoCAD Electrical

## Project Files

### `MATLAB_Simulink/`
Contains the MATLAB/Simulink model used for modelling and simulation of the regenerative braking system.

### `AutoCAD_Electrical/`
Contains the electrical schematic representing the battery, two-quadrant DC/DC converter, PMDC motor and control signal paths.

### `Results/`
Contains the comparison tables and simulation results used for analysis.

## Key Learning Outcomes

Through this project, I worked on:

- PMDC motor mathematical modelling
- Regenerative braking principles
- Two-quadrant DC/DC converter operation
- PI current control
- PWM generation and gate control
- Motor torque and speed analysis
- Battery energy recovery estimation
- MATLAB/Simulink modelling
- Electrical schematic development using AutoCAD Electrical

## Future Scope

The simplified model can be extended by incorporating a more detailed vehicle model, mechanical braking interaction, battery charging constraints, converter losses, thermal effects and more advanced regenerative braking control strategies.

## Author

**Adrija Chatterjee**

Electrical Engineering Student
