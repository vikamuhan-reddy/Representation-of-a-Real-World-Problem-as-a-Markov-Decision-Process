# Representation of a Real-World Problem as a Markov Decision Process

## Aim

To represent an **Ambulance Navigation System** in a confined environment with obstacles as a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, rewards, and Python representation.

---

## Problem Statement

### Problem Description

An ambulance must travel from a starting location to a hospital in a confined grid while avoiding obstacles such as roadblocks and blocked paths. At each step, the ambulance decides whether to move up, down, left, or right. The objective is to reach the hospital safely in the shortest possible path while maximizing the total reward.

---

## MDP Components

A Markov Decision Process is represented as:

$$
MDP = (S, A, P, R, \gamma)
$$

Where:

| Symbol | Meaning |
|---|---|
| $S$ | Set of states |
| $A$ | Set of actions |
| $P$ | Transition probability function |
| $R$ | Reward function |
| $\gamma$ | Discount factor |

---

## State Space

The state space should list all possible situations in which the ambulance can exist.

Example format:

```text
S = {
    Start,
    Free Cell,
    Obstacle,
    Hospital (Goal)
}
```

---

## Sample State

**Free Cell**

A sample state is one specific example from the state space.

---

## Action Space

The action space should list all possible actions available to the ambulance.

Example format:

```text
A = {
    Move Up,
    Move Down,
    Move Left,
    Move Right
}
```

---

## Sample Action

**Move Right**

A sample action is one action selected from the action space.

---

## Transition Probability

If the ambulance is at the **Free Cell** and chooses **Move Right**, it reaches the next free cell with probability **1.0**.

$$
P(\text{Next Free Cell} \mid \text{Free Cell}, \text{Move Right}) = 1.0
$$

The transition probability explains how the environment moves from one state to another after an action is taken.

General form:

$$
P(s' \mid s,a)
$$

This means:

> Probability of reaching the next state $s'$ after taking action $a$ in the current state $s$.

---

## Reward Function

```text
Reach Hospital = +100
Move to Free Cell = -1
Hit Obstacle/Invalid Move = -10
```

The reward function defines the feedback received by the ambulance after taking an action.

General form:

$$
R(s,a,s')
$$

---

## Graphical Representation

Draw the MDP graph.

The graph should include:

1. States as nodes.
2. Actions as arrows.
3. Rewards on transitions.
4. Transition probabilities if applicable.

<img width="450" height="400" alt="ambulance_navigation_mdp_graph" src="https://github.com/user-attachments/assets/0cc5b672-54cd-4910-b380-22c8d6f29cb8" />



---

## Python Representation

```python
# MDP Representation using Python
# print("Name: ")
# print("Register Number: ")

# Ambulance Navigation MDP

# States
# 0 = Start
# 1 = Free Cell
# 2 = Obstacle
# 3 = Hospital (Goal)

# Actions
# 0 = Move Up
# 1 = Move Down
# 2 = Move Left
# 3 = Move Right

P = {
    0: {
        3: [(1.0, 1, -1, False)]
    },

    1: {
        0: [(1.0, 1, -1, False)],
        1: [(1.0, 1, -1, False)],
        2: [(1.0, 2, -10, False)],
        3: [(1.0, 3, 100, True)]
    },

    2: {
        0: [(1.0, 2, -10, False)],
        1: [(1.0, 2, -10, False)],
        2: [(1.0, 2, -10, False)],
        3: [(1.0, 2, -10, False)]
    },

    3: {
        0: [(1.0, 3, 0, True)],
        1: [(1.0, 3, 0, True)],
        2: [(1.0, 3, 0, True)],
        3: [(1.0, 3, 0, True)]
    }
}

print("Ambulance Navigation MDP\n")

for state in P:
    print(f"{state}:")
    print(" {")
    for action in P[state]:
        print(f"   {action}: {P[state][action]}")
    print(" }\n")
```



## Output





## Result

Thus, the MDP model for Ambulance Navigation in a Confined Environment with Obstacles was successfully created and represented using Python.
