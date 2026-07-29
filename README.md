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
|---------|---------|
| $S$ | Set of states |
| $A$ | Set of actions |
| $P$ | Transition probability function |
| $R$ | Reward function |
| $\gamma$ | Discount factor |

---

## State Space

The state space lists all possible situations in which the ambulance can exist.

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

The action space lists all possible actions available to the ambulance.

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

When the ambulance is at the **Free Cell**, it has four possible transitions.

| Current State | Action | Next State | Probability |
|---------------|--------|------------|-------------|
| Free Cell | Move Up | Free Cell | 0.25 |
| Free Cell | Move Down | Free Cell | 0.25 |
| Free Cell | Move Left | Obstacle | 0.25 |
| Free Cell | Move Right | Hospital | 0.25 |

Since the sum of all transition probabilities from the **Free Cell** is

$$
0.25+0.25+0.25+0.25=1.0
$$

the transition probabilities satisfy the MDP requirement.

Example:

$$
P(\text{Hospital}\mid\text{Free Cell},\text{Move Right})=0.25
$$

General form:

$$
P(s'|s,a)
$$

This represents the probability of reaching the next state $s'$ after taking action $a$ from the current state $s$.

---

## Reward Function

```text
Reach Hospital        = +100
Move to Free Cell     = -1
Hit Obstacle          = -10
Invalid Move          = -10
```

The reward function provides feedback after every action.

General form:

$$
R(s,a,s')
$$

---

## Graphical Representation

Draw the MDP graph using the following transitions.
<img width="2720" height="1720" alt="ambulance_mdp_corrected_graph" src="https://github.com/user-attachments/assets/93c7266b-7c67-4e9a-bc78-62daa1a22cdc" />


The transition probabilities from the **Free Cell** satisfy

---

## Python Representation

```python
# MDP Representation using Python

print("Name: Vikamuhan Reddy")
print("Register Number: 212223240181")

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

    # Start
    0: {
        3: [(1.0, 1, -1, False)]
    },

    # Free Cell
    1: {
        0: [(0.25, 1, -1, False)],
        1: [(0.25, 1, -1, False)],
        2: [(0.25, 2, -10, False)],
        3: [(0.25, 3, 100, True)]
    },

    # Obstacle
    2: {
        0: [(0.25, 2, -10, False)],
        1: [(0.25, 2, -10, False)],
        2: [(0.25, 2, -10, False)],
        3: [(0.25, 2, -10, False)]
    },

    # Hospital (Goal)
    3: {
        0: [(0.25, 3, 0, True)],
        1: [(0.25, 3, 0, True)],
        2: [(0.25, 3, 0, True)],
        3: [(0.25, 3, 0, True)]
    }
}


print("Ambulance Navigation MDP\n")

for state in P:
    print(f"State {state}:")
    print("{")
    for action in P[state]:
        print(f"  Action {action}: {P[state][action]}")
    print("}\n")
```

---

## Output

The program displays the transition probabilities, rewards, and terminal states for each state-action pair of the Ambulance Navigation MDP.


<img width="150" height="250" alt="image" src="https://github.com/user-attachments/assets/232b0892-a398-46ee-992f-f830a73d6377" />


---

## Result

Thus, the **Ambulance Navigation System** was successfully represented as a **Markov Decision Process (MDP)** by defining its states, actions, transition probabilities, reward function, graphical representation, and Python implementation. The transition probabilities were updated so that they satisfy the MDP property that the total transition probability from a state equals **1.0**.
