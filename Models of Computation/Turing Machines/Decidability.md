# Table of Contents


# Encodings
- The input to a TM is always a string, but working other objects can be useful over $\Sigma$
- Almost any object can be encoded as a string
- Can be written as
	- $<X>$ in Sipser
	- `str(X)` in Python
	- or just as $X$
- The encoding of more than 1 object can be written as
	- $<X,Y>$
	- $X;Y$

# Encoding Numbers
The number $n\in \mathbb{Z}^+_0$ can be encoded as a string in some fixed base
e.g. The number 3 is encoded by the string:
- 111 in unary encoding
- 11 in binary
- 10 in ternary
- 3 in decimal
- etc
- Integers can be encoded as a string by adding a symbol for the sign

# Encoding sequences of strings
List the strings in order, separated by a new alphabet symbol called a **delimiter**
e.g.
- 00,1,000,10
- The delimiter here is the comma, but any other symbol can be used

# Encoding TMs
Let $Source_M$ denote the string encoding of a TM $M$
You can think that it is the source code in any general purpose programming language

# Encoding graphs
Use things like adjacen

