# Table of Contents
[What is an Automata?](<# What is an Automata?>)
- [Graphical Representation of Automata](<## Graphical Representation of Automata>)
[Deterministic Finite Automata](<# Deterministic Finite Automata (DFA)>)

# What is an Automata?
It's like a symbol processing program that:
- takes a *string* as input
- can only use variables with *finite* domains
	- state taking finitely many variables
- reads the input string character by character
- can test for end of input
- must decide to *accept* or *reject* the input string

## Graphical Representation of Automata
- Directed edge-labeled graph
	- Vertices represent states
	- Labeled edges $q\xrightarrow a q'$ represents transitions between states
	- The **start** state is marked with an incoming arrow
	- The **final** states are marked with an extra circle

# Deterministic Finite Automata (DFA)
A deterministic finite automaton (DFA) $M$ consists of 5 items
$$(Q,\Sigma,\delta,q_0,F)$$

where:
1. $Q$ is a finite set of **states**
2. $\Sigma$ is the **alphabet** (input alphabet)
3. $\delta:Q\times\Sigma\rightarrow Q$ is the **transition function**
	- if $\delta(q,a)=q'$ we write $q\xrightarrow a q'$ , called a **transition**
4. $q_0\in Q$ is the **start state** (initial state)
5. $F\subseteq Q$ is the set of **final states** (accepting states)

## Languages Recognised by $M$
- The automaton accepts the strings that label a path from the start state to a final state
- The **language recognised by** $\textbf{M}$ (the language of $M$) written $L(M)$ is the set of strings the automaton accepts
### Math definition
- A **run** (aka computation) of $M$ on $w=w_1w_2\cdots w_n$ is a sequence of transitions $q_0\xrightarrow w_1 q_1\xrightarrow w_2 q_2\xrightarrow w_3\cdots\xrightarrow {w_n} q_n$ where $q_0$ is the starting state
- The run is **accepting** if $q_n\in F$
- If $w$ has an accepting run, then we say $M$ **accepts** $w$
- 

