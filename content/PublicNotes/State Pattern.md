---
title: State Pattern
tags: Public
Aliases:
Date created: 2024-03-22 10:10
---

The state is a behavioural design pattern that let's an object alter it's behaviour when it's internal state changes. 

## Finite State Machine
A system in which:
- There's a fixed set of states
- There can be only one active state at a time
- A sequence of inputs or events is sent to the machine
- Each state has a set of transitions - defining what state it can change to after what input

## State Pattern

This pattern calls for representing each state as a class and extracting all state-specific behaviour into these classes. Each of them should follow the same `State` interface

The original object (called *\context*) stores a reference to one of the state objects and delegates work.

To transition the context into another state, replace the object with another that represents new state.

### Difference with [[Strategy Pattern]]
In the State pattern, the particular states may be aware of each other and initiate transitions from one state to another, whereas strategies almost never know about each other.

## Usage
### When to Use
- When an object behaves differently depending on its state, there's considerable number of states and the state-specific code is prone to changes
- When you need to use massive conditionals that alter class behaviour 
- When there's a lot of duplicated code across similar states and transitions of condition-based state machine

### When not to Use
- When a state machine has not a lot of states or rarely changes