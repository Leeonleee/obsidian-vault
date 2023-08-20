# Table of Contents

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

**Simulate $N_1$ or $N_2$**
- Given NFAs $N_i=(Q_i,\Sigma,\delta_i,q_i,F_i)$ construct NFA $N$ that guessing which of $N_1$ or $N_2$ to simulate
- $N$ has states $Q_1\cup Q_2\cup \lbrace q_0\rbrace$ so that it can simulate $N_1, N_2$
- $N$ guesses from $q_0$ whether to go to the start state of $N_1$ or $N_2$
	- $q_0$ is just a state that will guess between $N_1$ or $N_2$

**Simulate $N_1$ followed by $N_2$**
- Given NFAs $N_i=(Q_i,\Sigma,\delta_i,q_i,F_i)$ construct NFA $N$ that guesses how to break the input into 2 pieces, the first accepted by $N_1$ and the second by $N_2$
- $N$ has states $Q_1\cup Q_2$ so that it can simulate $N_1$ and $N_2$
- At some point when $N_1$ is in a final state, guess that it is time to move to the start state of $N_2$
	- Final states in $N_1$ are no longer final, but rather go to the initial states of $N_2$

**Repeatedly simulate $N_1$**
- Given NFAs $N_i=(Q_i,\Sigma,\delta_i,q_i,F_i)$ construct NFA $N$ that guesses how to break the input into pieces, each of which is accepted by $N_1$
- $N$ has states $Q\cup\lbrace q_0 \rbrace$ and extra transitions from final states of $N_1$ to the initial state of $N_1$
- The new state $q_0$ is ensured that $\epsilon$ is accepted (language always contains the empty string)
	- $q_0$ is before the initial state
	- Final states go back to the initial state
# NFA to NFA without $\epsilon$ Transitions
For every NFA $N$, there is an NFA $M$ without $\epsilon$ transitions such that $L(N)=L(M)$

$M$ **skips over $\epsilon$ transitions of $N$**
- $M$ is like $N$, but we remove all the $\epsilon$-transitions and add new transitions and final states
- Write $q\rightsquigarrow r$  to mean that $N$ can go from $q$ to $r$ using zero or more $\epsilon$-transitions
- When is $q$ a final state of $M$?
	- if $q\rightsquigarrow r$ and $r$ is a final state of $M$
	- Basically a state can transition to a final state using only $\epsilon$-transitions, it also becomes a final state
- When is $q\xrightarrow a s$ a transition of $M$?
	- if $q\rightsquigarrow r$ and $r\xrightarrow a s$
	- Basically if $q$ takes $\epsilon$-transitions to $r$, but $r$ takes $a$ to $s$, then its a transition on $M$
# NFA without $\epsilon$ Transitions to DFA
For every NFA $N$ without $\epsilon$-transitions, there is a DFA $M$ such that $L(M)=L(N)$

**Subset construction**
- How do you simulate the NFA if you are pretending to be a DFA?
	- Keep track of the set of possible states that the NFA is in
- When do you accept?
	- If at least one state you're tracking is an accepting state of the NFA
- Given NFA $N=(Q,\Sigma,\delta,q_0,F)$ without $\epsilon$-transitions, the subset construction builds a DFA $M$:
	- every set $X\subseteq Q$ is a state of $M$
	- the alphabet is $\Sigma$
	- for a state $X\subseteq Q$ of $M$, define $\delta'(X,a)=\bigcup_{q\in X}\delta(q,a)$ 
	- the initial state of $M$ is the set $\lbrace q_0\rbrace$
	- for a state $X\subseteq Q$ of $M$, put $X$ into $F'$ if $X$ contains an accepting state of $N$
		- all sets that contain a final state of the NFA

# DFA to Regular Expressions
For every DFA $M$ there is a regular expression $R$ such that $L(M)=L(R)$

- Convert $M$ into a *generalised nondeterministic f*