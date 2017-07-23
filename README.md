# R0-CPU

![alt tag](https://s24.postimg.org/bmq9o00s5/image.png)

# Intro

WIP

# Specs

WIP

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
