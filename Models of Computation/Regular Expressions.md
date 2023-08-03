# Table of Contents
- [Terminology](<#Terminology>)

# Terminology
## Alphabet
An alphabet $\Sigma$ is a non-empty finite set chose elements are called symbols
### Examples
- $\Sigma = \{0,1\}$ : binary alphabet
- $\Sigma = \{a,b,c,\dots,z\}$: lower-case English alphabet
- $\Sigma=\{0,1,2,+,-,\div,\times,(,)\}$: arithmetic expression alphabet for base 3
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
- $u=010,

