# Two-Axis Camera Gantry System

**Module:** Mechatronics (5CCE2MCT) — King's College London  
**Year:** Second Year BEng Electronic Engineering  
**Tool:** MATLAB / Simulink

## Overview
Designed and simulated an electromechanical actuation system for a two-axis camera gantry 
used in cinematic production. The gantry moves a camera both horizontally and vertically 
using geared DC motors driving leadscrew runners.

## What I Built
- **DC motor model** — modelled the electromechanical behaviour of two geared DC motors
- **Gearbox and motor specification** — selected motor and gearbox parameters to meet 
  payload and speed requirements (10–20 kg camera, 0.75 × 0.4 m travel area)
- **PID controllers with state estimation** — implemented independent feedback controllers 
  for each axis, converting rotational encoder readings to linear position
- **Performance testing** — evaluated system against step response and tracking response 
  requirements (rise time, settling time, overshoot, steady-state error)

## Requirements Met
- Battery: 7.4V (2S Li-Ion), within 5–12V spec
- DC motor within stall current, torque, and speed requirements
- Step response and tracking response simulations completed

## Files
- `twoaxis_camera_gantry_start_work_project_Yejesh_final` — completed Simulink model
