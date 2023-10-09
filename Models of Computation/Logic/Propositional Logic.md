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