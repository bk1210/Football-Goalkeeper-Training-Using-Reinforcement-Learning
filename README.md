# 🥅 Football Goalkeeper Training Using Reinforcement Learning

## Overview

An interactive 2D football simulation where an AI-powered goalkeeper learns to make saves through **Reinforcement Learning (PPO)**. Built with **Pygame** and **PyTorch**, the simulation lets a human-controlled attacker dribble and shoot while the goalkeeper agent trains itself to predict trajectories, assess threats, and dive — improving with every game played. This project bridges game development, physics simulation, and machine learning research.

---

## ✨ Key Features

- **Rule-Based Baseline AI** — Geometric threat estimation, shot direction prediction, and confidence-based diving logic
- **Reinforcement Learning (PPO)** — Goalkeeper trains via reward/penalty feedback using PyTorch's actor-critic model
- **State Machine Behavior** — `IDLE → TRACKING → READY → DIVING → RECOVERING` for realistic goalkeeper motion
- **Rich Visuals** — Grass textures, goal nets, ball trails, confidence meters, and predicted path overlays
- **Performance Metrics** — Tracks saves, goals, confidence scores, and threat levels in real-time

---

## 🛠️ Technologies Used

| Category       | Tools/Libraries                    |
|----------------|------------------------------------|
| Language       | Python 3.x                         |
| Simulation     | Pygame                             |
| Deep Learning  | PyTorch                            |
| Math & Physics | NumPy, `math`, `random`            |
| RL Algorithm   | Proximal Policy Optimization (PPO) |

---

## ⚙️ Installation

```bash
# 1. Clone the repository
git clone https://github.com/your-username/goalkeeper-rl.git
cd goalkeeper-rl

# 2. Create a virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install pygame torch numpy

# 4. Run the simulation
python main.py
```

---

## 🎮 Usage

- **Arrow Keys / WASD** — Move the attacker
- **Spacebar** — Shoot the ball
- **Watch** the AI goalkeeper react, dive, and learn from every attempt!

> Train mode runs PPO episodes automatically and logs save accuracy over time.

---

## 🤝 Contributing

Contributions are welcome! To get started:

1. Fork the repo and create a new branch: `git checkout -b feature/your-feature`
2. Commit your changes with clear messages
3. Open a Pull Request describing what you've added or fixed

Please follow [PEP 8](https://pep8.org/) style guidelines and include comments for any RL logic changes.

---

## 📄 License

MIT License — free to use, modify, and distribute.


---

## 👤 Contact

**Your Name**
- 📧 Email: bharathkesav1275@gmail.com
- 🐙 GitHub: [@bk1210](https://github.com/bk1210)
- 🎓 Institution:Amrita Vishwa Vidyapeetham

---

## 🙏 Acknowledgements

- [Groq](https://groq.com) — for providing free, ultra-fast LLM inference
- [Meta AI](https://ai.meta.com/llama/) — for the open-source LLaMA 3.3-70B model
- [Streamlit](https://streamlit.io) — for making Python web apps effortless

---

<div align="center">

**⭐ If you found this project useful, please give it a star on GitHub! ⭐**

*Built with ❤️ for college students everywhere*

</div>
