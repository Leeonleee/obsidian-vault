# Table of Contents
- [Decision Problems](<# Decision Problems>)
- [Terminology](<#Terminology>)


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
