# R0-CPU

![alt tag](https://s24.postimg.org/bmq9o00s5/image.png)

# Intro

**R0** is a hard-wired 8-bit CPU, built on Von Neumann Architecture.
It was built as an application on the theory of Computer Organization.


# Instruction Set 

- Half of the instructions in the instruction set fit into one byte.

- These instructions are identified by a 0 in the most-significant bit in the instruction, i.e. op1 = 0X.

- The 4 bits of opcode are split into op1 and op2.

- Rd is the destination register, and Rs is the source register.

- The other half of the instruction set are two-byte instructions. The first byte has the same format as above, and it is followed by an 8-bit constant or immediate value

- These two-byte instructions are identified by a 1 in the most-significant bit in the instruction, i.e. op1 = 1X.

- With 4 operation bits, there are 16 instructions.


| op1	| op2 |	Mnemonic	| Purpose|
|---|---|---|---|
| 00	| 00 |	AND |Rd, Rs	Rd = Rd AND Rs |
| 00	| 01 |	OR | Rd, Rs	Rd = Rd OR Rs |
| 00	| 10 |	ADD | Rd, Rs	Rd = Rd + Rs |
| 00	| 11 |	SUB | Rd, Rs	Rd = Rd - Rs |
| 01	| 00 |	LW | Rd, (Rs)	Rd = Mem[Rs] |
| 01	| 01 |	SW | Rd, (Rs)	Mem[Rs] = Rd |
| 01	| 10 |	MOV |Rd, Rs	Rd = Rs |
| 01	| 11 |	NOP |	Do nothing |
| 10	| 00 |	JEQ | Rd, immed	PC = immed if Rd == 0 |
| 10 |	01 |	JNE |Rd, immed	PC = immed if Rd != 0 |
| 10 |	10 |	JGT | Rd, immed	PC = immed if Rd > 0 |
| 10 |	11 |	JLT | Rd, immed	PC = immed if Rd < 0 |
| 11 |	00 |	LW  | Rd, immed	Rd = Mem[immed] |
| 11	| 01 |	SW  | Rd, immed	Mem[immed] = Rd |
| 11	| 10	| LI  | Rd, immed	Rd = immed |
| 11 |	11 |	JMP | immed	PC = immed |


# Architecture


- The CPU has an 8-bit data bus and an 8-bit address bus, so it can only support 256 bytes of memory to hold both instructions and data.

- Internally, there are four 8-bit registers, R0 to R3, plus an Instruction Register, the Program Counter, and an 8-bit register which holds immediate values.

- The ALU is the same one that we designed last week. It performs the four operations AND, OR, ADD and SUB on two 8-bit values, and supports signed ADDs and SUBs.

- The CPU is a load/store architecture: data has to be brought into registers for manipulation, as the ALU only reads from and writes back to the registers.

- The ALU operations have two operands: one register is a source register, and the second register is both source and destination register, i.e. destination register = destination register OP source register.

- All the jump operations perform absolute jumps; there are no PC-relative branches. There are conditional jumps based on the zeroness or negativity of the destination register, as well as a "jump always" instruction.

- The dbus and sbus labels indicate the lines coming out from the register file which hold the value of the destination and source registers.

- Note the data loop involving the registers and the ALU, whose output can only go back into a register.

- The dataout bus is only connected to the dbus line, so the only value which can be written to memory is the destination register.

# License

This Project is signed under MIT License.
