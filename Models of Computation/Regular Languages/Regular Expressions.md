# Table of Contents
- [Three Abstractions](<# Three Abstractions>)
- [Decision Problems](<# Decision Problems>)
- [Terminology](<#Terminology>)
- [Summary](<#Summary>)
- [Syntax](#Syntax)
- [Semantics](#Semantics)
- [Recursion](#Recursion)
- [Languages that are specified using regexes](<# Languages that are specified using regexes>)

# Three Abstractions
Computational problem:  
- defines a computational task
- specifies what the input is, and what the output should be

Algorithm:
- step by step instructions to go from input to output
- different from implementation

Correctness and complexity analysis:
- A formal proof that the algorithm solves the problem
- Establish bounds on the resources it uses

# Decision Problems
A decision problem only allows Yes (1) or No (0) outputs

# Terminology
## Alphabet
An alphabet $\Sigma$ is a non-empty finite set chose elements are called symbols
### Examples
- $\Sigma = \lbrace0,1\rbrace$ : binary alphabet
- $\Sigma = \lbrace a,b,c,\dots,z\rbrace$: lower-case English alphabet
- $\Sigma=\lbrace 0,1,2,+,-,\div,\times,(,)\rbrace$: arithmetic expression alphabet for base 3
- $\Sigma=$ ASCII characters
## String over $\Sigma$
A finite sequence of symbols from $\Sigma$  
The set of all strings over $\Sigma$ is denoted as $\Sigma^*$ ('Sigma star')
### Examples
- Python's `str` object
- $0110$ is a string of length 4 over the binary alphabet
- $bob$ is a string of length 3 over the English alphabet
- We often name strings using letters like $u,v,w$ 
	- $w=w_1w_2\cdots w_n$ where each $w_i\in\Sigma$
- The length of a string $w$ is written $|w|$
- There is only one string of length 0
	- denoted $\epsilon$ ('empty string')
	- Not a symbol from $\Sigma$
	- like `''` in Python
## Concatenation
The concatenation of string $u,v$ is the string $uv$
- Formed by appending $v$ to the end of $u$
### Examples
- `u+v` in Python
- $u=010,v=01,uv=01001$
- Concatenating empty string does not change the word
- Exponential notation $w^k$ means "concatenate $w$ with itself $k$ times"
## Language over $\Sigma$
A set $L\subseteq \Sigma^*$ of strings is called a *language over $\Sigma$*
### Examples
- $L=$ the set of all strings representing legal Python programs
- $L=$ the set of all binary strings representing prime numbers
- $L=$ the set of all true statements about arithmetic
- $L=$ the set of all English words (in a given dictionary)
- $L=$ the set of all English sentences (in a given book)
### Note
The empty set $\emptyset$, also written {} is a language with no elements in it
- However, the set $\lbrace\epsilon\rbrace$ is a language with one element in it, the empty string
- The languages $\lbrace0,1\rbrace$ and $\lbrace1,0\rbrace$ are equal, but the strings $01$ and $10$ are not
### Problems and Languages
Every decision problem on strings can be viewed as a language
- A set of strings for which the answer is "Yes"
Decision problem:
- Input: string $P$
- Output: "Yes" if $P$ is a legal Python program, "No"
 otherwise
has a corresponding language:
$$L_{\text{Python}}=\lbrace P|P\text{ is a legal Python program}\rbrace$$

The generic problem is parameterised by a language $L$, called the *membership problem in* $L$
- Input: string $x$
- Output: "Yes" if $x\in L$, and "No" otherwise

## Operations
- Ways to form new languages from old ones

Let $A,B$ be languages over $\Sigma$  
The new languages will also be over $\Sigma$

### $A\cup B$
- The language of strings that are in $A$ or $B$ or both
$$A\cup B=\lbrace x\in\Sigma^*:x\in A,x\in B\rbrace$$

### $A\cap B$
- The language of strings that are in both $A$ and $B$
$$A\cap B=\lbrace x\in \Sigma^*:x\in A,x\in B\rbrace$$

### $A\backslash B$
- The language of strings that are in $A$ but not $B$
$$A\backslash B=\lbrace x\in \Sigma^*:x\in A,x\notin B\rbrace$$

### $AB$
- Read "$A$ concatenate $B$ " or "$A$ cat $B$ "
- The language of strings formed by concatenating a string from $A$ with a string from $B$
$$AB=\lbrace xy\in \Sigma^*:x\in A,y\in B\rbrace$$

- Exponential notation $A^k$ means to concatenate $A$ with itself $k$ times
	- For $k\in\mathbb{Z}^+$, define $A^k$ to be $\overbrace{AA\cdots A}^\text{k}$
	- $A^0=\lbrace\epsilon\rbrace$
	- $A^{n+m}=A^nA^m$ (even if $n$ or $m$ is zero)

### $A^*$
- The language of strings that includes the empty string and all strings of the form $x_1x_2\cdots x_k$ where $k\geq 1$ and each $x_i\in A$
$$A^*=\lbrace x_1x_2\cdots x_k\in\Sigma^*:k\geq0,\text{ each }x_i\in A\rbrace$$

Also written as 
$$A^*=\bigcup_{n\in\mathbb{Z}^+_0}A^n$$

$$=A^0\cup A^1\cup A^2\cup A^3\cup\dots$$

We define $A^+$ ("A plus") to be $A^1\cup A^2\cup A^3\cup\dots$

# Summary
1. Expressions that describe "simple" languages
2. Extremely useful
	- Text processing, e.g. pattern matching
	- In Natural Language Processing as features in (machine learning) classifiers
	- Scanners (aka Lexical analysers, Tokenisers)
	- Specification of data formats
	- Foundations of query languages for graph databases
3. Based on 3 language operations
	1. Union
	2. Cat
	3. Star

# Syntax
Let $\Sigma$ be an alphabet
- The *regular expressions over* $\Sigma$ are strings defined by the following recursive process
	1. The symbols $\emptyset$ and $\epsilon$ are regular expressions
	2. Each symbol $a$ from $\Sigma$ is a regular expression
	3. If $R_1,R_2$ are regular expressions, then so is $(R_1|R_2)$
	4. If $R_1,R_2$ are regular expressions, then so is $(R_1R_2)$
	5. If $R$ is a regular expression, then so is $R^*$
## Examples
Let $\Sigma=\lbrace a,b,c\rbrace$  
- $(a|\emptyset)$ 
- $(a\epsilon)$ 
- $(b^*)$ 
- $((a^*|b^*)(ac))^*$

## Notation
You can drop the outermost brackets to improve readability
- $a|\emptyset$ instead of $(a|\emptyset)$  
- $ab^*$ instead of $(ab^*)$, which is NOT $(ab)^*$

# Semantics
A string *matches* a regular expressions according to these rules:
1. No string matches the regex $\emptyset$
2. Only the empty string matches the regex $\epsilon$
3. For alphabet symbol $a\in\Sigma$, only the string $a$ matches the regex $a$
4. A string $x$ matches $(R_1|R_2)$ means $x$ matches $R_1$ or $x$ matches $R_2$
5. A string $x$ matches $(R_1R_2)$ means $x$ can be written as $x=u_1u_2$ where $u_1,u_2$ are strings, and $u_1$ matches $R_1$ and $u_2$ matches $R_2$
6. A string $x$ matches $R^*$ means either $x$ is the empty string, or it can be written as $x=u_1u_2\cdots u_k$ (for $k\ge 1$) where each $u_i$ is a string that matches $R$
- These rules are recursive

# Recursion
Recursive procedures are used for defining many objects and properties
- Precise, unambiguous
- Can be implemented as is as a recursive algorithm

# Notation
- The set of all strings that match a regex $R$ is written $L(R)$, and is called
	- The *language specified* by $R$, 
	- The *language represented* by $R$, or
	- The *language of* $R$
- We can drop brackets for associative operations
	- $(R_1|R_2|R_3)$ instead of $((R_1|R_2)R_3)$
	- $(R_1|R_2|R_3)$ instead of $((R_1R_2)R_3)$
- If $A=\lbrace{a,b,c}\rbrace$, we can write $A$ instead of $(a|b|c)$
	- e.g. $A^*$ instead of $(a|b|c)^*$
	- We can do this for any finite set $A$ of strings
## Recursive definition of $L(R)$
Let $\Sigma$ be an alphabet 
The language $L(R)$ of a regex $R$ is defined by the following recursive procedure:
1. $L(\emptyset)=\lbrace\rbrace$ and $L(\epsilon)=\lbrace\epsilon\rbrace$
2. $L(a)=\lbrace a\rbrace$ for $a\in\Sigma$
3. $L(R_1|R_2)=L(R_1)\cup L(R_2)$
4. $L(R_1R_2)=L(R_1)L(R_2)$
5. $L(R^*)=L(R)^*$

***
- $\emptyset$ : symbol used in regexes and the empty set of strings
- $\epsilon$ : symbol used in regexes and a string
- $a\in\Sigma$ : symbol used in regexes, an alphabet symbol and a string of length 1
- * : symbol used in regexes, and an operation on sets of strings

Some places uses $+$ or $\cup$ instead of $|$

# Languages that are specified using regexes
Regexes can be used to specify keywords and identifiers in programming languages
- Set of identifiers in Python
- Signed and unsigned integers
- Hexadecimal numbers prefixed with '0x'
For specifier expressions and statements, we will need a more powerful model ([context-free grammars](Context-free%20Grammars.md Grammars>))
