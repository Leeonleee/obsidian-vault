# Table of Contents

# Normal Forms
- An object can have more than one representation
- A norma form is a standard representation of objects
- e.g.
	- Objects = formulas in logic (Disjunctive Normal Form)
	- Objects = relational databases (Boyce-Codd Normal Form)
	- Objects = context-free languages (Chomsky Normal Form)
# Chomsky Normal Form
A grammar is in CNF if every rule is in one of these forms:
1. $A\rightarrow BC$ $(A, B, C$ are any variables, except that neither $B$ nor $C$ is the start variable $)$
2. $A\rightarrow a(A$ is any variable and $a$ is a terminal$)$
3. In addition, we permit $S\rightarrow \epsilon$ where $S$ is the start variable
- Don't allow rules like $A\rightarrow0A1$ and $A\rightarrow B$ and $A\rightarrow ab$
- Parse trees of a grammar in CNF are binary trees
## Turning CFG into CNF
Rules we want to eliminate:
1. **Epsilon rule:** rules in the form $A\rightarrow \epsilon$
2. **Unit rule:** rules in the form $A\rightarrow B$

Transforming a grammar $G$ into an equivalent grammar $G'$ such that:
1. $G'$ has no epsilon rules except perhaps $S\rightarrow\epsilon$
2. $G'$ has no unit rules
- This is done in 2 steps