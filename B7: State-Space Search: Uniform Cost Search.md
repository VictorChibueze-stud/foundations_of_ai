## B7. State-Space Search: Uniform Cost Search  

### B7.1 Introduction  

#### Uniform Cost Search  
**Key Concept**: Uniform Cost Search (UCS) is a search algorithm designed to handle problems where action costs vary. Unlike breadth-first search, which guarantees optimal solutions only when every action has an equal cost, uniform cost search addresses varying action costs by always selecting the node with the lowest cumulative cost (`path cost`) to expand next.

**Formal Definition**:  
In a state-space graph, where states are connected by actions with potentially different costs, uniform cost search systematically explores paths according to their total cumulative cost from the initial state. Formally, if we denote the path cost from the initial state to a node `n` as `g(n)`, uniform cost search selects and expands nodes from a priority queue sorted by increasing `g(n)` values.

**Example**:  
Consider the "bounded inc-and-square" example from previous chapters with the state space defined as follows:
- **State set**: \( S = \{0,1,2,3,4,5,6,7,8,9\} \)
- **Action set**: \( A = \{\text{inc}, \text{sqr}\} \)
- **Transition set** \( T \) contains pairs based on modular arithmetic operations:
  - Increment operation: \( \langle i, \text{inc}, (i+1)\mod{10}\rangle \in T \)
  - Cost for action "inc" is defined as 1.
  - Cost for action "sqr" is higher, specifically defined as 3.
- **Initial state**: \( s_I = 1 \)
- **Goal states**: \( S_G = \{6,7\} \)

Breadth-first search selects the shortest path in terms of number of actions, yielding the solution path: ⟨inc, sqr, sqr⟩ with a total cost of 7 (since each "sqr" costs 3). Uniform cost search, however, identifies that the path ⟨inc, inc, inc, inc, inc⟩, although longer, has a total cost of only 5, and hence is optimal.

**Intuition**:  
The fundamental intuition behind uniform cost search is that a solution's optimality depends on cumulative path cost rather than the number of steps. BFS is inadequate in cost-varied scenarios since it only measures path length, not cumulative cost. Uniform cost search corrects this by prioritizing cumulative cost (`g(n)`).

---

### B7.2 Algorithm  
**Uniform Cost Search Algorithm**:  
Uniform cost search can be described as a variation of the generic graph search algorithm. It utilizes a min-priority queue (`MinHeap`) sorted by the cumulative path cost `g(n)` of nodes, ensuring the node with the lowest cost is always expanded next. The closed list can be implemented as a simple hash set of states, given nodes' unique states fully define their identity.

Formally, the algorithm is defined as follows:

```pseudo
UniformCostSearch:
  open ← MinHeap ordered by g(n)
  open.insert(make_root_node())
  closed := new HashSet()

  while not open.is_empty():
    n ← open.pop_min()
    if n.state not in closed:
      closed.insert(n.state)
      if is_goal(n.state):
        return extract_path(n)
      for each action-successor pair ⟨a, s'⟩ in successors of n.state:
        n' ← make_node(n, a, s')
        open.insert(n')
return unsolvable
```

**Properties** of this approach are significant in practice:
- Early goal tests and immediate updates of closed lists upon node generation are avoided. Early tests would compromise optimality, as they could prematurely conclude a non-optimal path to a goal state.
- Uniform cost search directly corresponds to Dijkstra's shortest-path algorithm when applied to graph traversal with non-negative edge costs.

### B7.3 Properties  

#### Completeness and Optimality  
Uniform cost search is complete when applied to finite graphs with non-negative action costs, meaning it is guaranteed to find a solution if one exists, and it will terminate if no solution exists. The algorithm is also optimal, guaranteeing the least-cost solution, provided all action costs are non-negative.

**Explanation of completeness**:  
Since uniform cost search explores nodes based strictly on their cumulative costs from the start node, it systematically examines all potential solution paths in order of increasing path cost. Therefore, it will eventually reach the goal state through the cheapest possible route, assuming the state space is finite and all costs are non-negative.

**Explanation of optimality**:  
The optimality of uniform cost search arises directly from its priority-based expansion method. Because nodes are always expanded in ascending order of their path costs, the first goal node expanded must represent a path that is at least as cheap as any other possible path to a goal. Thus, no cheaper solution can exist undiscovered.

#### Time and Space Complexity  
Analyzing the complexity of uniform cost search is slightly more nuanced than breadth-first search because the complexity depends directly on the distribution of action costs across the state space. To formalize this, consider:

- \(\epsilon = \min_{a \in A} \text{cost}(a)\), the smallest possible action cost, which must be strictly positive.
- \(c^*\), the cost of an optimal solution path.

Given these parameters, the worst-case complexity for both time and space depends intricately on the problem structure and cost distribution. In the worst case, the complexity can be expressed as:

\[
O\left(b^{\lfloor c^*/\epsilon \rfloor}\)
\]

where \( b \) is the branching factor of the search space. This exponential complexity can quickly become prohibitive for large search spaces or small values of \(\epsilon\).

#### Practical Considerations and Improvements  
In practice, if action costs are close to uniform or vary slightly, bucket-based heaps (bucket queues) can significantly improve performance. Additionally, employing delayed duplicate elimination (DDE)—waiting to eliminate duplicate states until nodes are about to be expanded—can further improve memory and runtime efficiency. It requires careful management to ensure the optimality of solutions is maintained when paths to duplicated states differ in cost.

---

### B7.4 Summary  

Uniform cost search systematically explores state spaces by always selecting the node with the lowest cumulative path cost for expansion. It is a crucial algorithm for state-space search when action costs vary. It guarantees both completeness (in finite state spaces with non-negative costs) and optimality (always finding the cheapest path).

Its complexity primarily depends on two factors: the branching factor of the state-space graph and the minimal action cost. Despite potentially large time and memory requirements, uniform cost search is fundamentally important and serves as the basis for more advanced heuristic search methods covered in subsequent chapters.  

In conclusion, uniform cost search addresses significant limitations found in simpler search methods, such as breadth-first search, making it indispensable for solving realistic state-space search problems in Artificial Intelligence.
