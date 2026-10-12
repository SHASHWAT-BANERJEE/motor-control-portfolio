# M.Tech Thesis: Design and Control of Magnetically Levitated Spherical Motors for Space Applications

Guide: Prof. Krishan Kant Bhalla, IIT Delhi | Demo video: https://lnkd.in/p/dVbiqRVr

## 1. Design overview
Spherical rotor with 6 maglev poles (bearingless along all three global axes) and 4 sets of three-phase hysteresis motor windings, each rotating the rotor about its local axis.

![ANSYS assembly](images/00_ansys_final_maglev_hysteresis_assembly.png.png)

*Final maglev and hysteresis motor assembly in ANSYS: 6 maglev poles, 4 hysteresis stator sets and the maglev body, showing the space optimization.*

## 2. B-H characterization of the rotor material (S52100 bearing steel)
![B-H tracer lab rig](images/01_bh_tracer_lab_rig.jpeg)

*Laboratory rig used to measure the B-H loop.*

![B-H loop on the DSO](images/02_bh_loop_dso_s52100.jpg)

*B-H loop of S52100 traced on the DSO. This data was used for the rotor material properties in ANSYS Maxwell 3D.*

## 3. FEA: maglev (ANSYS Maxwell 3D)
![Maglev cross section](images/03_maglev_pole_rotor_cross_section.jpg)

*Maglev structure: cross section of the maglev poles and rotor along one axis.*

![Vertical maglev model](images/04_ansys_vertical_maglev_setup.png)

*ANSYS model of the vertical maglev setup.*

![Force versus current](images/05_force_vs_current.png)

*Force versus circuit current.*

![Force versus displacement](images/06_force_vs_displacement.png)

*Force versus rotor displacement.*

## 4. FEA: hysteresis motor
![Hysteresis stator and rotor](images/07_hysteresis_stator_rotor_one_axis.png.jpg)

*Hysteresis motor stator and rotor along one axis.*

![ANSYS speed plot](images/08_ansys_speed_plot.png)

*Speed plot from ANSYS Maxwell.*

![ANSYS torque plot](images/09_ansys_torque_plot.png)

*Torque plot from ANSYS Maxwell.*

## 5. MIL simulation: maglev control
Parameters extracted from ANSYS were used in the Simulink model. Dual-loop controller: outer position loop, inner current loop.

![Maglev dual-loop model](images/10_maglev_dual_loop_simulink.png)

*Dual-loop maglev controller in Simulink.*

![Position response](images/11_maglev_position_response_mil.png)

*Position response (MIL).*

![Current response](images/12_maglev_current_response_mil.png)

*Current response (MIL).*

## 6. MIL simulation: hysteresis motor
![Bang-Bang controller model](images/13_hysteresis_bang_bang_simulink.png)

*Dual-loop Bang-Bang controller for the hysteresis motor in Simulink.*

![Hysteresis speed response](images/15_hysteresis_speed_response_mil.png)

*Speed response of the hysteresis motor with Bang-Bang control (MIL).*

## 7. Hardware and rapid control prototyping (vertical maglev)
![Pole machining](images/16_pole_machining_lathe.jpeg)

*Machining of the maglev poles on a lathe (turning and drilling).*

![Wound poles and rotor](images/17_wound_poles_and_rotor.jpg)

*Close-up of the wound maglev poles and rotor.*

![Circuit diagram](images/18_maglev_circuit_diagram.png)

*Circuit diagram of the maglev operation.*

![Final hardware setup](images/19_vertical_maglev_final_setup.png)

*Final hardware setup of the vertical maglev stabilization.*

![ADC interrupt synchronization](images/20_simulink_c2000_blockset_model_A.png)

*ADC-interrupt synchronization: the C28x Interrupt block (IRQ1) triggers the ADC-PWM function-call subsystem, so the control loop runs synchronized with ADC conversion.*

![ADC-PWM subsystem](images/20_simulink_c2000_blockset_model_B.png)

*Inside the ADC-PWM subsystem: position sensors via ADC feed the position controller, whose output is the reference for the PI current controller; the controller output sets the ePWM duty cycles.*

![Hardware current step response](images/21_current_step_response_hardware.jpg)

*Current response to a step change on hardware (DSO).*

## What ran where
| Part | Stage |
|---|---|
| Maxwell 3D design and B-H calibration | FEA simulation and bench measurement |
| Maglev controller | MIL, then code generation and RCP on hardware |
| Hysteresis motor Bang-Bang controller | MIL (simulation only) |

LinkedIn posts: [Maglev control](https://lnkd.in/p/gzrSWghU) | [Maxwell and B-H](https://lnkd.in/p/gDMaKcW5)
