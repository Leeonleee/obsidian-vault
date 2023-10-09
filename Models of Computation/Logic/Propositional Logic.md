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

## Syntax
1. Specifies what we mean by a propositional formula
2. Allows one to design algorithms that process/manipulate formulas using recursion
	1. The base case is rule 1 of the definition
	2. The recursive cases are rules 2 and 3
3. One can prove things about propositional formulas and about code that processes formulas


