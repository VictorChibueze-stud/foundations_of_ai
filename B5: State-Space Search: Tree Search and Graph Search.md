### B5. State-Space Search: Tree Search and Graph Search

#### B5.1 Introduction

**Key Concept**: *State-Space Search Algorithms*

**Formal Definition:** State-space search algorithms systematically explore possible states from an initial state to goal states. The search is structured through the expansion of states, generating successor states using defined transitions and actions.

This chapter introduces two fundamental classes of search algorithms:
- **Tree Search**
- **Graph Search**

Both categories contain numerous specific algorithms, each optimized for different search contexts.

#### B5.2 Tree Search

**Key Concept**: *Tree Search*

**Formal Definition:** Tree search is a method of systematically exploring paths in a state-space. It uses a search tree structure, where each node corresponds uniquely to a single path originating from the initial state.

**Example:** In the bounded increment-and-square problem (states {0,...,9}, actions {inc, sqr}), multiple paths can exist to the same state. Each unique path generates a separate node, even if states repeat across different paths.

**Intuition:** The search tree may contain duplicate states—also called transpositions—leading to inefficiencies. Furthermore, the search tree can potentially have infinite depth if state spaces contain cycles.

**Generic Tree Search Algorithm:**  
A typical tree search initializes an open list with the initial state node. It then repeatedly selects a node for expansion, checking if it's a goal. If not, it generates all successors of that state and inserts these successors into the open list. If the open list becomes empty before reaching a goal, the search reports failure (unsolvable).

#### B5.3 Graph Search

**Key Concept**: *Graph Search*

**Formal Definition:** Graph search refines the tree search by identifying and eliminating duplicate nodes, ensuring each state is represented by exactly one node in the search structure.

**Example:** Considering again the bounded increment-and-square problem, when the algorithm encounters a state previously expanded, it does not generate a new node but reuses the existing one, thus effectively eliminating redundant work.

**Intuition:** This elimination significantly reduces computational effort by avoiding unnecessary re-explorations, providing efficiency gains particularly relevant in large state spaces.

**Generic Graph Search Algorithm:**
The graph search introduces an additional data structure known as the closed list, which keeps track of all expanded states. Before expanding a node, the algorithm checks if the state has already been explored. Only unvisited states are expanded, thus ensuring each state is considered once, resulting in efficiency improvements.

#### B5.4 Evaluating Search Algorithms

When evaluating the performance and effectiveness of search algorithms, four primary criteria are considered:

**Completeness:**
Completeness refers to the guarantee that an algorithm finds a solution if one exists. If an algorithm terminates whenever no solution exists but guarantees finding one when it does, it is considered complete. An algorithm that only guarantees finding a solution if one exists (but does not guarantee termination if none exists) is termed semi-complete.

**Optimality:**
Optimality addresses whether the solutions returned by an algorithm are always the best or most efficient (i.e., minimal cost).

**Time Complexity:**
Time complexity assesses the duration or computational steps an algorithm requires to reach termination, typically measured by the number of nodes generated during the search. This complexity is usually expressed relative to branching factor (*b*, the maximum number of successors per state) and depth (*d*, the length of the longest path explored).

**Space Complexity:**
Space complexity evaluates the memory requirements of the algorithm, measured in the maximum number of concurrently stored nodes. It is similarly expressed in terms of branching factor (*b*) and search depth (*d*).

#### Analysis of Generic Algorithms:
- **Generic Tree Search:** May not be complete due to possible infinite loops from transpositions; optimality is not guaranteed without special measures. The worst-case time and space complexity depend primarily on branching factor and depth, usually exponential.
- **Generic Graph Search:** Typically more efficient and complete due to duplicate elimination. Optimality can depend on specific implementations (such as delayed duplicate elimination). Complexity is also related to branching factor and depth but generally lower than tree search because of duplicate state handling.

#### B5.5 Summary

**Summary:**  
Tree search explores paths from the initial state without recognizing repeated states, potentially causing inefficiency through duplication. Graph search improves upon this by ensuring each reachable state corresponds uniquely to a single node in the search structure, significantly reducing redundancy.

Evaluation criteria for these algorithms include completeness, optimality, and complexity (both time and space), providing a framework to assess performance and guide algorithm selection depending on the problem context and computational resources.

