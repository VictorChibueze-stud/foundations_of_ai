### B4. State-Space Search: Data Structures for Search Algorithms

#### B4.1 Introduction

**Key Concept:** *State-Space Search*

**Formal Definition:** State-space search involves systematically exploring the space of possible states to find a solution. A state space is formally defined by:
- A set of states `S`
- A set of actions `A`
- A transition relation `T ⊆ S × A × S`
- An initial state `s_I ∈ S`
- A set of goal states `S_G ⊆ S`

**Example:** The "bounded inc-and-square" problem defined as follows:
- State set: `S = {0,1,...,9}`
- Actions: `A = {inc, sqr}`
- Transition: For each `i` in `S`, action `inc` transitions state `i` to `(i+1) mod 10` and action `sqr` transitions state `i` to `(i²) mod 10`
- Costs: `cost(inc) = cost(sqr) = 1`
- Initial state: `s_I = 1`
- Goal states: `S_G = {6,7}`

**Intuition:** Search algorithms systematically expand states to explore reachable solutions until a goal state is found or all states have been considered.

**Properties:** The environment of this search is discrete, deterministic, finite, and fully observable.

#### B4.2 Search Nodes

**Key Concept:** *Search Node*

**Formal Definition:** A search node stores information about a state that has been reached, how it was reached, and the cost of the path taken to reach it. A search node contains:
- `state`: The state associated with the node.
- `parent`: The parent node from which this node was generated (none for root node).
- `action`: The action taken from the parent state to the current state (none for root node).
- `path_cost` (`g(n)`): The total cost from the initial state to the current state, computed by summing action costs along the path.

**Example:** If node `n` represents state 4, reached from state 2 via the action `sqr`, the node has attributes:
- `n.state = 4`
- `n.parent = node representing state 2`
- `n.action = sqr`
- `n.path_cost = 2` (assuming each action costs 1)

**Intuition:** Search nodes allow reconstruction of paths from initial to goal states, storing essential information to determine the efficiency and correctness of a search algorithm.

**Implementation:** A simple Java implementation would have interfaces for `State` and `Action`, and a class `SearchNode` encapsulating the state, parent, action, and path cost attributes.

**Operations:**
- `make_root_node()`: initializes the root node with the initial state.
- `make_node(parent, action, state)`: creates a new search node from a parent node, an action, and the resulting state.
- `extract_path(node)`: reconstructs the sequence of actions leading to the given node by traversing parent pointers.

#### B4.3 Open Lists

**Key Concept:** *Open List (Frontier)*

**Formal Definition:** The open list manages nodes that are candidates for expansion (leaves of the search tree). It requires efficient support for two operations:
- Selecting and removing the next node for expansion.
- Inserting new candidate nodes.

**Intuition:** The open list is crucial for implementing search strategies, determining the order in which states are expanded, directly influencing efficiency and solution optimality.

**Implementation:** Usually implemented using priority queues, heaps, or deques rather than simple lists for efficiency. Selection strategy depends on the search algorithm (e.g., breadth-first, depth-first, uniform cost).

**Modification of Entries:** Some advanced implementations support updating nodes already in the open list if shorter paths to their states are found. However, simpler implementations avoid this by using delayed duplicate elimination.

#### B4.4 Closed Lists

**Key Concept:** *Closed List*

**Formal Definition:** The closed list maintains expanded states to prevent redundant expansions. It supports efficient operations:
- Insert new expanded states.
- Lookup states to check if they have already been expanded.

**Intuition:** Avoiding redundant state expansions significantly reduces computational overhead and memory usage, making search algorithms more efficient.

**Implementation:** Often implemented with hash tables where states are keys, allowing rapid insertion and lookup.

#### B4.5 Summary

In state-space search algorithms, essential data structures include:
- **Search Nodes:** Storing reached states, the path by which they were reached, and the cost.
- **Node Expansion:** Generating successor nodes by applying all valid actions.
- **Open Lists:** Organizing candidate nodes for expansion efficiently.
- **Closed Lists:** Remembering expanded states to avoid duplication.

Collectively, these structures underpin the implementation and performance optimization of fundamental search algorithms in artificial intelligence.

