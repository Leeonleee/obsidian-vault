# Table of Contents


# Encodings
- The input to a TM is always a string, but working other objects can be useful over $\Sigma$
- Almost any object can be encoded as a string
- Can be written as
	- $<X>$ in Sipser
	- `str(X)` in Python
	- or just as $X$
- The encoding of more than 1 object can be written as
	- $<X,Y>$
	- $X;Y$

# Encoding Numbers
The number $n\in \mathbb{Z}^+_0$ can be encoded as a string in some fixed base
e.g. The number 3 is encoded by the string:
- 111 in unary encoding
- 11 in binary
- 10 in ternary
- 3 in decimal
- etc
- Integers can be encoded as a string by adding a symbol for the sign

# Encoding sequences of strings
List the strings in order, separated by a new alphabet symbol called a **delimiter**
e.g.
- 00,1,000,10
- The delimiter here is the comma, but any other symbol can be used

# Encoding TMs
Let $Source_M$ denote the string encoding of a TM $M$
You can think that it is the source code in any general purpose programming language

# Encoding graphs
Use things like adjacency lists

# Decidability
- If you run a TM on an input, one of three things can occur
	1. The TM eventually halts in an accept state
	2. The TM eventually halts in a reject state
	3. The TM doesn't enter a halting state (it **diverges**)
- A TM is a decider if it halts on every input
- A language $L$ is called **Turing-decidable** if $L=L(M)$ for a decider $M$

# Decidable problems about automata
## Membership problem for DFAs
The problem is the language
$$L_\text{DFA-acceptance}=\lbrace D,w | D\text{ is a DFA that accepts }w\rbrace$$
$$L(D)=\lbrace w:w\in L(D)\rbrace$$
- $w$ is the input string over the DFA $D$
- This problem is decidable
- This is a high level description of a decider for this language
	1. Simulate $D$ on word $w$
	2. If $D$ ends in an accepting state, accept, else reject
---
1. Membership/acceptance problems for DFA, NFA, RE, and CFG are decidable
2. The emptiness problems for DFA, NFA, RE, and CFG are decidable
3. The equivalence problems f0r DFA, NFA, and RE are decidable
	- The equivalence problem for CFGs is not decidable

# Acceptance problem for TMs

The acceptance problem for TMs is the language
$$L_\text{TM-acceptance}=\lbrace M,w|M\text{ is a TM that accepts }w\rbrace$$
- This language is recognisable
- To show this, build a TM $U$ that recognises it
High level description of $U$
1. On input $M,w:$
	1. simulate $M$ on $w$
	2. accept if $M$ enters $q_\text{accept}$, reject if $M$ enters $q_\text{reject}$, if $M$ doesn't halt, $U$ doesn't
- The TM $U$ is called a **universal TM** since it can do what any other TM can do

## Implementation level description of $U$
- Tape 1 holds the transition function $\delta_M$ of the input TM $M$
- Tape 2 holds the simulated contents of $M$'s tape
- Tape 3 holds the current state of $M$, and the current position of $M$'s tape head
- $U$ simulates $M$ on input $x$ one step at a time
	- In each step it updates:
		- $M$'s state
		- simulated tape contents
		- head position as dictated by $\delta_M$
	- If $M$ halts and accepts, or halts and rejects, then $U$ does the same
## Universal TM
- This is the blueprint for an interpreter, it takes TMs as input and executes them
- It's similar to a Python interpreter written in Python
	- A Python program that takes Python programs as input and executes them
- They are analogous to a computer

This is **NOT** a decider

The **acceptance problem** for TMs is not decidable because 
$$L_\text{TM-acceptance}=\lbrace M,w|M\text{ is a TM that accepts }w\rbrace$$
- TM $U$ recognises the acceptance problem for TM, but it doesn't decide it