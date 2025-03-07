### B6. State-Space Search: Breadth-first Search

#### B6.1 Blind Search

**Key Concept:** *Blind Search Algorithms*

**Formal Definition:** Blind search algorithms, also known as uninformed search algorithms, operate without any domain-specific knowledge about the state space, other than what is provided through a generic black-box interface. They explore state spaces systematically without guidance or heuristics.

Examples of blind search algorithms include:
- Breadth-first search
- Uniform cost search
- Depth-first search
- Depth-limited search
- Iterative deepening search

This chapter specifically explores breadth-first search (BFS).

#### B6.2 Breadth-first Search: Introduction

**Key Concept:** *Breadth-first Search (BFS)*

**Formal Definition:** Breadth-first search is an algorithm that expands nodes in the order they were generated, implementing a First-In-First-Out (FIFO) strategy for node expansion. Typically, an open list structured as a queue or deque manages this node expansion order.

**Example:** Consider the bounded inc-and-square problem with states `{0,1,...,9}` and actions `{inc, sqr}`, starting from state `1` with goal states `{6,7}`. BFS systematically explores all states reachable within a given number of steps from the initial state, layer by layer.

**Intuition:** Because of the FIFO property, BFS always finds the shallowest goal node first, ensuring minimal solution depth when action costs are uniform.

#### B6.3 BFS-Tree

**Key Concept:** *BFS-Tree*

**Formal Definition:** BFS-Tree performs breadth-first search without duplicate elimination. Each unique path creates a new node, even if this results in repeated states. Thus, the search tree can potentially contain infinite nodes if cycles are present.

**Algorithm (final version):**
```pseudo
if is_goal(init()):
    return empty path
open = new deque
open.push_back(make_root_node())
while not open.is_empty():
    n = open.pop_front()
    for each action a and resulting state s' in successors(n.state):
        n' = make_node(n, a, s')
        if is_goal(s'):
            return extract_path(n')
        open.push_back(n')
return unsolvable
```

**Intuition:** Early goal testing immediately upon node generation optimizes BFS-Tree by preventing unnecessary node expansions once a goal node is generated.

#### B6.4 BFS-Graph

**Key Concept:** *BFS-Graph*

**Formal Definition:** BFS-Graph incorporates duplicate elimination by using a closed list (usually a hash set) to track visited states. It ensures each state is only expanded once.

**Algorithm:**
```pseudo
if is_goal(init()):
    return empty path
open = new deque
open.push_back(make_root_node())
closed = new hash_set
closed.insert(init())
while not open.is_empty():
    n = open.pop_front()
    for each action a and resulting state s' in successors(n.state):
        if s' not in closed:
            n' = make_node(n, a, s')
            if is_goal(s'):
                return extract_path(n')
            closed.insert(s')
            open.push_back(n')
return unsolvable
```

**Example:** For the bounded inc-and-square problem, the BFS-Graph approach prevents duplicate explorations, significantly reducing the number of generated nodes compared to BFS-Tree.

#### B6.5 Properties of Breadth-first Search

**Completeness:** BFS-Tree is semi-complete—it finds solutions if they exist but might not terminate if none exist due to infinite loops. BFS-Graph is complete, as duplicate elimination prevents infinite loops.

**Optimality:** Both BFS variants are optimal when all actions have equal cost, as they always find the shallowest goal first. However, they are not guaranteed optimal with varied action costs.

**Time and Space Complexity:**
The complexity for both BFS-Tree and BFS-Graph is defined as follows, where `b` is the branching factor and `d` is the minimal depth to a solution:

\[
O(b^d)
\]

This complexity implies exponential growth in nodes generated and stored, illustrating significant computational limitations in large search spaces.

**Example (Rubik's Cube):** Given a branching factor of about `13` and typical solution depth of around `18`, BFS would require impractically large computational resources, highlighting the algorithm's limitations.

**Comparison:** BFS-Graph is generally superior to BFS-Tree because of completeness and significantly better efficiency in cases with many duplicate states. However, BFS-Tree may have lower overhead if duplicates are negligible.

#### B6.6 Summary

Breadth-first search is a fundamental blind search algorithm characterized by systematic, layer-by-layer exploration using a FIFO strategy. BFS can be executed as either BFS-Tree (no duplicate elimination, semi-complete) or BFS-Graph (duplicate elimination, complete). Its optimality holds under uniform action costs, while its computational complexity is exponential (`O(b^d)`), limiting practical usage in large or complex state spaces. Typically, BFS-Graph is preferred unless duplicate states are known to be rare.

