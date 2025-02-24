# State-Space Search: Examples of State Spaces

---

## **B3.1 Route Planning in Romania**

### **Introduction to Route Planning**
Route planning is a classic problem in artificial intelligence (AI), where the goal is to find the best path from a starting location to a destination. In this example, we are in Romania, starting in **Arad**, and need to reach **Bucharest** to catch a flight. The problem is modeled as a **state-space search**, where the states represent cities, and the actions represent moving between cities connected by roads.

### **Formal Definition of the State Space**
The state space for route planning in Romania can be formally defined as follows:

1. **States (S)**: The set of all cities in Romania, e.g., {Arad, Bucharest, Craiova, ..., Zerind}.
2. **Actions (A)**: The set of possible moves between cities. For any two cities **c** and **c'** connected by a road, there is an action **move_{c,c'}**.
3. **Action Costs (cost)**: The cost of moving between cities is given by the distance between them. For example, the cost of moving from Iasi to Vaslui is 92.
4. **Transitions (T)**: A transition **s → s'** occurs if there is an action **move_{s,s'}** that takes the agent from state **s** to state **s'**.
5. **Initial State (s₁)**: The starting city, which is **Arad**.
6. **Goal States (S_G)**: The destination city, which is **Bucharest**.

### **Intuition and Example**
The problem is essentially a graph traversal problem, where cities are nodes, and roads are edges with associated costs. The goal is to find the shortest (or least costly) path from Arad to Bucharest. This problem is:

- **Fully observable**: The agent knows the entire map and all possible routes.
- **Deterministic**: The outcome of each action (moving from one city to another) is certain.
- **Static**: The environment (the map of Romania) does not change while the agent is planning.

#### **Example Path**
One possible path from Arad to Bucharest is:
- Arad → Sibiu → Fagaras → Bucharest.

This path has a total cost of 140 + 99 + 211 = 450. However, a more optimal path might be:
- Arad → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest.

This path has a total cost of 140 + 80 + 97 + 101 = 418.

### **Visual Representation**
The state space can be visualized as a graph:

```
Arad --140-- Sibiu --99-- Fagaras --211-- Bucharest
 |             |             |
140           80            97
 |             |             |
Zerind         Rimnicu Vilcea -- Pitesti --101-- Bucharest
```

---

## **B3.2 Blocks World**

### **Introduction to Blocks World**
The Blocks World is a classic AI problem that involves manipulating blocks on a table. The goal is to rearrange the blocks from an initial configuration to a desired goal configuration by moving one block at a time. This problem is often used to illustrate planning and state-space search in AI.

### **Formal Definition of the State Space**
The state space for the Blocks World with **n** blocks can be formally defined as follows:

1. **States (S)**: The states are partitions of the set of blocks {1, 2, ..., n} into non-empty ordered lists. Each list represents a tower of blocks, and the order within the list represents the stacking order. For example, with 3 blocks, possible states include:
   - {(1, 2, 3)} (all blocks in one tower),
   - {(1, 2), {3}} (two towers, one with blocks 1 and 2, and another with block 3),
   - {(1), {2}, {3}} (each block in its own tower).
2. **Actions (A)**: There are two types of actions:
   - **move_{u,v}**: Move block **u** onto block **v**. Both blocks must be the top blocks of their respective towers.
   - **to-table_u**: Move block **u** onto the table, creating a new tower.
3. **Action Costs (cost)**: All actions have a cost of 1.
4. **Transitions (T)**: A transition **s → s'** occurs if an action **a** is applied to state **s**, resulting in state **s'**. For example:
   - If **a = move_{u,v}**, then block **u** is moved from its current tower to the top of block **v**'s tower.
   - If **a = to-table_u**, then block **u** is moved from its current tower to the table, forming a new tower.
5. **Initial State (s₁)**: The starting configuration of the blocks. For example, with 3 blocks, the initial state could be {(1, 3), {2}}.
6. **Goal States (S_G)**: The desired configuration of the blocks. For example, the goal state could be {(3, 2, 1)}.

### **Intuition and Example**
The Blocks World is a **discrete**, **deterministic**, and **static** environment. The number of possible states grows rapidly with the number of blocks, making the problem computationally challenging for large **n**. However, simple algorithms can find solutions in **O(n)** time, though finding **optimal solutions** (the shortest sequence of moves) is **NP-complete**.

#### **Example Problem**
- **Initial State**: {(1, 3), {2}}.
- **Goal State**: {(3, 2, 1)}.
- **Solution**: Move block 3 to the table, then move block 2 onto block 1, and finally move block 3 onto block 2.

### **Visual Representation**
The state space can be visualized as a tree, where each node represents a state, and edges represent actions:

```
Initial State: {(1, 3), {2}}
   |
   | (move 3 to table)
   v
State 1: {(1), {2}, {3}}
   |
   | (move 2 onto 1)
   v
State 2: {(1, 2), {3}}
   |
   | (move 3 onto 2)
   v
Goal State: {(3, 2, 1)}
```

---

## **B3.3 Missionaries and Cannibals**

### **Introduction to Missionaries and Cannibals**
The Missionaries and Cannibals problem is a classic puzzle in AI. The goal is to transport six people (three missionaries and three cannibals) across a river using a boat that can carry one or two people at a time. The constraint is that the missionaries must never be outnumbered by cannibals on either side of the river, as this would result in the missionaries being eaten.

### **Formal Definition of the State Space**
The state space for the Missionaries and Cannibals problem can be formally defined as follows:

1. **States (S)**: Each state is represented by a triple **(m, c, b)**, where:
   - **m**: The number of missionaries on the left bank.
   - **c**: The number of cannibals on the left bank.
   - **b**: The location of the boat (0 for the right bank, 1 for the left bank).
2. **Initial State (s₁)**: The starting state is **(3, 3, 1)**, meaning all missionaries, cannibals, and the boat are on the left bank.
3. **Goal States (S_G)**: The goal is to reach a state where all missionaries and cannibals are on the right bank, i.e., **(0, 0, 0)** or **(0, 0, 1)**.
4. **Actions (A)**: The possible actions involve moving one or two people (missionaries or cannibals) across the river. The exact actions depend on the current state and must ensure that the missionaries are never outnumbered by cannibals on either bank.
5. **Action Costs (cost)**: All actions have a cost of 1.
6. **Transitions (T)**: A transition **s → s'** occurs if an action is applied to state **s**, resulting in state **s'**. For example, moving one missionary and one cannibal from the left bank to the right bank would change the state from **(3, 3, 1)** to **(2, 2, 0)**.

### **Intuition and Example**
This problem is a **discrete**, **deterministic**, and **static** environment with a small state space (only 32 possible states, many of which are unreachable due to constraints). The challenge lies in finding a sequence of actions that satisfies the constraints and reaches the goal state. It is a classic example of a **constraint satisfaction problem** in AI.

#### **Example Solution**
1. Move two cannibals to the right bank: (3, 3, 1) → (3, 1, 0).
2. Return one cannibal to the left bank: (3, 1, 0) → (3, 2, 1).
3. Move two missionaries to the right bank: (3, 2, 1) → (1, 2, 0).
4. Return one missionary and one cannibal to the left bank: (1, 2, 0) → (2, 3, 1).
5. Move two cannibals to the right bank: (2, 3, 1) → (2, 1, 0).
6. Return one cannibal to the left bank: (2, 1, 0) → (2, 2, 1).
7. Move two missionaries to the right bank: (2, 2, 1) → (0, 2, 0).
8. Return one cannibal to the left bank: (0, 2, 0) → (0, 3, 1).
9. Move two cannibals to the right bank: (0, 3, 1) → (0, 1, 0).
10. Return one cannibal to the left bank: (0, 1, 0) → (0, 2, 1).
11. Move two cannibals to the right bank: (0, 2, 1) → (0, 0, 0).

### **Visual Representation**
The state space can be visualized as a graph, where each node represents a state, and edges represent valid actions:

```
(3, 3, 1) → (3, 1, 0) → (3, 2, 1) → (1, 2, 0) → (2, 3, 1) → ... → (0, 0, 0)
```

---

## **Summary**

1. **Route Planning in Romania**: A small, explicitly representable state space where the goal is to find the shortest path from Arad to Bucharest. The problem is fully observable, deterministic, and static.

2. **Blocks World**: A family of tasks where **n** blocks must be rearranged into a goal configuration. The number of states grows rapidly with **n**, making the problem computationally challenging. Simple algorithms can find solutions in **O(n)** time, but finding optimal solutions is NP-complete.

3. **Missionaries and Cannibals**: A traditional puzzle with a small state space (32 states) and strict constraints. The goal is to transport missionaries and cannibals across a river without violating the constraints.

These examples illustrate different types of state spaces and the challenges associated with solving problems in AI. Each problem has unique properties that influence the choice of algorithms and problem-solving methods.

--- 

### **Key Takeaways**
- **State-space search** is a powerful framework for modeling and solving problems in AI.
- The **complexity** of a state-space search problem depends on the size of the state space and the constraints involved.
- **Graph representations** are often used to visualize state spaces and transitions.
- **Optimal solutions** may require sophisticated algorithms, especially in large or constrained state spaces.
