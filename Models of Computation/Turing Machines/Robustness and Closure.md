# Table of Contents


---
Turing machines are fairly robust
- variations and extensions of the basic model do not change the languages that can be recognised
- Call our Turing machines *basic TMs*
	- Deterministic
	- Single doubly-infinite tape
	- Can move left, right or stay
- 2 machines are **equivalent** if they recognise the same language

# Must move TMs
- Basic TMs can move left, right or stay put in one step
- Sipser's variation doesn't allow 'stay'. Call them **must-move TMs**
- Every must-move TM is a basic TM
- Is every basic TM equivalent to a must-move TM?
**Theorem:** Every basic TM is equivalent to a must-move TM
**Proof idea:** simulate a basic TM by a must-move TM
- Replace each $S$-transition by an $R$-transition followed by an $L$-transition
- e.g. replace
```
q_i a b S q_j

with

q_i a b R q_i,j
q_i ** L q_j
```

# Left-bounded TM
- The head starts on the left-most square of the tape, with the head on the first letter of the input
- If the transition function suggests to move left when the head is already at the left=most position, the head stays
**Theorem:** Every basic TM is equivalent to a left-bounded TM
**Proof idea:** simulate a basic TM by a left-bounded one
- Split the left-bounded tape into 2 tracks: upper and lower
- Upper track represents the right half of the tape (from the initial head position)
- Lower track represents the left half of the tape
- An extra state component keeps track of the half in which the head currently is in

# Multitape TM
- Has multiple tapes, each with its own head for reading and writing
- Initially the input appears on tape 1, and the others start out blank
- The heads move simultaneously
- The type of the transition function of a $k$-tape TM becomes
$$\delta:Q\times\Gamma^k\rightarrow\Gamma^k\times\lbrace L,R,S\rbrace^k\times Q$$
- Every basic TM is a multi-tape TM ($k=1$)
- Is every multi-tape TM equivalent to a basic TM?
**Theorem:** Every multitape TM $M$ has an equivalent basic TM $B$
**Proof idea:**
- Split the tape into $2k$-many tracks of the single tape of $B$
- For each tape of $M$, use one track to store tape contents, and one track to mark head position on that tape
- Each transition of $M$ is simulated by a series of transitions of $B$
# Summary
1. The set of recognisable languages doesn't change if one makes certain variations
	- e.g. more tapes
2. The set of decidable languages doesn't change if one makes certain variations
	- e.g. more tapes
	- This is because the simulations do not introduce diverging computations

# Closure Properties
## Union
The union of decidable languages is decidable
**Proof:** Let $L_1$ and $L_2$ be languages that are decided by TMs $M_1$ and $M_2$ respectively
We construct a TM that decides $L_1\cup L_2$ as follows:
```
def L1_union_L2(x):
	if M1(x):
		return 1
	if M2(x):
		return 1
	return 0
```

## Complement
The complement of a decidable language is decidable
**Proof:** Suppose that TM $M$ decides language $L$. Build a TM from $M$ as follows
```
def Complement_M(X):
return not M(x)
```

A language is decidable exactly when it and its complements are recognisable
**Proof:**
- Follows from the closure properties of decidable languages
- If $M_1$ recognises $L$ and $M_2$ recognises $\Sigma^*\backslash L$ , we construct a decider for $L$ as follows:
	- On input $w$
	- Run $M_1$ and $M_2$ on parallel on $w$
		- Use one tape for each machine
		- At each step, simulate $M_1$ on tape 1, and $M_2$ on tape 2
	- If $M_1$ ever accepts, then accept; and if $M_2$ ever accepts, the reject
- Exactly one of $M_1$ or $M_2$ must eventually accept $w$, we we have built a decider for $L$
- 