# Closed-Loop FOC of a PMSM and an Induction Motor (Simulink, MIL)

All three projects are Simulink simulations, with the controller and the motor model both running in simulation (model-in-the-loop). No hardware was used.

Common structure: Clarke-Park transforms, decoupled PI current loops (d and q axes), an outer PI speed loop, and an inverter model.

## 1. PMSM, 19.8 kW, 1700 rpm, SPWM

![PMSM rating](images/pmsm_01_machine_rating.png)

*PMSM rating (19.8 kW, 1700 rpm).*

![PMSM FOC model](images/pmsm_02_foc_spwm_model.png)

*Simulink model of the PMSM FOC with an SPWM inverter.*

![PMSM speed and torque](images/pmsm_03_speed_torque_response.png)

*Speed and torque response, including a load step.*

![PMSM current](images/pmsm_04_current_response.png)

*Current response.*

Results: reference [value] rpm reached in [value] ms; load step of [value] Nm gives a speed dip of [value] % and recovery in [value] s; the drive tracks motoring and regenerative torque.

## 2. Induction motor, 2 HP, 3000 rpm, SPWM

![Induction motor rating](images/im_spwm_01_machine_rating.png)

*Induction motor rating (2 HP, 3000 rpm).*

![Induction FOC model, SPWM](images/im_spwm_02_foc_model.png)

*Simulink model of the induction motor FOC with an SPWM inverter.*

![Induction speed and torque, SPWM](images/im_spwm_03_speed_torque_response.png)

*Speed and torque response with SPWM, including a load step.*

Results: about 1.5 s rise time for a 0 to 3000 rpm reference step (torque-limited ramp); overshoot [value]; steady-state error [value]; load step of [value] Nm with a speed dip of [value].

## 3. Same induction motor, SVPWM

![Induction FOC model, SVPWM](images/im_svpwm_01_foc_model.png)

*Simulink model of the induction motor FOC with SVPWM.*

![SVPWM block](images/im_svpwm_02_svpwm_block.png)

*Inside the SVPWM block.*

![Induction speed and torque, SVPWM](images/im_svpwm_03_speed_torque_response.png)

*Speed and torque response with SVPWM.*

Observed difference from the SPWM version: [write what you saw, or delete this line].

Contact: [LinkedIn](https://www.linkedin.com/in/shashwat-banerjee-7a7b43197) | shashwatbanerjee96iitd@gmail.com
