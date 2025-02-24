
## B2. State-Space Search: Representation of State Spaces
---

## B2.1 Representation of State Spaces

### Overview

State-space search is fundamental in artificial intelligence (AI) for solving problems where the solution is a sequence of actions leading from an initial state to a goal state. The challenge lies in efficiently representing these state spaces since they can be extremely large, often containing more than \(10^{10}\), \(10^{20}\), or even \(10^{100}\) states.

### Representation Methods

There are three primary methods to represent state spaces efficiently:

1. **Explicit Graphs**: Direct representation using graph structures.
2. **Declarative Representations**: Compact, formal descriptions that allow reasoning.
3. **Black Box Models**: Abstract interfaces for problem-solving without explicitly defining transitions.

Each method has different trade-offs in terms of memory usage, computational efficiency, and scalability.

---

## B2.2 Explicit Graphs

### Definition

A **state space** can be represented explicitly as a **directed graph** where:
- **Vertices** correspond to possible states.
- **Directed arcs** represent transitions between states due to actions.

This representation is commonly stored using:
- **Adjacency Lists**: Each state lists its directly connected successor states.
- **Adjacency Matrices**: A matrix where an entry at \((i,j)\) represents a transition from state \(i\) to state \(j\).

### Example: The 8-Puzzle

The **8-puzzle** consists of a 3×3 grid where a blank tile can be moved into an adjacent position by sliding a neighboring tile into the blank space. The state space is defined by:
- **States**: Different tile configurations.
- **Actions**: Possible tile movements.
- **Transitions**: Moving tiles from one configuration to another.

This state space can be represented explicitly as a graph where each vertex corresponds to a board configuration, and edges represent valid moves.

### Discussion: Feasibility of Explicit Representation

- **Scalability Issues**: Representing large state spaces explicitly is often infeasible due to excessive memory requirements.
- **Efficient Computation**: For small state spaces, shortest-path algorithms like **Dijkstra’s Algorithm** (complexity \(O(|S| \log |S| + |T|)\)) can be efficiently applied.
- **Use Cases**: Suitable for applications requiring fast, precomputed all-pairs shortest paths, such as route planning in navigation systems or AI in video games.

---

## B2.3 Declarative Representations

### Definition

Rather than explicitly listing states and transitions, a **declarative representation** provides a **compact symbolic description** of the state space. This enables algorithms to operate on the **problem specification** rather than an enumerated list of states.

### Key Characteristics

- **Compactness**: A small input description can define an exponentially large state space.
- **Algorithmic Efficiency**: Algorithms work on symbolic descriptions rather than expanding the full state space.
- **Automatic Reasoning**: Facilitates reformulation, simplification, and abstraction of problems.

### Example: Declarative Representation for the 8-Puzzle

A declarative representation of the 8-puzzle can be formulated using the **Planning Domain Definition Language (PDDL)**:
- **Domain File**: Defines actions (e.g., move blank tile up, down, left, right) and their effects.
- **Problem File**: Specifies the initial state and goal state.

This allows AI planners to generate sequences of actions leading to the solution without explicitly storing all possible states.

---

## B2.4 Black Box Models

### Definition

A **black box representation** abstracts away explicit state representation and instead provides an **interface for querying and manipulating states dynamically**.

### Interface Functions

For a state space \(S = \langle S, A, \text{cost}, T, s_I, S_G \rangle \), the following methods define the black box:

1. `init()`: Generates the **initial state** \(s_I\).
2. `is_goal(s)`: Checks if a state \(s\) belongs to the **goal set** \(S_G\).
3. `succ(s)`: Returns all applicable **actions** and their **successor states** \( \{(a, s') \} \), where \( s \xrightarrow{a} s' \).
4. `cost(a)`: Returns the **cost** associated with an action \(a\) (usually a non-negative integer).

### Example: Black Box Representation for the 8-Puzzle

A Python-based black box implementation (e.g., `puzzle8.py`) provides these functions, allowing algorithms to explore the problem dynamically rather than storing all states explicitly.

### Advantages

- **Scalability**: Handles very large state spaces efficiently by avoiding full enumeration.
- **Flexibility**: Can be extended for various problem-solving approaches.
- **Abstraction**: Decouples problem representation from specific implementations.

### Future Extension

Later in the course, we will refine the black box model to include additional functionalities to improve efficiency in problem-solving.

---

## B2.5 Summary

### Key Takeaways

- **State spaces are often massive** (> \(10^{10}\) states), requiring efficient representations.
- **Explicit graphs** work well for small problems but are impractical for large-scale problems.
- **Declarative representations** provide compact problem descriptions, enabling efficient AI planning and reasoning.
- **Black box models** abstract the state space into a dynamic interface, making large-scale search feasible.

Each representation has trade-offs and is suitable for different problem domains, depending on the scale and computational constraints.

