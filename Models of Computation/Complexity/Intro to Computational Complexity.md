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
The transition function of a ND TM $N$ becomes
$$\delta:Q\times \Gamma\rightarrow P(\Gamma\times\lbrace L,R,S\rbrace)$$