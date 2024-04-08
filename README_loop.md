We consider implementation of the custom programming language "Loop". The syntax of the language is described by a grammar with the starting symbol Program:

Program → SequenceOfInstructions
SequenceOfInstructions → ε | SequenceOfInstructions Instruction

Instruction → Increase | Repeat

Increase → Variable

Repeat → '(' Variable SequenceOfInstructions ')'

Variable → 'a' | ... | 'z'

The program consists of characters that in the grammar are enclosed in quotes. Apart from these, no other characters, not even spaces or line endings, may appear in the source code.


***********************************************************************************

The program has access to 26 variables, whose values are non-negative integers.

Instructions derived from the SequenceOfInstructions symbol are executed in order from the first to the last.

The Increase instruction, in the form of a variable, is equivalent to the C language instruction:

++variable;


The Repeat instruction, in the form of (variable...), is equivalent to the C language instruction:

while (variable > 0) {
--variable;
...
}

***********************************************************************************

The implementation of the language consists of an optimizing compiler that generates code for a virtual machine, as well as an interpreter for the code of this machine.

The machine executes instructions:

INC Variable (increment)
increase the value of Variable by one;

ADD Variable0 Variable1 (add)
add to Variable0 the value of Variable1;

CLR Variable (clear)
clear the Variable;

JMP Address (jump)
jump to the instruction at Address;

DJZ Variable Address (decrement or jump if zero)
if Variable is 0 then jump to the instruction at Address, otherwise decrease the value of Variable by one;

HLT (halt)
end the execution of the program.

The execution of the program in machine language starts with the first instruction.

If the instruction does not specify otherwise, after its execution, we move to the next instruction in the code.

For a sequence of instructions, the compiler generates code in the order from the first to the last instruction. The code generated for the program ends with the HLT instruction.

If in the Repeat instruction no other Repeat instruction is nested, i.e., in brackets there is a sequence of variables Variable0, ..., VariableN, for N >= 0, and if none of the variables Variable1, ..., VariableN is the variable Variable0, then the compiler generates optimized code in the form of:

ADD Variable1 Variable0
...
ADD VariableN Variable0
CLR Variable0
If the conditions allowing for generating optimized code for the instruction are not met, the compiler generates ordinary code.

The ordinary code for the Increase instruction, in the form of Variable, is:

INC Variable
The ordinary code for the Repeat instruction, in the form of (Variable...), is:

DJZ Variable End
...
JMP Start
where Start is the address of the first instruction of this sequence and End is the address of the instruction directly after the last instruction of this sequence.


***********************************************************************************

The goal is to write a program that is an implementation of the language "Loop".

The program reads and executes commands:

printing the value of a variable;

executing a program in the language "Loop".

Before executing the first command, the values of all variables are equal to 0.

Variables retain their values after executing the command. They are not reset before each program execution.

***********************************************************************************

Input data format:

The program's data is a series of lines, each with one command.

The command to print the value of a variable starts with the character '=', followed by the variable's name.

The line of the command to execute the program contains the source code in the "Loop" language.

***********************************************************************************

Output data format:

The program's output is the result of executing commands to print the value of a variable.

The value of the variable is written in decimal, in one line, without any leading insignificant zeros.

The value 0 is represented by the digit 0 and positive values start with a non-zero digit.



It is assumed that the input is correct.
