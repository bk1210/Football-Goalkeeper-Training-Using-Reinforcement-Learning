# 🥅 Football Goalkeeper Training — Reinforcement Learning with Pygame

<div align="center">

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-orange?style=for-the-badge&logo=pytorch)
![Pygame](https://img.shields.io/badge/Pygame-2.x-green?style=for-the-badge)
![RL](https://img.shields.io/badge/PPO-Reinforcement_Learning-red?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**An interactive 2D football simulation where an AI goalkeeper learns to make saves through Reinforcement Learning (PPO) — combining game physics, state machine behavior, and deep learning in a single playable environment.**

[Features](#-features) • [How It Works](#-how-it-works) • [Installation](#-installation) • [Usage](#-usage) • [Architecture](#-architecture) • [Tech Stack](#-tech-stack) • [Contact](#-contact)

</div>

---

## 📌 Overview

**Football Goalkeeper Training** is a Pygame-based 2D simulation where a human-controlled attacker dribbles and shoots while an AI goalkeeper agent learns to predict trajectories, assess threats, and dive — improving with every attempt through Proximal Policy Optimization (PPO).

The system combines three layers:
- 🧠 **Rule-Based Baseline** — Geometric threat estimation, shot direction prediction, and confidence-based diving logic before RL kicks in
- 🤖 **PPO Reinforcement Learning** — Actor-critic model trained via reward/penalty feedback using PyTorch
- 🎮 **State Machine Goalkeeper** — `IDLE → TRACKING → READY → DIVING → RECOVERING` for physically realistic behavior

---

## ✨ Features

### 🧠 AI Goalkeeper Logic
- **Optimal positioning** — Bisector-based angle calculation between both posts relative to ball/attacker position
- **Shot prediction** — Estimates future ball trajectory and calculates predicted impact point on goal line
- **Threat assessment** — Dynamic threat level (0–1) based on distance, ball speed, and angle of approach
- **Confidence-gated diving** — Dives only when confidence > 0.6 and threat level > 0.8
- **State machine** — 5-state FSM: IDLE → TRACKING → READY → DIVING → RECOVERING

### 🤖 Reinforcement Learning (PPO)
- PyTorch actor-critic network trained on goalkeeper state observations
- Reward for saves, penalty for goals conceded
- Trains continuously across episodes — save accuracy improves over time

### 🎮 Simulation Environment
- 1200×800 pixel pitch with grass stripes, penalty area, six-yard box
- Realistic ball physics — friction (0.97), kick power, trajectory simulation
- Goal net detection — checks ball crossing the goal line
- Ball trails, confidence meters, threat level overlays, predicted path visualization

### 📊 Real-Time Metrics
- Save count and goals conceded
- Confidence score per shot attempt
- Threat level indicator
- Predicted shot path overlay

---

## 🖥️ Demo

![Demo](demo.mp4)
### Controls
```
WASD / Arrow Keys  → Move attacker
SPACE              → Shoot (aims toward mouse cursor)
R                  → Reset ball to attacker
Mouse              → Aim direction
```

---

## 🚀 Installation

### Prerequisites
- Python 3.x
- No GPU required

### Step 1 — Clone the Repository
```bash
git clone https://github.com/bk1210/goalkeeper-rl.git
cd goalkeeper-rl
```

### Step 2 — Install Dependencies
```bash
pip install pygame torch numpy
```

### Step 3 — Run the Simulation
```bash
python goalkeeper_training.py
```

Or open and run `goalkeeper_training.ipynb` directly in Jupyter.

---

## 📖 Usage

### Playing the Simulation
1. Use `WASD` or arrow keys to move your attacker toward the goal
2. Aim with your **mouse cursor**
3. Press **SPACE** to shoot
4. Watch the AI goalkeeper track, assess threat, and dive
5. Press **R** to reset the ball

### Training Mode
PPO training runs automatically in the background — the goalkeeper logs save accuracy over episodes and improves its diving decisions over time.

---

## 🏗️ Architecture

### System Design

```
Human Input (WASD + SPACE)
    │
    ▼
Attacker Entity
[Position, velocity, kick direction]
    │
    ▼
Ball Physics
[dx, dy, friction=0.97, kick power=12]
    │
    ▼
Goalkeeper AI
    │
    ├──► Threat Assessment
    │    [distance + angle width + ball speed → threat_level ∈ [0,1]]
    │
    ├──► Shot Prediction
    │    [future ball trajectory → predicted impact_y on goal line]
    │    [confidence = ball_speed / 10, clipped to [0,1]]
    │
    ├──► State Machine
    │    IDLE → TRACKING (threat>0.4)
    │         → READY    (threat>0.8)
    │         → DIVING   (confidence>0.6 AND threat>0.8)
    │         → RECOVERING
    │
    └──► PPO Agent (PyTorch)
         [Actor-Critic | Reward: save +1 | Penalty: goal -1]
    │
    ▼
Pygame Renderer
[Pitch, goal net, ball trail, confidence meter, predicted path overlay]
```
## 🔄 Pipeline

![Pipeline](pipeline.png)
### Key Classes

| Class | Responsibility |
|---|---|
| `Pitch` | Renders grass stripes, lines, penalty box, six-yard box, corner flags |
| `Goal` | Draws posts, crossbar, net — detects ball crossing goal line |
| `Goalkeeper` | AI positioning, threat assessment, shot prediction, state machine, PPO |
| `GoalkeeperState` | FSM enum: IDLE, TRACKING, READY, DIVING, RECOVERING |
| `DiveDirection` | Enum: NONE, LEFT, RIGHT, DOWN |

### Project Structure

```
goalkeeper-rl/
│
├── goalkeeper_training.ipynb    # Full simulation + PPO training
├── requirements.txt             # Python dependencies
└── README.md                    # Project documentation
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python 3.x | Core language |
| Pygame | 2D simulation, rendering, input handling |
| PyTorch | PPO actor-critic neural network |
| NumPy | Physics calculations, state vector construction |
| math / random | Trajectory geometry, randomisation |

---

## 📦 Dependencies

```txt
pygame>=2.0.0
torch>=2.0.0
numpy>=1.24.0
```

Install with:
```bash
pip install pygame torch numpy
```

---

## 🔮 Future Improvements

- [ ] Full PPO training loop with episode logging and save rate curves
- [ ] Multiple attacker positions and shot types (low, high, curved)
- [ ] Multiplayer mode — two human players
- [ ] Export trained goalkeeper model for standalone inference
- [ ] Add GK fatigue mechanics over extended sessions

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👤 Contact

**Bharath Kesav R**
- 📧 Email: bharathkesav1275@gmail.com
- 🐙 GitHub: [@bk1210](https://github.com/bk1210)
- 🎓 Institution: Amrita Vishwa Vidyapeetham, Coimbatore

---

<div align="center">

**⭐ If you found this project useful, please give it a star on GitHub! ⭐**

*Built with ⚽ and ❤️ for football and AI*

</div>
