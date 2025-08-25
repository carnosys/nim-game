# Nim Game AI (Q-Learning)

This project implements an **AI agent that learns to play the game of Nim** using **Reinforcement Learning (Q-learning)**.
By repeatedly playing against itself, the AI learns which actions to take and which actions to avoid, eventually developing an optimal strategy to win.

---

## 🎮 Game Background

**Nim** is a mathematical game of strategy where:

* The game begins with several piles of objects.
* Players take turns removing one or more objects from a single pile.
* The player forced to take the **last object loses**.

Example:

* State: `[1, 1, 3, 5]` → Four piles with 1, 1, 3, and 5 objects.
* Action: `(3, 5)` → Take all 5 objects from pile 3.
* Resulting State: `[1, 1, 3, 0]`.

---

## 🤖 AI Approach

This project uses **Q-learning** to teach the AI how to play:

* A **state** is the current configuration of piles (e.g., `[1, 1, 3, 5]`).
* An **action** is removing `j` objects from pile `i` (e.g., `(3, 5)`).
* The AI assigns a **Q-value** to each `(state, action)` pair:

  * `+1` → if the action leads to a win.
  * `-1` → if the action leads to a loss.
  * `0` → if the game continues.

The Q-learning update rule:

```
Q(s, a) <- Q(s, a) + α * (reward + future_reward - Q(s, a))
```

Where:

* `α` (alpha) = learning rate.
* `reward` = immediate outcome of the action.
* `future_reward` = best possible Q-value from the next state.

---

## 📂 Project Structure

```
.
├── nim.py      # Contains Nim game logic and NimAI (Q-learning agent)
├── play.py     # Lets a human play against the trained AI
├── README.md   # Project documentation
```

* **Nim class** → Handles game rules, moves, and states.
* **NimAI class** → Implements Q-learning (functions like `get_q_value`, `update_q_value`, `best_future_reward`, `choose_action`).
* **train(n)** → Trains the AI by simulating `n` games against itself.
* **play(ai)** → Allows a human to play against the trained AI.

---

## 🛠️ Technologies Used

* **Python 3**
* **Reinforcement Learning (Q-learning)**
* Standard Python libraries (`random`, `collections`, etc.)
* Optional: `numpy` / `pandas` (for analysis, if added)

---

## 📊 Learning Behavior

* Initially, the AI makes random moves.
* With repeated self-play and Q-value updates, it learns **winning strategies**.
* Over time, it avoids losing moves and prioritizes optimal actions.

---

## ✨ Features

* Implements the Nim game rules.
* AI agent learns through reinforcement learning.
* Supports **epsilon-greedy** strategy (balancing exploration vs exploitation).
* Human vs AI gameplay.

---

