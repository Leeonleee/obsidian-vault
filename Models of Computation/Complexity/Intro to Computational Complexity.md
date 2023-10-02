# Table of Contents

# What counts as a step?
## Pseudocode
- Assignments: `a=42`
- Comaprisions: `i<j`
- Boolean formulas: `(p && q) && q`
- Mathematical operations: `a = 42x + y`

## Turing Machine
- A single transition counts as a step

# Time Complexity
$$f(n)=\text{the largest number of steps taken by the algorithm/TM on any input of length }n$$

# Most important class of languages
Define **P** to be the collection of languages $L$ that are decidable in polynomial time on **deterministic** TMs
- Read as "P" or "P Time" or "Polynomial Time" or "Deterministic Polynomial time"
- P includes all the languages decided by linear-time algorithms, quadratic time algorithms, cubic time algorithms, etc
- P is robust to certain changes, notably multiple tapes
P roughly corresponds to problems that can be realistically solved on a computer
## Examples of languages in P
- Every regular language
- Every context-free language
- Some problems, e.g.
	- DFA membership, RE membership, DFA equivalence, CFG membership, CFG emptiness
- Most problems studied in DSA

# Non-Deterministic TMs
The transition function of a NTM $N$ becomes
$$\delta:Q\times \Gamma\rightarrow P(\Gamma\times\lbrace L,R,S\rbrace\times Q)$$

e.g. $(a',L,q')\in \delta(q,a)$ means
- If $N$ is in state $q$ and reads symbol $a$ under the head, one of its possible transitions it to write $a'$, change to state $q'$ and move the head one cell to the left
- A computation of $N$ on an input $u$ is a tree, called the **computation tree**

## Accepting inputs
A NTM accepts input $u$ if some branch of the computation tree of $u$ has an accepting configuration

**Theorem:** Every NTM $N$ has an equivalent deterministic TM $D$
**Idea:** $D$ will search the computation tree of $N$
High level description of $D$:
- $D$ does a breadth-first search of $N$'s computation tree on given input
- If it finds $q_\text{accept}$, it accepts, otherwise it diverges

## Time complexity for NTMs
- An NTM $N$ is a **decider** if on every input, every branch of its computation tree halts
- The **time-complexity** of $N$ is the function $f:\mathbb{N}\rightarrow\mathbb{N}$ where $f(n)$ is the max number of steps that $N$ uses on any branch of its computation on any input length $n$
- If $f(n)=O(p(n))$ for some polynomial $p$, then $N$ runs in polynomial time

# Second most important class of languages
Define NP to be the collection of languages $L$ that are decidable in polynomial time on **nondeterministic** Turing machines
- Read as "NP" or "Nondeterministic Polynomial Time"
- All languages in P are in NP

# Graphs
A graph $G$ is a pair $(V,E)$ where $V$ is a set of vertices, and $E\subseteq V\times V$  is a set of edges
- A non-empty graph is called a **clique (completely connected)** if every pair of different nodes is connected by an edge

## CLIQUE is in NP
The CLIQUE problem:
**Input:** graph $(V,E)$ and $K\in\mathbb{Z}^+$
**Output:** "yes" if the graph contains $K$ vertices that form a clique, "no" otherwise
To show that CLIQUE is in NP, we need a polynomial time NTM that decides it

High level description of the TM
On input $(V,E),K$
1. Nondeterministically select a subset $C\subseteq V$ of $K$ vertices
	- Explores all $C$ simultaneously
2. Test whether every pair of different nodes in $C$ is connected by an edge
3. If yes, accept, else reject

# P=NP
We know that every problem P is in NP, $P\subseteq NP$, however, we don't know if they are equal