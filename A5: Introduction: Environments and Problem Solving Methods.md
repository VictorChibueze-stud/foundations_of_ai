## A5. Introduction: Environments and Problem Solving Methods
---

## A5.1 Environments of Rational Agents

### Definition of an Environment

An **environment** in AI refers to the external context in which an agent operates. It includes all external factors that affect the agent’s decision-making process.

### Components of an AI Agent System

- **Agent**: The decision-making entity.
- **Sensors**: Devices that provide the agent with observations about the environment.
- **Actuators**: Mechanisms that allow the agent to affect the environment.
- **Agent Program**: The algorithm that processes observations and determines actions.
- **Performance Measure**: The metric used to evaluate the agent’s success.

### Key Questions
- Which aspects of the environment are relevant for the agent?
- How do the agent’s actions impact the environment?
- What observations does the agent receive from the environment?

### Properties of Environments

1. **Observability**
   - *Fully Observable*: The agent has complete information about the environment at all times.
   - *Partially Observable*: The agent only has limited or incomplete information.
   - *Unobservable*: The agent has no direct access to environmental data.

2. **Agent Interaction**
   - *Single-Agent*: The agent operates independently.
   - *Multi-Agent*: The environment includes other agents, which may be adversarial, cooperative, or neutral.

3. **Determinism**
   - *Deterministic*: The next state is fully determined by the current state and the agent’s action.
   - *Nondeterministic*: The next state is not fully predictable.
   - *Stochastic*: Probabilities determine state transitions.

4. **Environment Changeability**
   - *Static*: The environment does not change while the agent deliberates.
   - *Dynamic*: The environment evolves over time, even without agent interaction.

5. **Nature of Variables**
   - *Discrete*: The environment consists of a finite number of distinct states.
   - *Continuous*: The environment includes an infinite or uncountable number of possible states.

### Impact on AI Problem Solving

Different environments require specialized problem-solving strategies. The real world typically combines several complex properties, making it a challenging environment for AI.

---

## A5.2 Problem Solving Methods

### Three Approaches to Solving AI Problems

1. **Problem-Specific Algorithms**
   - Tailored to a particular problem.
   - Takes advantage of domain-specific knowledge.
   - Limited to solving only one type of problem efficiently.

2. **General Problem Solvers**
   - User defines a model of the problem instance using a formal representation.
   - A general solver computes solutions using established algorithms.
   - Suitable for a broad range of problems but may lack optimization for specific cases.

3. **Learning-Based Methods**
   - The agent learns problem-solving strategies from data.
   - Adaptation occurs through experience rather than predefined rules.
   - Requires feedback and large datasets for training.

### Strengths and Weaknesses

| Method                 | Strengths                                           | Weaknesses                                      |
|------------------------|---------------------------------------------------|------------------------------------------------|
| Problem-Specific      | Highly efficient for well-defined tasks           | Not reusable for different problems            |
| General Solvers       | Versatile across multiple problems                | May be less efficient than specialized methods |
| Learning-Based        | Adaptable, can improve with experience            | Requires large amounts of data                 |

Most modern AI applications utilize **hybrid approaches**, combining elements from multiple problem-solving strategies.

---

## A5.3 Classification of AI Topics

### AI Research Classification

AI problems are categorized based on:
- **The properties of the environment they address.**
- **The problem-solving approach applied.**

### Example Applications

#### **Informed Search Algorithms**
- Environment Properties: Static/Dynamic, Deterministic/Stochastic, Single/Multi-Agent.
- Problem Solving: Problem-Specific, General, Learning-Based.

#### **Constraint Satisfaction Problems (CSPs)**
- Environment Properties: Static, Deterministic, Fully Observable.
- Problem Solving: General Solvers.

#### **Board Games**
- Environment Properties: Static, Deterministic, Fully Observable, Adversarial.
- Problem Solving: General AI, Learning-Based.

#### **General Game Playing**
- Environment Properties: Dynamic, Stochastic, Partially Observable.
- Problem Solving: Learning-Based.

#### **Classical Planning**
- Environment Properties: Static, Deterministic, Fully Observable.
- Problem Solving: General Problem Solvers.

#### **Acting Under Uncertainty**
- Environment Properties: Dynamic, Stochastic, Partially Observable.
- Problem Solving: Learning-Based, General Solvers.

#### **Reinforcement Learning**
- Environment Properties: Dynamic, Stochastic, Partially Observable.
- Problem Solving: Learning-Based.

---

## A5.4 Summary

### Key Takeaways

- **AI problems** are defined by the agent model, environment properties, and performance measures.
- **Environmental properties** (observability, determinism, dynamics) influence the choice of suitable algorithms.
- **Three problem-solving approaches** exist:
  - *Problem-Specific Algorithms* (optimized for single tasks).
  - *General Problem Solvers* (flexible but potentially less efficient).
  - *Learning-Based Methods* (adaptive but data-intensive).
- **Different AI topics** require different combinations of problem-solving strategies depending on their properties.

The field of AI integrates multiple methodologies, blending rule-based systems, probabilistic reasoning, and machine learning to tackle complex real-world challenges.

