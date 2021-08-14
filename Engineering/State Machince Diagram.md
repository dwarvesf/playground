---
tags: modeling, state-machine
---

### What
State Machine Diagram (SMD) represents the state of an object from the creation of an object until the object is destroyed or terminated.

keyword: `transactional data`

### Why
An object can go through a various of states during its lifespan. SMD captures the behavior from the systems. The behavior can be visualized from a class, subsystems, package or even the whole system. 

Only one state operates during the active span. The diagram works through the transition state of its object.

### Problem & Resolution
If an event/ action gets replicated too many times, data cannot be fetched. The system crashes and the workflow gets interrupted, since the system cannot recognize if its action A or action B.

State machine Diagram approaches things in `state`.

It defines which action can perform during that state. Hence, the system won't recognize if that action belongs to another state; and reduces the risk of system crashing due to several actions during one state. 

### To sum up
- 1 objects
- Many actions / Many states

### Example
Visualize a SMD for Gaming State.
Gamers will go through 3 states
- Game Running
- Game Pause
- Game Over

![[state-machine.jpeg]]

- start
- end

-> fortress/ turing alley
- tsao co nhieu loai diagram
	- serve muc dich gi
	- use case cho moi diagram

---
Citation:
- [Chapter 5 State Machine Diagrams | System Analysis (fhv.at)](https://homepages.fhv.at/thjo/lecturenotes/sysan/state-machine-diagrams.html)