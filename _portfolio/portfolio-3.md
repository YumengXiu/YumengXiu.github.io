---
title: Voltage Control based on ISS Neural Certificates
excerpt: "We Developed methods for stabilizing large scale power systems based on Input-to-State Stability (ISS) Lyapunov-based neural certificate, by treating a large system as an interconnection of smaller subsystems. Each ISS Lyapunov function of subsystem could be collected to prove the global stability of power system. <br/><img src='/images/power_flow.png'>"
collection: portfolio
---

We Developed methods for stabilizing large scale power systems based on Input-to-State Stability (ISS) Lyapunov-based neural certificate, by treating a large system as an interconnection of smaller subsystems. Each ISS Lyapunov function of subsystem could be collected to prove the global stability of power system.


We demonstrate <strong>NeuralISS</strong> using three examples - Power systems, Platoon, and Drone formation control, and show that <strong>NeuralISS</strong> can find certifiably stable controllers for networks of size up to 100 subsystems. Compared with centralized neural certificate approaches, <strong>NeuralISS</strong> reaches similar results in small-scale systems, and can generalize to large scale systems that centralized approaches cannot scale up to. Compared with LQR, <strong>NeuralISS</strong> can deal with strong coupled networked systems like the microgrids, and reaches smaller tracking errors on both small and large scale systems. Compared with RL (PPO, LYPPO, MAPPO), our algorithm achieves similar or smaller tracking errors in small systems, and can hugely reduce the tracking errors in large systems (up to 75%). 

In our experiments, we consider a power distribution system that consists of 8 buses. The buses are arranged in a line, each one is connected to a static generator. The nominal controller is similar to the droop control and is a proportion controller on the voltage deviation, u_i(t) = c_i(v_i(t)-1) (where c_i is a constant). This proportion controller is a standard controller used in practice.

See the related [Paper](https://arxiv.org/pdf/2303.14564.pdf) if you are interested.

<div align="center">
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img src="../../images/GridVoltage8.png" title="example image" class="img-fluid rounded z-depth-1" width=500 height=300>
    </div>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
    The example of 8 bus GridVoltage.
    </div>
</div>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img src="../../images/eval_voltatges.png" title="example image" class="img-fluid rounded z-depth-1" width=200 height=100>
        <img src="../../images/ref_voltages.png" title="example image" class="img-fluid rounded z-depth-1" width=200 height=100>
        <img src="../../images/lyapunov_GridVoltage8.png" title="example image" class="img-fluid rounded z-depth-1" width=200 height=100>
    </div>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
    To control the bus voltage to 1kv. Left is the performance of Neural Controller. Middle, we take a simple practical Propotional controller for reference. Right is the figure of lyapunov values.
    </div>
</div>


We compare NeurISS with both centralized and decentralized baselines. For centralized ones, we compare with the state-of-the-art RL algorithm PPO, the RL-with-Lyapunov-critic algorithm LYPPO, and the centralized Neural CLF controller (NCLF). For decentralized ones, we compare with the classical LQR controller and the multi-agent RL algorithm MAPPO. We hand-craft reward functions based on the common way of designing reward functions of tracking problems for the RL algorithms. For LQR, since the agents only have local observation, we calculate the goal point for the LQR controller based on local observations in each time step.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img src="../../images/NeuralISS_rewards.png" title="example image" class="img-fluid rounded z-depth-1">
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
    Experiment Results of NeuralISS
    </div>
</div>
