## A4. Introduction: Rational Agents
---

## A4.1 Systematic AI Framework

### **Systematic AI Framework Overview**
Artificial Intelligence (AI) systems are applied to a wide variety of challenges. The goal is to design systems that act rationally in different environments. The study of AI has historically focused on four approaches:
- **Thinking like humans**
- **Thinking rationally**
- **Acting like humans**
- **Acting rationally**

This lecture formalizes a systematic framework that:
- Captures the diversity of challenges in AI
- Includes an entity (agent) that interacts with an environment
- Provides criteria to evaluate whether the agent is acting rationally

### **Agent-Environment Interaction**
An AI system is typically modeled as an *agent* interacting with an *environment* through a set of mechanisms:
- **Agent components:**
  - *Sensors:* Detect observations from the environment
  - *Actuators:* Perform actions that influence the environment
  - *Agent Program:* The logic controlling the agent’s behavior
- **Environmental components:**
  - *Observations:* The information the agent perceives
  - *Actions:* The decisions made by the agent
  - *Performance Measure:* A criterion used to evaluate the agent's effectiveness
  - *Agent Function:* A mathematical function mapping observations to actions

The agent's goal is to maximize its performance measure by selecting the best possible actions based on its observations.

### **Formalizing an Agent’s Behavior**
An agent can be formally described in two ways:
1. **As an agent program:** The internal structure of the agent, including:
   - How it represents information internally
   - How it processes observations to produce actions
   - How computations occur within the physical architecture

2. **As an agent function:** A more abstract characterization that:
   - Maps a sequence of observations to a probability distribution over actions
   - Provides a formal mathematical model of agent behavior

---

## A4.2 Example: The Vacuum Agent

### **Vacuum Domain**
The *Vacuum Cleaner Agent* is a simple AI system used to illustrate the concepts of agents and environments.

#### **Performance Measure Influences:**
- Dirt levels (how clean the environment remains)
- Noise levels (if the vacuum makes excessive noise)
- Energy consumption (efficiency in power usage)
- Safety (avoiding collisions or damage)

### **Vacuum Agent: Sensors and Actuators**
- **Sensors:** Cliff sensors, bump sensors, wall sensors, battery charge sensor, WiFi module
- **Actuators:** Wheels, cleaning system

### **Vacuum Agent: Observations and Actions**
- **Observations:**
  - Current location
  - Dirt level of the current room
  - Presence of humans
  - Battery charge

- **Actions:**
  - Move to next room
  - Move to base
  - Vacuum
  - Wait

### **Vacuum Agent: Agent Program**
The logic controlling the vacuum cleaner’s behavior is described by the following pseudocode:

```python
 def vacuum_agent([location, dirt_level, owner_present, battery]):
     if battery <= 10%:
         return move_to_base
     elif owner_present == True:
         return move_to_next_room
     elif dirt_level == 'dirty':
         return vacuum
     else:
         return move_to_next_room
```

### **Vacuum Agent: Agent Function**
The agent function determines the vacuum agent’s behavior over time.

| Observation Sequence | Action |
|----------------------|--------|
| ⟨[blue, clean, False, 100%]⟩ | Move to next room |
| ⟨[blue, dirty, False, 100%]⟩ | Vacuum |
| ⟨[blue, clean, True, 100%]⟩ | Move to next room |
| ⟨[blue, clean, False, 100%], [blue, clean, False, 90%]⟩ | Move to next room |
| ⟨[blue, clean, False, 100%], [blue, dirty, False, 90%]⟩ | Vacuum |

---

## A4.3 Rationality

### **Evaluating Agent Functions**
A fundamental question in AI is: *What is the right agent function?*
The answer depends on:
- The agent’s performance measure (utility, reward, or cost)
- The environment in which the agent operates

### **Definition of Perfect Rationality**
An agent is *perfectly rational* if, for each possible observation sequence, it selects an action that **maximizes the expected value of future performance** given:
- Available information from observation history
- Knowledge of the environment’s behavior

### **Perfect Rationality of the Vacuum Agent**
To determine if the vacuum agent is perfectly rational, we must examine:
- Whether actions reliably have the intended effect
- Whether the initial state of the environment is known
- Whether new dirt can appear while the agent operates

#### **Effect of Different Performance Measures:**
1. **If the performance measure is `+1 utility` for cleaning a dirty room:**
   - The vacuum agent is **perfectly rational** in an environment where actions and observations are reliable, and the world changes only through the agent’s actions.

2. **If the performance measure is `-1 utility` for each dirty room per time step:**
   - The vacuum agent is **not perfectly rational**, as it does not optimize long-term cleanliness.

3. **If the environment allows rooms to spontaneously become dirty:**
   - The vacuum agent is **not perfectly rational**, as it does not proactively address potential future dirt accumulation.

### **Discussion on Rationality**
- *Perfect rationality ≠ Omniscience*: An agent cannot achieve perfect results if it lacks complete information.
- *Perfect rationality ≠ Perfect future prediction*: Environmental uncertainty and stochastic effects limit achievable utility.
- *Bounded Rationality*: Due to computational limits, real-world agents cannot always achieve perfect rationality.

---

## A4.4 Summary

### **Key Takeaways**
- AI systems are commonly modeled as *rational agents* interacting with an *environment*.
- Agents process *observations* from sensors and perform *actions* via actuators.
- The *agent function* maps observation sequences to actions.
- A rational agent aims to maximize a *performance measure*.
- *Perfect rationality* requires selecting optimal actions based on available information, but real-world constraints often lead to *bounded rationality*.

---

