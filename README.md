# MipsWithPipesProcessor

Introduction

The problem of the Towers of Hanoi is to move a column made from discs concentric of different diameters, stacked from the largest diameter to the smallest diameter, from its original position A to its destination position C, having point B available for movements intermediate This movement has the restriction that only one disc can be moved to the time, and that at no time can a disc of greater diameter be on a disk of lesser diameter.

But know we are making the processor that can handle the instruction of the program, that’s using Quartus to program in Verilog de MIPS.

Development of the MIPS
Implement in Verilog a processor based on the MIPS architecture, which can execute the instructions add, addi, sub, or, ori, and, andi, nor, sll, srl, lw, sw, beq, bne, j, jal, jr which must adhere to the MIPS Green Sheet specification. This implementation can use as a starting point the data-path seen in class, which was designed to support some of the previous instructions. This implementation must be able to execute the program that was used in practice 1, note that this implementation must support recursive functions.

Development of HANOI
This algorithm starts by filling up tower A with N discs, then proceeds to enter the Hanoi function by giving it the values of N, and the 3 towers (origin, auxiliary and destiny), if the N value is 1 it will directly move the disc at the top of the given tower directly to the destiny tower, if it's not one it will move the N-1 discs to the auxiliary tower by calling for Hanoi function with the values N-1, Origin and swapping auxiliary and destiny, then proceeds to move the Nth disc to destiny tower and move the N-1 discs to destiny tower, this time using origin tower as destiny.


New modules:

	OR Gate:
A gate of type OR was added, this to be able to perform a branch, since in the case that BEQ or BNE is 1 then it becomes a branch.

Forwarding Unit:
This module serves as a way to send ahead data that hasn't been sent in a register and is required for a following instruction.




Hazard Detection Unit:
This module was made to stall and noop the next operation in cases of branches, jumps or if the value of a load word will be used right after it's been requested.

Pipe
This is a register module saves the needed data for the next step in a pipeline to be able to move on to the next step while loading the next instruction in the previous step.

Equals
This module serves as a way to put the branch conditions into a module, making it easier to release the wire that tells us if a branch is taken,
