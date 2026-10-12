# M.Tech Thesis: Design and Control of Magnetically Levitated Spherical Motors for Space Applications

Guide: Prof. Krishan Kant Bhalla, IIT Delhi | Demo video: https://lnkd.in/p/dVbiqRVr

## 1. Design overview
Spherical rotor with 6 maglev poles (bearingless along all three global axes) and 4 sets of three-phase hysteresis motor windings, each rotating the rotor about its local axis.

![Final maglev and hysteresis motor assembly in ANSYS: 6 maglev poles, 4 hysteresis stator sets and the maglev body, showing the space optimization](images/00_ansys_final_maglev_hysteresis_assembly.png)

## 2. B-H characterization of the rotor material (S52100 bearing steel)
![Laboratory rig used to measure the B-H loop](images/01_bh_tracer_lab_rig.png)
![B-H loop of S52100 traced on the DSO. This data was used for the rotor material properties in ANSYS Maxwell 3D](images/02_bh_loop_dso_s52100.png)

## 3. FEA: maglev (ANSYS Maxwell 3D)
![Maglev structure: cross section of the maglev poles and rotor along one axis](images/03_maglev_pole_rotor_cross_section.png)
![ANSYS model of the vertical maglev setup](images/04_ansys_vertical_maglev_setup.png)
![Force versus circuit current](images/05_force_vs_current.png)
![Force versus rotor displacement](images/06_force_vs_displacement.png)

## 4. FEA: hysteresis motor
![Hysteresis motor stator and rotor along one axis](images/07_hysteresis_stator_rotor_one_axis.png)
![Speed plot from ANSYS Maxwell](images/08_ansys_speed_plot.png)
![Torque plot from ANSYS Maxwell](images/09_ansys_torque_plot.png)

## 5. MIL simulation: maglev control
Parameters extracted from ANSYS were used in the Simulink model. Dual-loop controller: outer position loop, inner current loop.

![Dual-loop maglev controller in Simulink](images/10_maglev_dual_loop_simulink.png)
![Position response (MIL)](images/11_maglev_position_response_mil.png)
![Current response (MIL)](images/12_maglev_current_response_mil.png)

## 6. MIL simulation: hysteresis motor
![Dual-loop Bang-Bang controller for the hysteresis motor in Simulink](images/13_hysteresis_bang_bang_simulink.png)
![Speed response of the hysteresis motor with Bang-Bang control (MIL)](images/15_hysteresis_speed_response_mil.png)

## 7. Hardware and rapid control prototyping (vertical maglev)
![Machining of the maglev poles on a lathe (turning and drilling)](images/16_pole_machining_lathe.png)
![Close-up of the wound maglev poles and rotor](images/17_wound_poles_and_rotor.png)
![Circuit diagram of the maglev operation](images/18_maglev_circuit_diagram.png)
![Final hardware setup of the vertical maglev stabilization](images/19_vertical_maglev_final_setup.png)
![ADC-interrupt synchronization: the C28x Interrupt block (IRQ1) triggers the ADC-PWM function-call subsystem, so the control loop runs synchronized with ADC conversion](images/20_simulink_c2000_blockset_model_A.png)
![Inside the ADC-PWM subsystem: position sensors via ADC feed the position controller, whose output is the reference for the PI current controller; the controller output sets the ePWM duty cycles](images/20_simulink_c2000_blockset_model_B.png)
![Current response to a step change on hardware](images/21_current_step_response_hardware.png)

## What ran where
| Part | Stage |
|---|---|
| Maxwell 3D design and B-H calibration | FEA simulation and bench measurement |
| Maglev controller | MIL, then code generation and RCP on hardware |
| Hysteresis motor Bang-Bang controller | MIL (simulation only) |

LinkedIn posts: [Maglev control](https://lnkd.in/p/gzrSWghU) | [Maxwell and B-H](https://lnkd.in/p/gDMaKcW5)
