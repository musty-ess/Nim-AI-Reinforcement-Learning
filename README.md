# Nim AI - Reinforcement Learning

This project implements an AI that teaches itself to play the game of **Nim** using **Q-learning**, a form of reinforcement learning. By playing thousands of games against itself, the AI learns optimal strategies for playing Nim, eventually improving its performance by updating a reward table based on game outcomes.

## Table of Contents
- [Nim AI - Reinforcement Learning](#nim-ai---reinforcement-learning)
  - [Table of Contents](#table-of-contents)
  - [Background](#background)
    - [Reinforcement Learning with Q-Learning](#reinforcement-learning-with-q-learning)
  - [Getting Started](#getting-started)
  - [Project Files](#project-files)
  - [How It Works](#how-it-works)
    - [Game Representation](#game-representation)
    - [Q-learning](#q-learning)
  - [Usage](#usage)

## Background
**Nim** is a mathematical game of strategy where two players take turns removing any number of objects from a single pile. The player forced to take the last object loses the game. With multiple piles, the strategy becomes more complex.

The goal of this project is to build an AI that learns the best strategies for playing Nim through self-play. The AI will make decisions based on the current state of the game, aiming to maximize the reward (win the game) and avoid penalties (lose the game).

### Reinforcement Learning with Q-Learning
In Q-learning, the AI learns to assign a reward value to every possible (state, action) pair. Over time, the AI refines these reward values by updating them based on the outcomes of actions it takes during games. The formula for updating the Q-value is as follows: `Q(s, a) <- Q(s, a) + alpha * (new value estimate - old value estimate)`


Where:
- `s`: the current state (list of pile sizes).
- `a`: the action taken (which pile to take from and how many objects to remove).
- `alpha`: the learning rate, determining how much to value new information.
- The new value estimate incorporates both immediate rewards and future rewards.

By playing thousands of games against itself, the AI improves its decision-making process and learns to play optimally.

## Getting Started

To run this project, ensure you have **Python 3.12** installed. You can install the necessary dependencies by running the following command (if applicable): `pip install numpy pandas`

1. **Clone the repo**: `git clone https://github.com/musty-ess/Nim-AI-Reinforcement-Learning.git`
2. **Install necessary dependencies**: `pip install numpy pandas`
3. **Run**: `python play.py`

## Project Files  
- `nim.py`: Contains two main classes:
  - `Nim`: Defines the rules and structure of the Nim game, including available actions and managing players.
  - `NimAI`: Contains the reinforcement learning agent, responsible for training and playing the game.

- `play.py`: A script used to train the AI by simulating a large number of games and allowing humans to play against the trained AI.

## How It Works

### Game Representation
- **State**: A state is represented as a list of integers, where each integer corresponds to the number of objects in a pile. For example, `[1, 3, 5, 7]` means pile 0 has 1 object, pile 1 has 3, pile 2 has 5, and pile 3 has 7 objects.
  
- **Action**: An action is represented as a tuple `(i, j)`, where `i` is the index of the pile, and `j` is the number of objects to remove from that pile.

### Q-learning
The AI learns by playing multiple games against itself and updating its knowledge of state-action pairs. For each state, the AI calculates the best possible action based on its experience (the Q-values it has learned).

The following key functions were implemented to complete the AI:
1. **`get_q_value(state, action)`**: Returns the Q-value for a given state and action.
2. **`update_q_value(state, action, old_q, reward, future_rewards)`**: Updates the Q-value using the Q-learning formula.
3. **`best_future_reward(state)`**: Returns the best possible reward for any action in a given state.
4. **`choose_action(state, epsilon=False)`**: Chooses the best action for a state, either using the greedy approach or the epsilon-greedy approach for exploration.

## Usage

1. **Training the AI**
Run the following command to train the AI by simulating 10,000 games: `python play.py`

The AI will play a large number of games, updating its knowledge through Q-learning.

**Example output**:
```bash
Playing training game 1
Playing training game 2
...
Playing training game 10000
Done training
```

2. **Playing against the AI**
After training, you can play against the AI:
```bash
Piles:
Pile 0: 1
Pile 1: 3
Pile 2: 5
Pile 3: 7

AI's Turn
AI chose to take 1 from pile 2.
```
The AI will make its move based on the strategies it learned during training, and you can play against it interactively.# Nim-AI-Reinforcement-Learning
