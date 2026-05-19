[README (3).md](https://github.com/user-attachments/files/27989980/README.3.md)
# 🟡 Logistics RL Agent with Memory


## Overview

This project implements a **Q-Learning reinforcement learning agent** that navigates a simulated logistics grid, autonomously making inventory and delivery decisions. It serves as the **baseline agent-based model (ABM)** for an internship research project focused on integrating Large Language Models (LLMs) into supply chain management workflows.

---

## What the Agent Does

- Starts at a **depot** (🏭) every episode
- Navigates a **10×10 logistics grid** with obstacles and customer nodes
- Delivers goods to **10 customer locations** (📦)
- Learns from a **reward/punishment system** across 80 episodes
- Stores experience in an **episode memory** and improves over time
- **Stops automatically** the moment all deliveries are complete

---

## Reward System

| Event | Points |
|---|---|
| Successful delivery to customer | +15 |
| All deliveries complete (bonus) | +30 |
| Exploring a new cell | +2 |
| Hitting an obstacle | −5 |
| Stepping out of grid boundary | −3 |
| Each step taken (time cost) | −0.5 |

---

## Results

Training over **80 episodes** with Q-Learning (α=0.15, γ=0.92):

| Metric | First 10 Episodes | Last 10 Episodes |
|---|---|---|
| Avg Total Reward | −19.95 | +177.85 |
| Avg Deliveries | 2.2 / 10 | 8.1 / 10 |
| Avg Efficiency (deliveries/steps) | 0.027 | 0.101 |
| Best Episode Reward | — | **222.50** |

The agent converges from **random exploration** to a **structured delivery strategy**, demonstrating measurable learning over episodes.

---

## Project Structure

```
├── notebooks/
│   └── logistics_rl_agent_EN.ipynb   # Main simulation notebook (run in Colab)
├── results/
│   └── agent_evaluation.png          # Full evaluation dashboard (auto-generated)
└── README.md
```

---

## How to Run

1. Open `notebooks/logistics_rl_agent_EN.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Run all cells top to bottom (**Runtime → Run all**)
3. Watch the agent move step-by-step in real time
4. Review KPI results and evaluation charts at the end

No local setup required — everything runs in Colab.

---

## Agent Architecture

The agent follows a **perception → decision → action → memory** loop aligned with autonomous agent design principles:

- **Perception:** observes current position, visited cells, remaining customers
- **Reasoning:** epsilon-greedy Q-value lookup (exploration vs exploitation)
- **Memory:** records every episode's reward, steps, deliveries, and dangerous zones
- **Execution:** moves on the grid, updates Q-table via Bellman equation

## Internship Context

This notebook covers **Week 1–2** of the internship work plan:

- ✅ Literature concepts implemented: perception, memory, execution loop
- ✅ Baseline ABM simulation established
- ✅ KPI metrics defined and measured (reward, deliveries, efficiency)
- ✅ Comparative analysis: untrained vs trained agent performance
- 🔲 Next step: extend with LLM-based reasoning layer (Chain-of-Thought / InteraSSort framework)

---
