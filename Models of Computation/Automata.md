# Table of Contents
[What is an Automata?](<# What is an Automata?>)
- [Graphical Representation of Automata](<## Graphical Representation of Automata>)
[Deterministic Finite Automata](<# Deterministic Finite Automata (DFA)>)
[Nondeterministic Finite Automata](<# Nondeterministic Finite Automata>)
[Comparing NFAs and DFAs](<# Comparing NFAs and DFAs>)
[Regular Expressions to NFAs](<# Regular Expressions to NFAs>)

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
- A **run** (aka computation) of $M$ on $w=w_1w_2\cdots w_n$ is a sequence of transitions $q_0\xrightarrow {w_1} q_1\xrightarrow {w_2} q_2\xrightarrow {w_3}\cdots\xrightarrow {w_n} q_n$ where $q_0$ is the starting state
- The run is **accepting** if $q_n\in F$
- If $w$ has an accepting run, then we say $M$ **accepts** $w$
- The set $L(M) = \lbrace w\in\Sigma^*:M\text{ accepts } w\rbrace$ is the **language recognised by** $\textbf M$ ( the language of $M$)

## Regular Languages
- A language $L\subseteq\Sigma^*$ is called **regular** if $L = L(M)$ for some DFA $M$
	- $M$ must accept all strings in $L$ and reject all strings (in $\Sigma^*$) that are not in $L$

## Designing Automata Tips
- Build automata out of other automata using closure properties of regular languages
- If you have DFA for $L_1,L_2$ then you can get DFA for
	1. $\Sigma^*\backslash L_1$ 
	2. $L_1\cup L_2$
	3. $L_1L_2$
	4. $(L_1)^*$

### Regular Languages Closed Under Complementation
**Theorem**
- If $L$ is regular, then $\Sigma^*\backslash L$ is regular
**Idea**
- Swap final and non-final states in a DFA for $L$
	- Given DFA $M=(Q,\Sigma,\delta,q_0,F)$ recognising $L$
	- We build a DFA $M'$ recognising $\Sigma^*\backslash L$ as follows:
		- Define $M'=(Q,\Sigma,\delta,q_0,F')$ where $F'=Q\backslash F$
## Important Questions about DFA
1. **Membership problem**
	- Input: DFA $M$, string $w$
	- Output: decide if $w\in L(M)$
2. **Non-emptiness problem**
	- Input: DFA $M$
	- Output: decide if $L(M)\neq\emptyset$
3. **Equivalence problem**
	- Input: DFAs $M_1,M_2$
	- Output: decide if $L(M_1)=L(M_2)$
### Membership problem
```
def membership(M,w):
state = q_0
while not end_of_input(w):
	x = get_char(w)
	state = δ(state,x)
if state in F:
	return "Yes" # M accepts x
else:
	return "No" # M does not accept x
```

# Nondeterministic Finite Automata
- Nondeterminism: situations where the next state of a computation is not uniquely determined by the current state and current input
- A **nondeterministic finite automaton (NFA)** is like a DFA, except that states can have *zero*, *one*, or *more* outgoing transitions on the same input symbol
- A string is *accepted by an NFA* if it labels some path from the start state to a final state
- In an NFA, a string can label 0, 1, or more paths
- NFAs are good for specifying languages in the form "the string has $x$ as a substring"

## Definition
A nondeterministic finite automaton (NFA) $M=(Q\Sigma,\delta,q_0,F)$ is the same as a DFA, except that
$$\delta:Q\times\Sigma_\epsilon\rightarrow P(Q)$$
called the **transition relation**
- If $q'\in\delta(q,a)$ we write $q\xrightarrow a q'$, called a **transition**
- Here $\Sigma_\epsilon=\Sigma\cup\lbrace\epsilon\rbrace$ 
- We allow **epsilon-transitions**
	- This amounts to transitions that don't consume the next input symbol
### Maths definition
Formalises the idea that an NFA $M$ describes the language $L(M)$ of all strings that label paths from the start state to a final state
- A **run** (computation) of an NFA $M$ on string $w$ is a sequence of transitions $q_0\xrightarrow {y_1}q_1\xrightarrow {y_2} q_2\cdots\xrightarrow {y_m} q_m$ such $q_0$ is the start state, each $y_i\in\Sigma_\epsilon$ and $w=y_1y_2\cdots y_m$
- The run is **accepting** if $q_m\in F$
- If $w$ has at least one accepting run, then $w$ is **accepted** by $M$
- The language **recognised** by $M$ is $L(M)=\lbrace w\in\Sigma^*:w\text{ is accepted by }M\rbrace$

# Comparing NFAs and DFAs
1. In a DFA, every input has exactly one run. The input string is accepted if this run is accepting
	- an input of a DFA may have no runs, but we don't draw rejecting
2. In an NFA, an input may have zero, one or more runs. The input string is accepted if at least one of its runs is accepting
3. For every DFA $M$, there is an NFA $N$ such that $L(M) = L(N)$
	- $q'=\delta(q,a)$ in $M$ becomes $\lbrace q'\rbrace=\delta(q,a)$ in $N$
	- DFA is an NFA where there is no nondeterminism

# Regular Expressions to NFAs
## Theorem
For every regex $R$ there is an NFA $N$ such that $L(R)=L(N)$
- Since regexes are built recursively, this construction is also recursive
	- Base cases: $R=\emptyset, R=\epsilon, R=a$ for $a\in\Sigma$
		- We must show that each of these languages is recognised by some NFA
	- Recursive cases: $R=(R_1|R_2), R=(R_1R_2)$ and $R=R_1^*$
		- We must show that if $N_1, N_2$ are NFAs, then there are NFAs recognising $L(N_1\cup N_2), L(N_1)L(N_2)$ and $L(N_1)^*$
### Base cases
1. $L(\emptyset)=\emptyset$
	![NFA Base Case 1 Diagram|100](NFA_base_case_1.png) 
2. $L(\epsilon)={\epsilon}$
![NFA Base Case 2 Diagram|100](NFA_base_case_2.png)


3. $L(a) ={a}$
 ![NFA Base Case 3|100](NFA_base_case_3.png)
### NFAs are closed under union
#### Lemma
If $N_1, N_2$ are NFAs, there is an NFA $N$ recognising $L(n_1)\cup L(n_2)$
- Given NFAs $N_i=(Q_i,\Sigma,\delta_i,q_i,F_)