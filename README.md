# 🤖 Unity ML-Agents: Reinforcement Learning & AI Training Guide

Unity • ML-Agents • Reinforcement Learning • AI Training • PPO • Python • CUDA • cuDNN

# 📌 Project Overview

This project demonstrates the complete workflow of training AI agents in Unity using the Unity ML-Agents Toolkit.

The implementation focuses on understanding:
- Reinforcement Learning (RL)
- Imitation Learning (IL)
- Heuristic-Based Agents
- PPO Training Pipeline
- Randomized Environment Training
- AI Observation & Decision Systems
- ML-Agents Configuration & Optimization

The project was built to deeply understand how intelligent agents observe environments, make decisions, receive rewards, and continuously improve using machine learning.

# 🧠 Introduction to ML-Agents

ML-Agents (Machine Learning Agents) is a Unity toolkit that allows developers to train intelligent agents using Reinforcement Learning (RL), Imitation Learning (IL), and Heuristic Methods.

# 🎯 ML-Agents Learning Methods

1. Reinforcement Learning (RL)

How It Works:
The agent interacts with the environment and learns using rewards and penalties. Positive rewards for good behavior, negative rewards for bad behavior. Over time, the agent improves by maximizing cumulative rewards.

Training Algorithm:
PPO (Proximal Policy Optimization)

Example:
A self-driving car learns to stay on the road by receiving rewards for staying on track and penalties for going off-road.

ML-Agents Setup:
Behavior Type: Default

Training Command:
mlagents-learn config.yaml --run-id=MyTraining --no-graphics


2. Imitation Learning (IL)

How It Works:
The agent learns by copying expert demonstrations instead of trial and error using Behavioral Cloning (BC) or GAIL.

Example:
A robotic arm learns object pickup by imitating human actions.

ML-Agents Setup:
Behavior Type (Recording): Player
Behavior Type (Training): Default


3. Heuristic Methods

How It Works:
The agent follows manually written rules instead of learning.

Example:
NPC patrol movement using fixed paths.

Example Script:
public override void Heuristic(in ActionBuffers actionsOut)
{
    var continuousActions = actionsOut.ContinuousActions;
    continuousActions[0] = Input.GetAxis("Horizontal");
    continuousActions[1] = Input.GetAxis("Vertical");
}

Used for debugging and testing only.

# ⚙️ Installation & Setup

Required Versions:
Python 3.8.10
ML-Agents 0.29.0
CUDA 11.8.0
cuDNN 8.9.7

Virtual Environment:
python -m venv venv
venv\Scripts\activate (Windows)
source venv/bin/activate (Mac/Linux)

Install ML-Agents:
pip install mlagents==0.29.0

Verify:
mlagents-learn --help

# 🚀 CUDA & cuDNN Setup

CUDA Path:
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vXX.X

Verify:
nvcc --version
python -c "import torch; print(torch.cuda.is_available())"

# 🧩 Unity Behavior Types

Default → Training + inference
Inference Only → Uses trained model
Heuristic Only → Manual logic
Player → Human control

# 🎮 Training Commands

Start Training:
mlagents-learn config.yaml --run-id=MoveToGoal --no-graphics

Resume Training:
mlagents-learn config.yaml --run-id=MoveToGoal --resume --no-graphics

Force Training:
mlagents-learn config.yaml --run-id=MoveToGoal --force --no-graphics

Initialize From Model:
mlagents-learn config.yaml --initialize-from=MoveToGoal2

# 🧠 Custom Agent System

Agent handles:
- Observations
- Actions
- Rewards
- Episode resets

CollectObservations() → Reads environment
OnActionReceived() → Executes actions
SetReward() → Assigns rewards
OnEpisodeBegin() → Resets environment

# ⚡ Key Issue & Fix

Problem:
Agent learned fixed paths and failed when target moved.

Solution:
Randomized both agent and target spawn positions every episode.

This improved:
- Generalization
- Path diversity
- Learning stability

# 🧠 Training Lifecycle

1. Observation
2. Decision Making
3. Action Execution
4. Reward Assignment
5. Model Update

# 🔄 RL vs IL

RL → Learns via rewards
IL → Learns via expert data

# 🚀 Deploy Model

1. Train model
2. Get .onnx file
3. Assign in Unity
4. Set Behavior Type → Inference Only

# ⚡ Optimization Tips

- Increase training time
- Improve reward shaping
- Use curriculum learning
- Save checkpoints

# 📈 Results

- Stable AI navigation
- Adaptive learning behavior
- Improved generalization with randomization

# 🔗 Links

GitHub:
https://github.com/NikhilChaudhary285/MLAgents-Demo

ML-Agents Setup:
https://drive.google.com/file/d/1VhoXz61Y6u3euByQUN9HaaH7WFDTHBSy/view?usp=sharing

⭐ Feel free to explore this repository and connect with me. I’m always open to discussions around Unity AI, ML-Agents, reinforcement learning, and scalable game architecture.
