# Lunar Lander with Fuel Resource Management 🚀⛽

**Deep Q-Network (DQN) controlling a lunar lander that must land safely while conserving fuel**

Classic Lunar Lander is too easy when fuel is unlimited.
This project makes it realistic: **fuel is limited** ⛽, added directly into the observation space, and the reward function heavily punishes wasting it.

---
### What's Different & Cool ✨
* Custom `FuelWrapper` → turns standard 8D state into **9D** (adds remaining fuel).
* Dense + shaped rewards 📊:
    * → distance penalty, velocity penalty, angle penalty
    * → **+0.1 bonus every step** if fuel > 20% (incentivizes conservation)
    * → **-100 instant death** if fuel runs out mid-air
* Baseline: Vanilla DQN with experience replay
* Ready for Double DQN / Dueling DQN / Prioritized Replay in the future

---
### Environment Note 🛰️
* Using `LunarLander-v3` (v2 is deprecated as of 2025, v3 is 100% identical in physics, state, and actions).
* Observation: `Box(-inf, inf, (9,), float32)` → 8 physics vars + fuel
* Action: `Discrete(4)` → nothing / left / main / right engine

---
### Quick Demo 🧪
```bash
# Install
pip install "gymnasium[box2d]" torch matplotlib numpy

# Verify the 9D environment works
python test_env.py
