# Robust Deep Reinforcement Learning for Chaotic Plasma Control Proxies

This project implements a Deep Reinforcement Learning (DRL) control system designed to handle severe sensor degradation, serving as a simplified proxy for magnetic plasma confinement in nuclear fusion tokamaks (inspired by DeepMind's 2022 breakthrough research). 

Using an inverted pendulum (CartPole) as a physical proxy system, this project introduces a custom observation wrapper that injects Gaussian sensor noise to simulate extreme reactor conditions. It compares a baseline Proximal Policy Optimization (PPO) agent against a robustly trained agent to demonstrate the power of domain randomization in safety-critical control tasks.

---

## 🚀 Project Overview

In a real tokamak fusion reactor, magnetic coils must adjust dynamically to keep superheated plasma confined. However, physical sensors facing extreme heat and radiation produce heavily distorted, noisy telemetry. Standard AI controllers often fail when exposed to this real-world noise.

This repository demonstrates that:
1. **Standard AI Controllers Fail Under Stress:** An RL agent trained in a perfect simulation environment collapses when sensors become noisy.
2. **Noise Injection Creates Resilience:** An RL agent trained *inside* simulated chaos adapts to ignore sensor fluctuations and maintains system stability.

---

## 🛠️ Tech Stack & Tools

* **Framework:** Google Colab / Python 3
* **Simulation Environment:** [Gymnasium](https://gymnasium.farama.org/) (formerly OpenAI Gym)
* **RL Algorithms:** [Stable-Baselines3](https://stable-baselines3.readthedocs.io/) (Proximal Policy Optimization - PPO)
* **Data Visualization:** Matplotlib / NumPy

---

## 📊 Repository Structure

The experiment is broken down into discrete phases:
* **Sensor Noise Wrapper:** A custom Python class (`NoisyObservationWrapper`) that intercept environment readings and adds random Gaussian noise.
* **Baseline Training:** Training a standard PPO agent in a perfect environment.
* **Robust Training:** Training a PPO agent in the noisy environment.
* **Evaluation & Stress Testing:** Evaluating both models across a sliding scale of noise levels (from 0.0 to 0.5 standard deviation).

---

## 📈 Results & Visuals

The final evaluation demonstrates a stark contrast between the two control strategies:

* **Standard Agent on Clean Env:** Achieves the optimal score of `500.0` time steps.
* **Standard Agent on Noisy Env:** Performance drops severely as sensor noise increases, leading to catastrophic failure.
* **Robust Agent on Noisy Env:** Maintains stable control and near-optimal rewards even under high levels of sensor interference.

*(Tip: Drag and drop your saved Matplotlib graph image right here in your GitHub file to display your visual results!)*

---

## 💻 How to Run This Project

You can run this entire pipeline directly in Google Colab without any local setup.

1. Open a blank notebook in **Google Colab**.
2. Keep the runtime set to **CPU** (GPU is not required for this lightweight proxy environment).
3. Copy and run the cells sequentially to install dependencies, train the models, and output the final comparative graph.

### Core Installation Command:
```bash
pip install stable-baselines3 gymnasium
