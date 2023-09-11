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
- Symbols are from the tape alphabet $\Gamma$, which includes the input alphabet $\Sigma$ and '_'

