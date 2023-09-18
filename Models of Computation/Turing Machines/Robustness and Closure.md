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
- Split the left-bounded tape into 2 tracks