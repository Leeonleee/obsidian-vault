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
| --- | --- | ----------- |
| 0   | 0   | 0           |
| 0   | 1   | 1           |
| 1   | 0   | 0           |
| 1   | 1   | 1           |

- An **assignment** is a function $\alpha$ from atoms to truth values
	- i.e. "row of a truth table"
- On three variables, there are $2^3=8$ assignments
- On four variables, there are $2^4=16$ assignments
- The truth value $tv(F,\alpha)$ of a formula $F$ under assignment $\alpha$ is defined by the following recursive process:
	TV1. $tv(p,\alpha=\alpha(p)$ for every atom $p$
	TV2. $$tv(\neg F,\alpha)=\begin{cases}0\text{ if }tv(F,\alpha)=1\\1\text{ if }tv(F,\alpha)=0\end{cases}$$
	TV3.$$tv(F\wedge G,\alpha)=\begin{cases}1\text{ if }tv(F,\alpha)\text{ and }tv(G,\alpha)=1\\0\text{ otherwise }\end{cases}$$
	TV4.$$tv(F\vee G,\alpha)=\begin{cases}1\text{ if }tv(F,\alpha)\text{ or }tv(G,\alpha)=1\\0\text{ otherwise }\end{cases}$$
This is a shorter way to code $tv(F,\alpha)$$
	TV1. $tv(p,\alpha)=\alpha(p)$ for atoms $p$
	TV2. $tv(\neg F,\alpha)=1-tv(F,\alpha)$
	TV3. $tv(F\wedge G, \alpha)=\text{min}\lbrace tv(F,\alpha),tv(G,\alpha)\rbrace$
	TV3. $tv(F\vee G, \alpha)=\text{max}\lbrace tv(F,\alpha),tv(G,\alpha)\rbrace$

## Terminology
- Sometimes shorten $tv(F,\alpha)$ to $\alpha(F)$
	- e.g. $tv(F\wedge G,\alpha)=1$ can be written as $\alpha(F\wedge G) = 1$
- If $\alpha(F)=1$, we say
	- $\alpha$ makes $F$ true
	- $\alpha$ satisfies $F$
	- $\alpha$ models $F$
	- Also written as $\alpha\vDash F$
- The symbol $\vDash$ is called the **double-turnstile**

## Other symbols
1. $\top$ and $\bot$ are formulas
	- Called the **propositional constants**
2. If $F,G$ are formulas, then so are $(F\rightarrow G)$ and $(F\leftrightarrow G)$
	- $\rightarrow$ is called the **conditional** (aka implication)
	- $\leftrightarrow$ is called the **bi-conditional** (aka bi-implication)
3. Semantics
	- $\top$ is always true, $\bot$ is always false
	- $(F\leftrightarrow G)$ is true if and only if $F$ and $G$ have the same truth values

| $F$ | $G$ | $(F\rightarrow G)$ |
| --- | --- | ------------------ |
| 0   | 0   | 1                  |
| 0   | 1   | 1                  |
| 1   | 0   | 0                  |
| 1    |   1  |      1              |
## Connection with natural language
1. "or" in English
	- Sometimes it's inclusive ("I will sing or dance"), so we write $p\vee q$
	- Sometimes it's exclusive ("I will arrive now or later") so we write $(p\vee q)\wedge \neg(p\wedge q)$
	- and sometimes it's unclear ("your error is in the program or the data")
2. "and" in English
	- "He throw the stone and the window broke"
	- "The window broke and he threw the stone"
	- Different meanings in English but the same in formal logic
# Validity
A formula $F$ is **valid** if every assignment satisfies $F$
- i.e. if its truth table always has value 1
- Valid formulas represent logical laws
	- In the same way that $x+0=x$ is an arithmetic law

# Satisfiable
A formula $F$ is **satisfiable** if at least one assignment satisfies $F$
- i.e. if it's truth table has at least one 1

## Satisfiability problem
- To decide if a given propositional formula $F$ is satisfiable
- Can be solved by checking all rows of the truth table for $F$
	- Suppose $F$ has $n$ atoms, then the truth table has $2^n$ rows
	- This algorithm is $O(2^n)$
- if the satisfiability problem is in P, then P=NP