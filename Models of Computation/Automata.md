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



