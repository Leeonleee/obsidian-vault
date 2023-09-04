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
### Removing Epsilon Rules
1. Find all variables $A^+\xRightarrow + \epsilon$ ('nullable variable')
2. if $B\rightarrow AcA$ is in $R$, and $A\xRightarrow + \epsilon$, then add the rules $B\rightarrow cA|Ac|c$
#### Pseudocode
Given $G=(V,\Sigma,R,S):$
1. Let $R'=\emptyset$
2. Put all the non epsilon rules from $R$ into $R'$
3. Repeat the following until $R'$ doesn't change:
	- If $A\xRightarrow +\epsilon$  in $R$, and $B\rightarrow \alpha$ is a rule in $R'$ where $A$ occurs in $\alpha$
	- Then add to $R'$ all the rules in which some occurrence of $A$ in $\alpha$ are removed but don't add $B\rightarrow \epsilon$
4. If $S\xRightarrow+\epsilon$ in $R$ then add $S\rightarrow\epsilon$ to $R'$
Return $G'=(V,\Sigma, R', S)$

### Removing Unit Rules
1. Find all pairs $A,B$ such that $A\xRightarrow + B$
2. If $A\xRightarrow + B$ and $B\rightarrow aBcD$ then add $A\rightarrow aBcD$
#### Pseudocode
Given $G = (V,\Sigma,R,s)