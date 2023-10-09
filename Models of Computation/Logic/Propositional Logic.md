# Similar to algebra
- Algebra is for expressions and reasoning about arithmetic
- Propositional logic is for expressing and reasoning about propositions (aka statements)

| Name         | Propositional Logic               | Algebra                    |
| ------------ | --------------------------------- | -------------------------- |
| variables    | $p,q,r,\dots$                     | $x,y,z,\dots               |
| values       | $0,1$                             | $1,2,3,\dots               |
| operations   | $\vee,\wedge,\neg$                | $+,-,\times,\dots$         |
| expressions  | $\neg(p\wedge q)$                 | $1+(x-y)$                  |
| equivalences | $p\wedge q = q\wedge p$           | $x + y = y + x$            |
| evaluation   | $\neg(p\wedge q)=0$ if $p,q=1$    | $x\times y=3$ if $x=1,y=3$ |
| deduction    | $p\wedge q$ true implies $p$ true | $x=2$ implies $x\times x=4$                           |
- Can be written in post programming languages
	- In Python and Java these are called Boolean expressions
	- Usually used as conditions for control flow

# Propositions
- A **proposition** is a sentence that declares a fact that is either true, or false, but not both

# Syntax
- Java and Python each have their own syntax for writing propositional formulas
- We will use another syntax standard in computer science and maths

| Name           | Propositional Logic | Python              | Java                |
| -------------- | ------------------- | ------------------- | ------------------- |
| conjunction    | $\wedge$            | `and`               | `&&`                |
| disjunction    | $\vee$              | `or`                | `||`                |
| negation       | $\neg$              | `not`               | `!`                 |
| implication    | $\rightarrow$       |                     |                     |
| bi-implication | $\leftrightarrow$   | `==`                | `==`                |
| top/verum      | $\top$              | `True`              | `true`              |
| bottom/falsum  | $\bot$              | `False`             | `false`             |
| atoms          | $p,q,r,\dots$       | Boolean variables   | Boolean variables   |
| formulas       | $F,G,H,\dots        | Boolean expressions | Boolean expressions |

## Rules
Syntactic rules for defining formulas of Propositional logic
**Definition**
- An **atom** is a variable of the form $p_1,p_2,p_3,\dots,p,q,r$
- A **formula** is defined by the following recursive process:
	F1. Every atom is a formula
	F2. If $F$ is a formula, then $\neg F$ is a formula
	F3. If $F,G$ are formulas, then so are $(F\vee G)$ and $(F\wedge G)$
**Reading guide**
- $\neg$ is read "it is not the case that"
- $\wedge$ is read "and"
- $\vee$ is read "or"

- A formula can also be represented as a tree
- 

**Example**
- Build $(p\wedge(q\vee\neg p))$ using the definition
1. By F1., $p,q$ are formulas
2. By F2. $\neg p$ is a formula
3. By F3. $(q\vee\neg p)$ is a formula
4. By F3. $(p\wedge(q\vee\neg p))$ is a formula

# Syntax 2
1. Specifies what we mean by a propositional formula
2. Allows one to design algorithms that process/manipulate formulas using recursion
	1. The base case is rule 1 of the definition
	2. The recursive cases are rules 2 and 3
3. One can prove things about propositional formulas and about code that processes formulas

- Use abbreviations:
	- $(F_1\vee F_2\vee F_3)$ instead of $((F_1\vee F_2)\vee F_3)$
	- $(F_1\wedge F_2\wedge F_3)$ instead of $((F_1\wedge F_2)\wedge F_3)$

## Reading logical formulas
- It's not always grammatically correct to read formulas by inserting the names of the symbols
e.g. 
- We read $p\wedge q$ as "p and q" and $\neg p$ as "not p"
- But if we know $p$ stand for "The earth is flat" and $q$ stands for "The earth is round"
- Then we can read $p\wedge q$ as "The earth is flat and the earth is round" or "The earth is flat and round"
- We don't read $\neg p$ as "not the earth is flat", but rather "it is not the case that the earth is flat", or "the earth is not flat"

# Semantics
- How you derive the value of a formula based on the values of its atomic subformulas
- The elements of the set $\lbrace 0,1\rbrace$ are called **truth values**
- Read $1$ as "true", $2$ as "false"
- After we assign truth values to atoms, we can give truth values to formulas
- We only need to give rules for each connective $(\wedge, \vee, \neg)$

## Truth tables
The formula $\neg F$ is true if and only if the formula $F$ is false

| $F$   | $\neg F$ |
| --- | -------- |
| 0   | 1        |
| 1   | 0         |

The formula $(F\wedge G)$ is true if and only if both formulas are true

| $F$ | $G$ | $(F\wedge G)$ |
| --- | --- | ------------- |
| 0   | 0   | 0             |
| 0   | 1   | 0             |
| 1   | 0   | 0            |
| 1   |  1   | 1              |

The formula $(F\vee G)$ is true if and only if either or both formulas are true

| $F$ | $G$ | $(F\vee G)$ |
| --- | --- | ------------- |
| 0   | 0   | 0             |
| 0   | 1   | 1             |
| 1   | 0   | 1            |
| 1   |  1   | 1              |