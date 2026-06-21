# On the Use of AI-Driven Immersive Digital Technologies for Designing and Operating UAVs

This repository contains the code and resources for the paper **"On the Use of AI-Driven Immersive Digital Technologies for Designing and Operating UAVs"** by Yousef Emami, Mohammadhossein Homaei, Miguel Gutiérrez Gaitán, Kai Li, and Sai Zou.

## Abstract
Uncrewed Aerial Vehicles (UAVs) offer agile, cost-effective and efficient solutions for communication relay networks. However, their modeling and control are challenging, and the mismatch between simulations and actual conditions limits real-world deployment, while maintaining adequate situational awareness remains essential for safe operation. Several studies have proposed integrating the operation of UAVs with immersive digital technologies such as Digital Twin (DT) and Extended Reality (XR) to overcome these challenges. This paper provides a comprehensive overview of the latest research and developments involving immersive digital technologies for UAVs. We explore the use of Machine Learning (ML) techniques, particularly Deep Reinforcement Learning (DRL), to improve the capabilities of DT for UAV systems, and present a case study of a DT-driven DRL pipeline that couples bidirectional physical-digital synchronisation with online recursive least-squares channel calibration for UAV resource allocation.

## Digital Twin-Driven DQN for UAV-Assisted IoT Data Collection

In this project, a UAV flies a circular path and collects data from 10 ground sensors.  
**Goal:** Keep the Age of Information (AoI) — representing how stale the data is — low across all sensors.

**The Key Idea:** We maintain a Digital Twin of the UAV and its environment that stays in sync with the real UAV. The Deep Q-Network (DQN) trains inside this twin, and the twin continuously corrects its own parameters from real measurements to bridge the simulation-to-reality gap.

### Key Components
- **`PhysicalUAVStub`**: A stand-in for the real UAV (simulates GPS noise and channel fading).
- **`DigitalTwin`**: The virtual replica that syncs with the physical UAV.
  - **`KalmanFilter1D`**: Fuses noisy position and path-loss readings.
  - **`DTCalibrator`**: Estimates path-loss exponent online using Recursive Least Squares (RLS).
  - **`FaultDetector`**: Catches anomalies in telemetry such as GPS spoofing or False Data Injection (FDI) attacks.
- **`MultiHeadDQN`**: Neural network with two action heads: picking the sensor to serve and picking the flight speed.
- **`Agent`**: DQN agent with an epsilon-greedy policy and a target network.
- **`RealEnv`**: A skeleton environment to plug in real hardware later.

### Training and Deployment Flow
- **Phase 1**: The agent trains entirely inside the digital twin.
- **Phase 2**: Meanwhile, the twin calibrates itself from physical telemetry.
- **Phase 3**: The trained policy runs on the physical UAV stub.
- **Phase 4**: The twin continues calibrating as the UAV flies, adapting to dynamic changes.

## Code Structure
- `digital_twin_driven_dqn.py`: Implementation of the DT-driven DQN model for UAV resource allocation.

## Results
The following figure illustrates the results of the Digital Twin Driven DQN model:

![DT DQN Results](dt_dqn_results.png)

## Citation
If you find this code or research helpful, please cite our paper using the following BibTeX format:

```bibtex
@article{emami2026aidriven,
  title={On the Use of AI-Driven Immersive Digital Technologies for Designing and Operating UAVs},
  author={Emami, Yousef and Homaei, Mohammadhossein and Gait{\'a}n, Miguel Guti{\'e}rrez and Li, Kai and Zou, Sai},
  journal={IEEE Transactions},
  year={2026}
}
```
