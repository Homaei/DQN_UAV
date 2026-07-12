# On the Use of AI-Driven Immersive Digital Technologies for Designing and Operating UAVs

This repository contains the Python implementation of the Deep Reinforcement Learning (DRL) and Digital Twin (DT) framework presented in the paper **"On the Use of AI-Driven Immersive Digital Technologies for Designing and Operating UAVs"**.

## Authors
Yousef Emami, Mohammadhossein Homaei, Miguel Gutiérrez Gaitán, Kai Li, and Sai Zou.

## Overview
Uncrewed Aerial Vehicles (UAVs) are transformative for modern wireless and IoT networks. However, mitigating the simulation-to-reality gap remains a critical challenge. This repository implements a novel DT-driven DRL pipeline where a UAV Digital Twin continuously synchronizes with its physical counterpart, corrects its own internal models using recursive least-squares (RLS) estimation, and provides a highly accurate training environment for DRL agents.

The codebase includes two primary case studies discussed in the paper:
- **Case Study I**: DT-Driven DRL for UAV Resource Allocation. Joint UAV velocity control and sensor scheduling to minimize the Age of Information (AoI) in a UAV-assisted IoT data collection network.
- **Case Study II**: Evaluating the performance and convergence of online RLS calibration compared to miscalibrated and static prior configurations.

## Files in this Repository
- `DQN.py`: The complete Python implementation containing both Case Study I and Case Study II. It includes the physical UAV stubs, Digital Twin engine, Kalman filters, RLS calibrator, anomaly detector, and the DRL (DQN) agent. The code is heavily commented with simple human-readable English instructions.
- `Result1.png`: Training convergence and policy deployment results for Case Study I.
- `Result2.png`: Performance comparisons and distributions for Case Study II.

## Citation
If you find this code useful in your research, please consider citing our paper:

```bibtex
@article{emami2024immersive,
  title={On the Use of AI-Driven Immersive Digital Technologies for Designing and Operating UAVs},
  author={Emami, Yousef and Homaei, Mohammadhossein and Gait{\'a}n, Miguel Guti{\'e}rrez and Li, Kai and Zou, Sai},
  journal={IEEE},
  year={2024}
}
```
*(Note: Please update the citation with the exact journal, volume, and page numbers once published.)*

## Usage
The code is designed to be self-contained and run efficiently. You can execute the script directly to train the agents and reproduce the results for both case studies.

```bash
python DQN.py
```
