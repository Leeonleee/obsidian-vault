# Table of Contents


# Turing Machines in a Nutshell
A  Turing Machine (TM) $M$ is like a program that:
- Can only use variables with finite domains
	- e.g. variable called `state` taking finitely many values
- Has an infinite **tape**, made of **cells**
	- there is a single pointer (aka **head**) on the tape
	- the is a pointer than can move left, right or stay
	- the pointer can read and write symbols (from a bigger tape alphabet $\Gamma$)
- Initially, the input string over input alphabet $\Sigma$ is written on the tape
- The machine can, depending on the state decide to Halt, Accept, or Reject
- It is deterministic
- A TM $M$ **accepts** a string $u\in\Sigma^*$ if $M$ starting with $u$ on the input tape, with the pointer on the left-most symbol. from the initial state runs and reaches an "Accept" state 
- The **language recognised by $M$ (language of $M$)** is the set of strings it accepts

# A TM is written as a list of "instructions"
Each instruction is in the form 
```
<current state> <current symbol> <new symbol> <direction> <new state>
```
- The instruction "q1 a b R q2" tells the machine that "if it is in state $q1$ and sees the symbol $a$ under the head, it should write the symbol $b$ under the head, move one cell to the right, and change to state $q2$"
- Symbols are from the tape alphabet $\Gamma$, which includes the input alphabet $\Sigma$ and '\_\' 
- Directions:
	- Move one cell to the left $'L'$
	- Move one cell to the right $'R'$
	- Do not move $'*'$ (aka $S$)
- The machine stops running when it reaches any state starting with 'halt'
	- e.g. halt, halt-accept, halt-reject

# TM recognising the language of a\*b\*
Idea: scan the tape, do not write anything but keep track that once you see a $b$, you don't see an $a$ again
```
; Checks of the input string matches a*b*
; q0 is the initial state
q0 _ _ * halt-accept
q0 a a * q1
q0 b b * q2

; q1 represents that only a's have been seen
q1 a a R q1
q1 b b R q2
q1 _ _ * halt-accept

; q2 represents that a's have been seen, followed by b's
q2 b b R q2

q2 _ _ * halt-accept
q2 a a * halt-reject
```

# TM recognising $\lbrace0^n1^n:n\ge 1\rbrace$
- Match leftmost 0 with leftmost 1, replace 0 with X and 1 with Y and repeat
- If a 1 cannot be found this way, reject (more 0s than 1s)
- If a 0 cannot be found this way, go to the end and check there are no more characters
```
; replace 0 by X and look for matching 1 
; but if Y is seen, go for endgame
q0 0 X R q1
q0 Y Y R q3

; skip over 0's and Y's until 1 is found 
; replace it by Y and start heading back to left
q1 0 0 R q1
q1 Y Y R q1
q1 1 Y L q2

; move left skipping 0's and Y's until the first X is found
; move right to look for leftmost 0
q2 Y Y L q2
q2 0 0 L q2
q2 X X R q0

; endgame
; make sure there are no extra 1's or 0's
q3 Y Y R q3
q3 _ _ * halt-accept
q3 0 0 * halt-reject 
q3 1 1 * halt-reject
```

# Notation
- $Q=$ set of states
- $\Sigma=$ input alphabet
- $\Gamma=$ tape alphabet, includes $\Sigma$ and the blank symbol $\_$
- $\delta:Q\times \Gamma\rightarrow\Gamma\times\lbrace L,R,S\rbrace \times Q$ is the transition function

# Relationship between TMs and DFAs
- A DFA is a TM that cannot right on its tape, can only move right and must enter a halting state when it first reaches a blank symbol (read the entire input)
- A TN can write on the tape, move left, go past the original input and also run forever

