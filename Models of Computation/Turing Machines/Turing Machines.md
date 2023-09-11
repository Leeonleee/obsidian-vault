# Table of Contents


# Turing Machines in a Nutshell
A  Turing Machine (TM) $M$ is like a program that:
- Can only use variables with finite domains
	- e.g. variable called `state` taking finitely many values
- Has an infinite **tape**, made of **cells**
	- there is a single pointer (aka **head**) on the tape
	- there is a pointer than can move left, right or stay
	- the pointer can read and write symbols (from a bigger tape alphabet $\Gamma$)

