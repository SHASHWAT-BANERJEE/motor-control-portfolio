# Closed-Loop FOC of a PMSM and an Induction Motor (Simulink, MIL)

All three projects are Simulink simulations: the controller and the motor model both run in simulation (model-in-the-loop). No hardware was used for this project.

Common structure: Clarke-Park transforms, decoupled PI current loops (d and q axes), an outer PI speed loop, and a three-phase inverter model.

Values below marked "about" are read from the scope plots.

## 1. PMSM, 19.8 kW, 1700 rpm, SPWM

![PMSM rating](images/pmsm_01_machine_rating.png)

*PMSM rating: 19.8 kW, 1700 rpm (rated torque about 111 Nm).*

![PMSM FOC model](images/pmsm_02_foc_spwm_model.png)

*Simulink model of the PMSM FOC with an SPWM inverter.*

![PMSM speed and torque response](images/pmsm_03_speed_torque_response.png)

*Speed and torque response: reference steps (0 to 1500 rpm, then 1500 to 500 rpm), load steps of +33 Nm and then -33 Nm.*

![PMSM current response](images/pmsm_04_current_response.png)

*Current response.*

| Test | Result |
|---|---|
| Speed reference step 0 to 1500 rpm | Fast rise, about 20% overshoot (peak about 1800 rpm), settles within about 0.2 s |
| Load step of 33 Nm (about 30% of rated) | Speed dips by about 8%, recovers within a few tenths of a second |
| Load reversal to -33 Nm | Electrical torque follows, so the drive tracks regenerative operation |
| Reference step down to 500 rpm | Brief undershoot, then settles at the reference |

## 2. Induction motor, 1 kW, 2880 rpm rated, SPWM

![Induction motor rating](images/im_spwm_01_machine_rating.png)

*Induction motor rating and parameters: 1 kW, 380 V, 50 Hz, 2 poles, 2880 rpm rated (rated torque about 3.3 Nm; synchronous speed 3000 rpm).*

![Induction FOC model, SPWM](images/im_spwm_02_foc_model.png)

*Simulink model of the induction motor FOC with an SPWM inverter.*

![Induction speed and torque, SPWM](images/im_spwm_03_speed_torque_response.png)

*Speed and torque response with SPWM: a 0 to 3000 rpm reference step, a 1.45 Nm load from 4 s to 9 s, and a reference step down to 2000 rpm at 6 s.*

| Test | Result |
|---|---|
| Speed reference step 0 to 3000 rpm | Torque-limited ramp (about 3 Nm), rise time about 1.5 s |
| Overshoot and steady-state error | None visible |
| Load step of 1.45 Nm (about 44% of rated) | No visible speed dip; torque rises to about 1.8 Nm |
| Reference step down to 2000 rpm | Electrical torque goes negative (about -0.6 Nm), so the drive brakes regeneratively, then settles |

## 3. Same induction motor, SVPWM

![Induction FOC model, SVPWM](images/im_svpwm_01_foc_model.png)

*Simulink model of the induction motor FOC with SVPWM.*

![SVPWM block](images/im_svpwm_02_svpwm_block.png)

*Inside the SVPWM block.*

![Induction speed and torque, SVPWM](images/im_svpwm_03_speed_torque_response.png)

*Speed and torque response with SVPWM, same test sequence.*

Observation: the speed reaches 3000 rpm after about 1.4 s of ramping, but with a sustained oscillation of about ±50 rpm, and the electrical torque oscillates at roughly 3 to 4 Hz. [Write the current status here, for example "controller gains are being retuned", or delete this section.]

Contact: [LinkedIn](https://www.linkedin.com/in/shashwat-banerjee-7a7b43197) | shashwatbanerjee96iitd@gmail.com
