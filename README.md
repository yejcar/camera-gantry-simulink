# Two-Axis Camera Gantry System

**Module:** Mechatronics (5CCE2MCT) — King's College London  
**Year:** Second Year BEng Electronic Engineering  
**Tool:** MATLAB / Simulink

Simulink model of a dual-axis electromechanical camera gantry, controlling motion along the Y and Z axes using PID control and encoder feedback.

**Overview**
Simulink model of a dual-axis electromechanical camera gantry, controlling motion along the **Y** and **Z** axes using PID control and encoder feedback.

## Overview

This project models the electromechanical dynamics of a DC-motor-driven camera gantry and designs closed-loop PID controllers to track reference position inputs on two independent axes. The Z-axis model additionally accounts for gravitational loading, since the camera is lifted vertically along that axis.

## System Modelling

The motor and mechanical dynamics were derived from two coupled differential equations:

**Electrical (current) dynamics:**

di/dt = (1/L)(V − Ri − Keω)

**Mechanical (angular velocity) dynamics:**

dω/dt = (1/J)(Kt·i − b·ω)

These were combined in Simulink to build a DC motor model, with the output fed into an encoder block to convert motion into position feedback signals. The Y and Z feedback loops share this structure, with the Z-loop extended to include a gravity term.

### Calculated / Assumed Constants

- **Battery voltage (V):** 11.1 V (3 × 3.7 V cells)
- **Resistance (R):** 11.1 Ω
- **Back-EMF constant (Ke):** 0.0106 Vs/rad, derived from V / ω₀ at 10,000 rpm (1047.2 rad/s)
- **Inductance (L):** 0.005 H, assumed
- **Torque constant (Kt):** 0.049 Nm/A, calculated as 0.5 × stall torque × 0.0981
- **Damping (b):** 1 × 10⁻⁴ Nms/rad, small nonzero damping assumption
- **Rotor inertia (J):** 1 × 10⁻⁵ kg·m², within typical motor rotor inertia range
- **Efficiency (η):** 0.8, assumed to account for losses to friction, heat, and sound
- **Gearbox ratio (Y:Z):** 20:50

## Control Architecture

- Independent **PID controllers** for the Y-axis and Z-axis feedback loops
- **Encoder-based** position feedback for both axes
- Reference, estimated, and actual position tracked and compared via Simulink scopes
- Z-axis loop includes an added gravity constant to compensate for vertical lift

## Results

Step-response and tracking-response simulations were run for both axes, comparing reference input, position estimate, and actual measured position.

### Known Issue — Jerk Calculation

Triple differentiation of the Z-axis actual position (to compute jerk) caused a solver error — the nonlinear iteration failed to converge even at the minimum step size. The jerk-calculation subsystem was disconnected, and its effect was instead accounted for directly within the feedback loop tuning rather than computed explicitly.

## Tools

- MATLAB / Simulink

## Reference

[1] S. Morris, *"Electromechanical System Modelling,"* 5CCE2MCT Lecture 2, King's College London.

Coursework project — BEng Electronic Engineering, King's College London (5CCE2MCT Mechatronics).
## Files
- `twoaxis_camera_gantry_start_work_project_Yejesh_final` — completed Simulink model
