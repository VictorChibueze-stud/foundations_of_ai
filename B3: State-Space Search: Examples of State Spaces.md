### State-Space Search: Examples of State Spaces
---

### **B3.1 Route Planning in Romania**

#### **Introduction to Route Planning**
Route planning is a classic problem in AI, where the goal is to find the best path from a starting location to a destination. In this example, we are in Romania, starting in **Arad**, and need to reach **Bucharest** to catch a flight. The problem is modeled as a **state-space search**, where the states represent cities, and the actions represent moving between cities connected by roads.

#### **Formal Definition of the State Space**
The state space for route planning in Romania can be formally defined as follows:
- **States (S)**: The set of all cities in Romania, e.g., {Arad, Bucharest, Craiova, ..., Zerind}.
- **Actions (A)**: The set of possible moves between cities. For any two cities **c** and **c'** connected by a road, there is an action **move_{c,c'}**.
- **Action Costs (cost)**: The cost of moving between cities is given by the distance between them. For example, the cost of moving from Iasi to Vaslui is 92.
- **Transitions (T)**: A transition **s → s'** occurs if there is an action **move_{s,s'}** that takes the agent from state **s** to state **s'**.
- **Initial State (s₁)**: The starting city, which is **Arad**.
- **Goal States (S_G)**: The destination city, which is **Bucharest**.

#### **Intuition and Example**
The problem is essentially a graph traversal problem, where cities are nodes, and roads are edges with associated costs. The goal is to find the shortest (or least costly) path from Arad to Bucharest. This problem is **fully observable** (the agent knows the entire map), **deterministic** (the outcome of each action is certain), and **static** (the environment doesn’t change while the agent is planning).

---

### **B3.2 Blocks World**

#### **Introduction to Blocks World**
The Blocks World is a classic AI problem that involves manipulating blocks on a table. The goal is to rearrange the blocks from an initial configuration to a desired goal configuration by moving one block at a time. This problem is often used to illustrate planning and state-space search in AI.

#### **Formal Definition of the State Space**
The state space for the Blocks World with **n** blocks can be formally defined as follows:
- **States (S)**: The states are partitions of the set of blocks {1, 2, ..., n} into non-empty ordered lists. Each list represents a tower of blocks, and the order within the list represents the stacking order. For example, with 3 blocks, possible states include:
  - {(1, 2, 3)} (all blocks in one tower),
  - {(1, 2), {3}} (two towers, one with blocks 1 and 2, and another with block 3),
  - {(1), {2}, {3}} (each block in its own tower).
- **Actions (A)**: There are two types of actions:
  1. **move_{u,v}**: Move block **u** onto block **v**. Both blocks must be the top blocks of their respective towers.
  2. **to-table_u**: Move block **u** onto the table, creating a new tower.
- **Action Costs (cost)**: All actions have a cost of 1.
- **Transitions (T)**: A transition **s → s'** occurs if an action **a** is applied to state **s**, resulting in state **s'**. For example:
  - If **a = move_{u,v}**, then block **u** is moved from its current tower to the top of block **v**'s tower.
  - If **a = to-table_u**, then block **u** is moved from its current tower to the table, forming a new tower.
- **Initial State (s₁)**: The starting configuration of the blocks. For example, with 3 blocks, the initial state could be {(1, 3), {2}}.
- **Goal States (S_G)**: The desired configuration of the blocks. For example, the goal state could be {(3, 2, 1)}.

#### **Intuition and Example**
The Blocks World is a **discrete**, **deterministic**, and **static** environment. The number of possible states grows rapidly with the number of blocks, making the problem computationally challenging for large **n**. However, simple algorithms can find solutions in **O(n)** time, though finding **optimal solutions** (the shortest sequence of moves) is **NP-complete**.

---

### **B3.3 Missionaries and Cannibals**

#### **Introduction to Missionaries and Cannibals**
The Missionaries and Cannibals problem is a classic puzzle in AI. The goal is to transport six people (three missionaries and three cannibals) across a river using a boat that can carry one or two people at a time. The constraint is that the missionaries must never be outnumbered by cannibals on either side of the river, as this would result in the missionaries being eaten.

#### **Formal Definition of the State Space**
The state space for the Missionaries and Cannibals problem can be formally defined as follows:
- **States (S)**: Each state is represented by a triple **(m, c, b)**, where:
  - **m**: The number of missionaries on the left bank.
  - **c**: The number of cannibals on the left bank.
  - **b**: The location of the boat (0 for the right bank, 1 for the left bank).
- **Initial State (s₁)**: The starting state is **(3, 3, 1)**, meaning all missionaries, cannibals, and the boat are on the left bank.
- **Goal States (S_G)**: The goal is to reach a state where all missionaries and cannibals are on the right bank, i.e., **(0, 0, 0)** or **(0, 0, 1)**.
- **Actions (A)**: The possible actions involve moving one or two people (missionaries or cannibals) across the river. The exact actions depend on the current state and must ensure that the missionaries are never outnumbered by cannibals on either bank.
- **Action Costs (cost)**: All actions have a cost of 1.
- **Transitions (T)**: A transition **s → s'** occurs if an action is applied to state **s**, resulting in state **s'**. For example, moving one missionary and one cannibal from the left bank to the right bank would change the state from **(3, 3, 1)** to **(2, 2, 0)**.

#### **Intuition and Example**
This problem is a **discrete**, **deterministic**, and **static** environment with a small state space (only 32 possible states, many of which are unreachable due to constraints). The challenge lies in finding a sequence of actions that satisfies the constraints and reaches the goal state. It is a classic example of a **constraint satisfaction problem** in AI.

---

### **Summary**

1. **Route Planning in Romania**: A small, explicitly representable state space where the goal is to find the shortest path from Arad to Bucharest. The problem is fully observable, deterministic, and static.

2. **Blocks World**: A family of tasks where **n** blocks must be rearranged into a goal configuration. The number of states grows rapidly with **n**, making the problem computationally challenging. Simple algorithms can find solutions in **O(n)** time, but finding optimal solutions is NP-complete.

3. **Missionaries and Cannibals**: A traditional puzzle with a small state space (32 states) and strict constraints. The goal is to transport missionaries and cannibals across a river without violating the constraints.

These examples illustrate different types of state spaces and the challenges associated with solving problems in AI. Each problem has unique properties that influence the choice of algorithms and problem-solving methods.

---

Let me know if you need further clarification or additional examples!
