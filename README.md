# VSDSquadron Mini Internship 2024

## Overview
The VSDSquadron Mini Internship 2024 is an intensive, short-term internship program designed to provide participants with hands-on experience in the fields of VLSI design, semiconductor technology, and related domains. Tailored for engineering students, recent graduates, and aspiring technologists, this program bridges the gap between academic knowledge and industry-ready skills.

 <p align="center">
  <img width="400" height="250" src="/Task 1/VSD_sq/vsdsquadron mini.jpg">
</p>

The VSDsquadron Mini is a compact RISC-V development board designed for hobbyists, educators, and engineers. It features a powerful RISC-V microcontroller, offering a balance of performance and energy efficiency. Equipped with essential peripherals like GPIOs, UART, I2C, SPI, and ADC, it supports a wide range of applications, from IoT projects to embedded systems development. The board is USB-programmable, making it beginner-friendly, and is compatible with popular development tools and open-source resources. Its small form factor and versatility make it an ideal choice for learning RISC-V architecture and prototyping innovative designs.

##  Basic Details

**Name:** Rohith DR  
**College:** Global Academy of Technology  
**Email ID:** rohithrohith838@gmail.com  
**GitHub Profile:** [Rohith-DR](https://github.com/Rohith-DR?tab=repositories)  
**LinkedIN Profile:** [Rohith-DR_ECE](https://www.linkedin.com/in/rohith-dr/)

-------------------------------------------------

<details>
<summary><b>Task 1:</b> The assignment is to watch lab videos that are based on C and RISCV and then use the gcc and riscv compilers to compile the C code</summary>

### C Language based LAB
We have to follow the given steps to compile any **.c** file in our machine:  
1. Open the bash terminal and locate to the directory where you want to create your file. Then run the following command:

	```
	gedit sum.c
	```  
2. This will open the editor and allows you to write into the file that you have created. You have to write the C code of printing the sum of n numbers. Once you are done with your code, press ```Ctrl + S``` to save your file, and then press ```Ctrl + W``` to close the editor.   
3. To the C code on your terminal, run the following command:

	```
	gcc sum.c
	./a.out
	```
### C Code compiled on gcc Compiler:
 <p align="center">
  <img width="800" height="500" src="/Task 1/C Code compiled on gcc Compiler.png">
</p>

### Compiled C output:
 <p align="center">
  <img width="800" height="500" src="/Task 1/compiled C output.png">
</p>

### RISCV based LAB
We have to do the same compilation of our code but this time using RISCV gcc compiler. Follow the given steps:  
1. Open the terminal and run the given command:  

	```
	cat sum.c
	```
### Cat Command:
 <p align="center">
  <img width="800" height="500" src="/Task 1/cat Command.png">
</p>

2. Using the **cat** command, the entire C code will be displayed on the terminal. Now run the following command to compile the code in riscv64 gcc compiler:  

	```
	riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum.o sum.c
	```
3. Open a new terminal and run the given command:    

	```
	riscv64-unknown-elf-objdump -d sum.o
	```
### Objdump using -O1 format:
 <p align="center">
  <img width="800" height="500" src="/Task 1/Objdump using -O1 format.png">
</p>

4. Open the previous tab and run the following command to compile the code in riscv64 gcc compiler:  

	```
	riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum.o sum.c
	```

5. Open a new terminal and run the given command:    

	```
	riscv64-unknown-elf-objdump -d sum.o
	```
### Objdump using -Ofast format:
 <p align="center">
  <img width="800" height="500" src="/Task 1/Objdump using -Ofast format.png">
</p>
</details>

-------------------------------------------------

<details>
<summary><b>Task 2:</b> Using Spike Simulation and Interactive Debugging Mode to Debugg the C code during Spike</summary> 

### What is SPIKE in RISCV?
> * A RISC-V ISA is a simulator, enabling the testing and analysis of RISC-V programs without the need for actual hardware.  
> * Spike is a free, open-source C++ simulator for the RISC-V ISA that models a RISC-V core and cache system. It can be used to run programs and a Linux kernel, and can be a starting point for running software on a RISC-V target.    
  
### What is pk (Proxy Kernel)?  
> * The RISC-V Proxy Kernel, pk , is a lightweight application execution environment that can host statically-linked RISC-V ELF binaries.  
> * A Proxy Kernel in the RISC-V ecosystem simplifies the interaction between complex hardware and the software running on it, making it easier to manage, test, and develop software and hardware projects.  

### Testing the SPIKE Simulator  
The target is to run the ```sum.c``` code using both ```gcc compiler``` and ```riscv compiler```, and both of the compiler must display the same output on the terminal. So to compile the code using **gcc compiler**, use the following command:  
```
gcc sum.c  
./a.out
```
And to compile the code using **riscv compiler**, use the following command:  
```
spike pk sum.o
```  
#### Spike Simulation:
 <p align="center">
  <img width="800" height="500" src="/Task 2/Spike Simulation.png">
</p>

#### Following are the snapshots of RISCV Objdump with **-O1** and **-Ofast** options  
  
#### Objdump in -O1:

```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum.o sum.c
```

 <p align="center">
  <img width="800" height="500" src="/Task 2/Objdump in -O1.png">
</p>
  
#### Objdump in -Ofast:

```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum.o sum.c
```
 
 <p align="center">
  <img width="800" height="500" src="/Task 2/Objdump in -Ofast.png">
</p>

#### Debugging the Assembly Language Program of  ```sum.c```  
* Open the **Objdump** of code by using the following command  
```
riscv64-unknown-elf-objdump -d sum.o | less  
```
* Open the debugger in another terminal by using the following command  
```
spike -d pk sum.o
```
* The debugger will be opened in the terminal. Now, debugging operations can be performed as shown in the following snapshot.

#### Debugging:
 <p align="center">
  <img width="800" height="500" src="/Task 2/Debugging.png">
</p>
</details>

----------------------------------------

<details>
<summary><b>Task 3:</b> Identifying RISC-V Instruction Types</summary>

## WHAT IS RISC-V?
- RISC-V is an open-source instruction set architecture (ISA) that allows developers to create processors tailored for specific applications.
- RISC-V is based on reduced instruction set computer principles and is the fifth generation of processors built on this concept.
- RISC-V can also be understood as an alternative processor technology that is free and open-source, meaning you don't need to purchase a license to use it.

## INSTRUCTIONS FORMAT IN RISC-V
The instruction format of a processor dictates how machine language instructions are structured and organized for the processor to execute. Each instruction is composed of a series of 0s and 1s, with each segment containing information about the location and operation of data.  
There are six primary instruction formats in RISC-V:

1. R-format
2. I-format
3. S-format
4. B-format
5. U-format
6. J-format

#### RISCV Instruction Types

 <p align="center">
  <img src="/Task 3/Instruction_Types.png">
</p>

#### 1. R-type Instruction
In RV32, each instruction is 32 bits in size. R-type instructions perform operations on registers (not memory) and are used for various arithmetic and logical operations. The 32-bit instruction is divided into six fields:

 <p align="center">
  <img src="/Task 3/Instruction_R_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register where the result of the operation is stored.
- **func3** (3 bits): Specifies the type of operation performed.
- **rs1, rs2** (5 bits each): Source registers used in the operation.
- **func7** (7 bits): Further specifies the operation.

#### 2. I-type Instruction
I-type instructions involve operations that use both registers and an immediate value (not memory). These instructions are used for immediate and load operations. The instruction format is as follows:

 <p align="center">
  <img src="/Task 3/Instruction_I_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register for the result.
- **func3** (3 bits): Specifies the type of operation.
- **rs1** (5 bits): Source register.
- **imm[11:0]** (12 bits): A 12-bit signed immediate value used in the operation.

#### 3. S-type Instruction
S-type instructions are used for store operations where data is stored from a register to memory. The 32-bit instruction is divided as follows:

 <p align="center">
  <img src="/Task 3/Instruction_S_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[11:5]** (7 bits) and **imm[4:0]** (5 bits): The 12-bit immediate value is split across two fields, specifying the store offset.
- **rs1** (5 bits): The register containing the data to store.
- **rs2** (5 bits): The register containing the address where data should be stored.
- **func3** (3 bits): Specifies the type of store (byte, half-word, or word).

#### 4. B-type Instruction
B-type instructions are used for conditional branching based on comparisons. The 32-bit instruction format is as follows:

 <p align="center">
  <img src="/Task 3/Instruction_B_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[12]** (1 bit), **imm[10:5]** (6 bits), **imm[4:1]** (4 bits), and **imm[11]** (1 bit): These bits form the 12-bit signed immediate used for the branch offset.
- **rs1, rs2** (5 bits each): Source registers involved in the comparison.
- **func3** (3 bits): Defines the condition used for branching.

#### 5. U-type Instruction
U-type instructions are used to transfer an immediate value into the destination register. The format is simple and involves only two instructions: `LUI` and `AUIPC`.

 <p align="center">
  <img src="/Task 3/Instruction_U_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register for the immediate value.
- **imm[19:0]** (20 bits): The 20-bit immediate value that is transferred to the destination register.

For example, the instruction `lui x15, 0x13579` would load the value `0x13579000` into the upper 20 bits of register `x15`.

#### 6. J-type Instruction
J-type instructions are used for jump operations. These instructions are often used for loops and branching to a specified memory location. The format is as follows:

 <p align="center">
  <img src="/Task 3/Instruction_J_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[20]** (1 bit), **imm[10:1]** (10 bits), **imm[11]** (1 bit), and **imm[19:12]** (8 bits): These bits form the 20-bit signed immediate for the jump address.
- **rd** (5 bits): The destination register (used for return addresses).

## Commands for Extracting RISC-V Instructions
<details>
<summary>Commands</summary>
	
#### Compile the C program into a RISC-V ELF binary
```
riscv64-unknown-elf-gcc -march=rv32i -mabi=ilp32 -o sum sum.c
```

#### Generate a disassembly of the binary
```
riscv64-unknown-elf-objdump -d sum > sum.objdump
```

#### Display the main function's disassembly, with 30 lines of context
```
riscv64-unknown-elf-objdump -d sum | grep -A 30 "<main>:"
```

#### Filter for arithmetic and logical instructions: add, sub, and, or
```
riscv64-unknown-elf-objdump -d sum | grep -E "add|sub|and|or"
```

#### Filter for immediate arithmetic, load, and jump instructions: addi, lw, jalr
```
riscv64-unknown-elf-objdump -d sum | grep -E "addi|lw|jalr"
```

#### Filter for store and branch instructions: sw, beq, bne, blt, bge
```
riscv64-unknown-elf-objdump -d sum | grep -E "sw|beq|bne|blt|bge"
```

#### Filter for control flow and address instructions: lui, auipc, jal
```
riscv64-unknown-elf-objdump -d sum | grep -E "lui|auipc|jal"
```

#### Count occurrences of each unique instruction
```
riscv64-unknown-elf-objdump -d sum | grep -o "\s\w\+\s" | sort | uniq -c
```
</details>

# Instructions with explaination
<details>
<summary>Now, let's analyse each instruction one by one</summary>
	
# RISC-V Instructions Explanation

This document provides a detailed explanation of the given RISC-V assembly instructions, including their types, functionality, and corresponding 32-bit representations.

### 1. `add a5, a4, a5`
- **Type**: R-type  
- **Description**: Adds the values in `a4` and `a5`, and stores the result in `a5`.  
- **Fields**:  
  - **opcode**: 0110011  
  - **rd**: a5 = 10101  
  - **rs1**: a4 = 10100  
  - **rs2**: a5 = 10101  
  - **func3**: 000  
  - **func7**: 0000000  
- **32-bit Instruction**: `0000000_10101_10100_000_10101_0110011`

---

### 2. `addi a2, a3, 4`
- **Type**: I-type  
- **Description**: Adds the immediate value `4` to the value in `a3`, and stores the result in `a2`.  
- **Fields**:  
  - **opcode**: 0010011  
  - **rd**: a2 = 10010  
  - **rs1**: a3 = 10011  
  - **imm**: 0000000000000100  
  - **func3**: 000  
- **32-bit Instruction**: `0000000000000100_10011_000_10010_0010011`

---

### 3. `sub a1, a1, a2`
- **Type**: R-type  
- **Description**: Subtracts the value in `a2` from the value in `a1`, and stores the result in `a1`.  
- **Fields**:  
  - **opcode**: 0110011  
  - **rd**: a1 = 10001  
  - **rs1**: a1 = 10001  
  - **rs2**: a2 = 10010  
  - **func3**: 000  
  - **func7**: 0100000  
- **32-bit Instruction**: `0100000_10010_10001_000_10001_0110011`

---

### 4. `and a5, a5, a2`
- **Type**: R-type  
- **Description**: Performs a bitwise AND operation between the values in `a5` and `a2`, and stores the result in `a5`.  
- **Fields**:  
  - **opcode**: 0110011  
  - **rd**: a5 = 10101  
  - **rs1**: a5 = 10101  
  - **rs2**: a2 = 10010  
  - **func3**: 111  
  - **func7**: 0000000  
- **32-bit Instruction**: `0000000_10010_10101_111_10101_0110011`

---

### 5. `or a5, a5, a6`
- **Type**: R-type  
- **Description**: Performs a bitwise OR operation between the values in `a5` and `a6`, and stores the result in `a5`.  
- **Fields**:  
  - **opcode**: 0110011  
  - **rd**: a5 = 10101  
  - **rs1**: a5 = 10101  
  - **rs2**: a6 = 10110  
  - **func3**: 110  
  - **func7**: 0000000  
- **32-bit Instruction**: `0000000_10110_10101_110_10101_0110011`

---

### 6. `xor a4, a7, a4`
- **Type**: R-type  
- **Description**: Performs a bitwise XOR operation between the values in `a7` and `a4`, and stores the result in `a4`.  
- **Fields**:  
  - **opcode**: 0110011  
  - **rd**: a4 = 10100  
  - **rs1**: a7 = 10111  
  - **rs2**: a4 = 10100  
  - **func3**: 100  
  - **func7**: 0000000  
- **32-bit Instruction**: `0000000_10100_10111_100_10100_0110011`

---

### 7. `lw a2, 20(sp)`
- **Type**: I-type  
- **Description**: Loads a word from the memory address obtained by adding `20` to the value in `sp`, and stores it in `a2`.  
- **Fields**:  
  - **opcode**: 0000011  
  - **rd**: a2 = 10010  
  - **rs1**: sp = 00010  
  - **imm**: 0000000000010100  
  - **func3**: 010  
- **32-bit Instruction**: `0000000000010100_00010_010_10010_0000011`

---

### 8. `sw a5, 28(sp)`
- **Type**: S-type  
- **Description**: Stores the value in `a5` at the memory address obtained by adding `28` to the value in `sp`.  
- **Fields**:  
  - **opcode**: 0100011  
  - **rs1**: sp = 00010  
  - **rs2**: a5 = 10101  
  - **imm**: 0000000000011100  
  - **func3**: 010  
- **32-bit Instruction**: `0000000_10101_00010_010_11100_0100011`

---

### 9. `beq s2, a2, 21978`
- **Type**: B-type  
- **Description**: Branches to the address offset `21978` if `s2` equals `a2`.  
- **Fields**:  
  - **opcode**: 1100011  
  - **rs1**: s2 = 10110  
  - **rs2**: a2 = 10010  
  - **imm**: 000000010101101110  
  - **func3**: 000  
- **32-bit Instruction**: `0000000_10010_10110_000_1010111010_1100011`

---

### 10. `bne a2, a5, 2174c`
- **Type**: B-type  
- **Description**: Branches to the address offset `2174c` if `a2` does not equal `a5`.  
- **Fields**:  
  - **opcode**: 1100011  
  - **rs1**: a2 = 10010  
  - **rs2**: a5 = 10101  
  - **imm**: 000000010001110100  
  - **func3**: 001  
- **32-bit Instruction**: `0000000_10101_10010_001_1001110100_1100011`

---

### 11. `sll a7, a7, a4`
- **Type**: R-type  
- **Description**: Performs a logical left shift of `a7` by the number of positions specified in the lower bits of `a4`, and stores the result in `a7`.  
- **Fields**:  
  - **opcode**: 0110011  
  - **rd**: a7 = 10111  
  - **rs1**: a7 = 10111  
  - **rs2**: a4 = 10100  
  - **func3**: 001  
  - **func7**: 0000000  
- **32-bit Instruction**: `0000000_10100_10111_001_10111_0110011`

---

### 12. `lui a3, 0x80`
- **Type**: U-type  
- **Description**: Loads the value `0x80` into the upper 20 bits of `a3`.  
- **Fields**:  
  - **opcode**: 0110111  
  - **rd**: a3 = 10011  
  - **imm**: 000000000000100000  
- **32-bit Instruction**: `000000000000100000_10011_0110111`

---

### 13. `jal ra, 247e4`
- **Type**: J-type  
- **Description**: Jumps to the address offset `247e4` and stores the return address in `ra`.  
- **Fields**:  
  - **opcode**: 1101111  
  - **rd**: ra = 00001  
  - **imm**: 0010010001111110100  
- **32-bit Instruction**: `0010010001111110100_00001_1101111`

---

### 14. `jalr a5`
- **Type**: I-type  
- **Description**: Jumps to the address specified in `a5` and stores the return address in `ra`.  
- **Fields**:  
  - **opcode**: 1100111  
  - **rd**: ra = 00001  
  - **rs1**: a5 = 10101  
  - **imm**: 0000000000000000  
  - **func3**: 000  
- **32-bit Instruction**: `0000000000000000_10101_000_00001_1100111`

---

### 15. `auipc a5, 0x6`
- **Type**: U-type  
- **Description**: Adds the immediate value `0x6` shifted left 12 bits to the current PC and stores the result in `a5`.  
- **Fields**:  
  - **opcode**: 0010111  
  - **rd**: a5 = 10101  
  - **imm**: 000000000000000110  
- **32-bit Instruction**: `000000000000000110_10101_0010111`
</details>

# Example Application with its Instructions
<details>
<summary>Given below is the C code for a application of 16-Bit ReRAM Memory Model</summary>
	
```c
//16-Bit ReRAM Memory Model

#include <stdio.h>
#include <stdint.h>

// Define states for ReRAM
#define HRS 0 // High Resistance State (binary 0)
#define LRS 1 // Low Resistance State (binary 1)

// Structure to represent a ReRAM cell
typedef struct {
    int state; // Current state of the cell (HRS or LRS)
} ReRAM_Cell;

// Structure to represent a 16-bit RAM
typedef struct {
    ReRAM_Cell cells[16]; // Array of 16 ReRAM cells
} ReRAM_16Bit_RAM;

// Function to initialize the 16-bit RAM
void initialize_ram(ReRAM_16Bit_RAM *ram) {
    for (int i = 0; i < 16; i++) {
        ram->cells[i].state = HRS; // Set all cells to HRS (binary 0)
    }
}

// Function to write a 16-bit value to the RAM
void write_to_ram(ReRAM_16Bit_RAM *ram, uint16_t data) {
    for (int i = 0; i < 16; i++) {
        // Write each bit to the corresponding cell
        if (data & (1 << i)) {
            ram->cells[i].state = LRS; // Set to LRS (binary 1)
        } else {
            ram->cells[i].state = HRS; // Set to HRS (binary 0)
        }
    }
}

// Function to read a 16-bit value from the RAM
uint16_t read_from_ram(ReRAM_16Bit_RAM *ram) {
    uint16_t data = 0;
    for (int i = 0; i < 16; i++) {
        if (ram->cells[i].state == LRS) {
            data |= (1 << i); // Set the corresponding bit in the output
        }
    }
    return data;
}

// Main function to demonstrate the 16-bit RAM simulation
int main() {
    ReRAM_16Bit_RAM ram;

    // Initialize the RAM
    initialize_ram(&ram);
    printf("Initialized RAM. All cells are in HRS (0).\n");

    // Write a 16-bit value to the RAM
    uint16_t value_to_write = 0b1010101010101010; // Example value: 16-bit alternating pattern
    printf("Writing value: 0x%04X\n", value_to_write);
    write_to_ram(&ram, value_to_write);

    // Read the value from the RAM
    uint16_t value_read = read_from_ram(&ram);
    printf("Value read from RAM: 0x%04X\n", value_read);

    // Write another 16-bit value to the RAM
    value_to_write = 0xFFFF; // All bits set to 1
    printf("Writing value: 0x%04X\n", value_to_write);
    write_to_ram(&ram, value_to_write);

    // Read again
    value_read = read_from_ram(&ram);
    printf("Value read from RAM: 0x%04X\n", value_read);

    return 0;
}
```
</details>


<details>
<summary>Now, let's analyse each instruction one by one present in Reram model application</summary>

### 1) `addiw a5, a5, 1`
* This is an I-type instruction used for adding an immediate value to a register.
* `a5` is both the source register (rs1) and the destination register (rd).
* The immediate value `1` is added to the value in register `a5` and the result is stored in `a5`.
* Opcode for `addiw` = `0001011`
* rd = `a5` = `00101`
* rs1 = `a5` = `00101`
* imm = `1` = `000000000001`
* func3 = `000`

**32 bits instruction:** `000000000001_00101_000_00101_0001011`

----------------------------------------------

### 2) `addi a4, a4, 4`
* This is an I-type instruction used for adding an immediate value to a register.
* `a4` is both the source register (rs1) and the destination register (rd).
* The immediate value `4` is added to the value in register `a4` and the result is stored in `a4`.
* Opcode for `addi` = `0010011`
* rd = `a4` = `00100`
* rs1 = `a4` = `00100`
* imm = `4` = `000000000100`
* func3 = `000`

**32 bits instruction:** `000000000100_00100_000_00100_0010011`

----------------------------------------------

### 3) `beq a5, a2, 10200`
* This is a B-type instruction used for conditional branching (branch if equal).
* If the values in registers `a5` and `a2` are equal, the program counter will jump to the specified offset (`10200`).
* Opcode for `beq` = `1100011`
* rs1 = `a5` = `00101`
* rs2 = `a2` = `00010`
* imm = `10200` = `000000000000101000000`
* func3 = `000`

**32 bits instruction:** `000000000000101_00101_000_00010_1100011`

----------------------------------------------

### 4) `lw a3, 0(a4)`
* This is an I-type instruction used for loading a word from memory.
* The value at memory address `a4 + 0` (no offset) is loaded into register `a3`.
* Opcode for `lw` = `0000011`
* rd = `a3` = `00011`
* rs1 = `a4` = `00100`
* imm = `0` = `000000000000`
* func3 = `010`

**32 bits instruction:** `000000000000_00100_010_00011_0000011`

----------------------------------------------

### 5) `bne a3, a1, 101d8`
* This is a B-type instruction used for conditional branching (branch if not equal).
* If the values in registers `a3` and `a1` are not equal, the program counter will jump to the specified offset (`101d8`).
* Opcode for `bne` = `1100011`
* rs1 = `a3` = `00011`
* rs2 = `a1` = `00001`
* imm = `101d8` = `00000000000101110111000`
* func3 = `001`

**32 bits instruction:** `000000000001011_00011_001_00001_1100011`

----------------------------------------------

### 6) `sllw a3, a6, a5`
* This is an R-type instruction used for performing a shift-left operation on a word.
* The value in register `a6` is shifted left by the number of bits specified in register `a5`, and the result is stored in register `a3`.
* Opcode for `sllw` = `0001011`
* rd = `a3` = `00011`
* rs1 = `a6` = `00110`
* rs2 = `a5` = `00101`
* func3 = `001`
* func7 = `0000000`

**32 bits instruction:** `0000000_00101_00110_001_00011_0001011`

----------------------------------------------

### 7) `or a0, a0, a3`
* This is an R-type instruction used for performing a bitwise OR operation between two registers.
* The values in registers `a0` and `a3` are bitwise OR’ed, and the result is stored in register `a0`.
* Opcode for `or` = `0110011`
* rd = `a0` = `00000`
* rs1 = `a0` = `00000`
* rs2 = `a3` = `00011`
* func3 = `110`
* func7 = `0000000`

**32 bits instruction:** `0000000_00011_00000_110_00000_0110011`

----------------------------------------------

### 8) `slli a0, a0, 0x30`
* This is an I-type instruction used for shifting a register value left by an immediate number of bits.
* The value in register `a0` is shifted left by `0x30` (48 in decimal), and the result is stored in register `a0`.
* Opcode for `slli` = `0010011`
* rd = `a0` = `00000`
* rs1 = `a0` = `00000`
* imm = `0x30` = `000000110000`
* func3 = `001`

**32 bits instruction:** `000000110000_00000_001_00000_0010011`

----------------------------------------------

### 9) `sd ra, 88(sp)`
* This is an S-type instruction used for storing a double word from a register to memory.
* The value in register `ra` is stored at memory address `sp + 88`.
* Opcode for `sd` = `0100011`
* rs1 = `sp` = `11101`
* rs2 = `ra` = `00000`
* imm = `88` = `0000000010110000`
* func3 = `011`

**32 bits instruction:** `000000001011000_11101_011_00000_0100011`

----------------------------------------------

### 10) `mv a0, sp`
* This is a pseudo-instruction that copies the value in `sp` to `a0`.
* It is equivalent to `addi a0, sp, 0`.
* Opcode for `addi` = `0010011`
* rd = `a0` = `00000`
* rs1 = `sp` = `11101`
* imm = `0` = `000000000000`
* func3 = `000`

**32 bits instruction:** `000000000000_11101_000_00000_0010011`

----------------------------------------------

### 11) `lui a0, 0x21`
* This is a U-type instruction used for loading an upper immediate value into a register.
* The value `0x21` is loaded into the upper 20 bits of register `a0`.
* Opcode for `lui` = `0110111`
* rd = `a0` = `00000`
* imm = `0x21` = `0000000000100001`

**32 bits instruction:** `0000000000100001_00000_0000000_0110111`

----------------------------------------------

### 12) `jal ra, 10184`
* This is a J-type instruction used for performing a jump and link operation.
* The program counter is updated by the immediate value (`10184`), and the return address is stored in `ra`.
* Opcode for `jal` = `1101111`
* rd = `ra` = `00000`
* imm = `10184` = `000000000001010010000`

**32 bits instruction:** `000000000001010_00000_0000000_1101111`

----------------------------------------------

### 13) `AND r8, r1, r3`
* All the arithmetic and logical operations are performed using R-type instruction format, hence this instruction belongs to R-type instruction set.  
* r8 is the destination register that will hold the value of r1 & r3, means performing AND operation bit by bit.  
* Opcode for AND = 0110011  
* rd = r8 = 01000  
* rs1 = r1 = 00001  
* rs2 = r3 = 00011  
* func3 = 111  
* func7 = 0000000  

**32 bits instruction :** `0000000_00011_00001_111_01000_0110011`

----------------------------------------------

### 14) `ld ra, 88(sp)`
* This is an I-type instruction used for loading a double word from memory.
* The value at memory address `sp + 88` is loaded into register `ra`.
* Opcode for `ld` = `0000011`
* rd = `ra` = `00000`
* rs1 = `sp` = `11101`
* imm = `88` = `0000000010110000`
* func3 = `011`

**32 bits instruction:** `000000001011000_11101_011_00000_0000011`

----------------------------------------------

### 15) `beqz a5, 102f0`
* This is a B-type instruction used for conditional branching (branch if equal to zero).
* If the value in register `a5` is zero, the program counter will jump to the specified offset (`102f0`).
* Opcode for `beqz` = `1100011`
* rs1 = `a5` = `00101`
* rs2 = `x0` = `00000`
* imm = `102f0` = `000000000010111100000`
* func3 = `000`

**32 bits instruction:** `000000000010111_00101_000_00000_1100011`

</details>

</details>

----------------------------------------------

<details>
<summary><b>Task 4:</b> Use RISCV Core: Verilog Netlist and Testbench to conduct a functional simulation experiment and view the waveforms</summary>  
<br>

>***NOTE:** Since this research internship does not include building the RISCV architecture or writing its testbench, we will utilize the pre-existing Verilog code and testbench. The GitHub repository used as a reference is : [iiitb_rv32i](https://github.com/vinayrayapati/rv32i/)*    
  
### Steps to perform functional simulation of RISCV 
1. download the ```iiitb_rv32i.v``` and ```iiitb_rv32i_tb.v``` files from
https://github.com/vinayrayapati/rv32i/
3. Create a new directory with your name ```mkdir <your_name>```
4. Copy the files ```iiitb_rv32i.v``` and ```iiitb_rv32i_tb.v``` to this directory
  
  
5. To run and simulate the verilog code, enter the following command:  
	```
	$ iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v
	$ ./iiitb_rv32i
	```
6. To see the simulation waveform in GTKWave, enter the following command:
	```
	$ gtkwave iiitb_rv32i.vcd
	```

7. The GTKWave will be opened and following window will be appeared  

 <p align="center">
  <img width="500" src="/Task 4/GTKWave Window.png">
</p>
 
#### Every instruction in the provided verilog file is hard-coded, as seen in the picture below. Hard-coded indicates that each instruction has been hard-coded according to the designer's own pattern rather than adhering to the RISCV specifications bit pattern. As a result, the 32-bit instruction we produced in Task 3 will not correspond to the specified instruction.  
  
 <p align="center">
  <img width="500" src="/Task 4/Instructions.png">
</p>
  
#### Following are the differences between standard RISCV ISA and the Instruction Set given in the reference repository:  
  
|  **Operation**  |  **Standard RISCV ISA**  |  **Hardcoded ISA**  |  
|  :----:  |  :----:  |  :----:  |  
|  ADD R6, R2, R1  |  32'h00110333  |  32'h02208300  |  
|  SUB R7, R1, R2  |  32'h402083b3  |  32'h02209380  |  
|  AND R8, R1, R3  |  32'h0030f433  |  32'h0230a400  |  
|  OR R9, R2, R5  |  32'h005164b3  |  32'h02513480  |  
|  XOR R10, R1, R4  |  32'h0040c533  |  32'h0240c500  |  
|  SLT R1, R2, R4  |  32'h0045a0b3  |  32'h02415580  |  
|  ADDI R12, R4, 5  |  32'h004120b3  |  32'h00520600  |  
|  BEQ R0, R0, 15  |  32'h00000f63  |  32'h00f00002  |  
|  SW R3, R1, 2  |  32'h0030a123  |  32'h00209181  |  
|  LW R13, R1, 2  |  32'h0020a683  |  32'h00208681  |  
|  SRL R16, R14, R2  |  32'h0030a123  |  32'h00271803  |
|  SLL R15, R1, R2  |  32'h002097b3  |  32'h00208783  |   
  

#### *Analysing the Output Waveform of various instructions that we have covered in TASK-2*  

**```Instruction 1: ADD R6, R2, R1```**

<p align="center">
  <img width="500" src="/Task 4/ADD.png">
</p>

---

**```Instruction 2: SUB R7, R1, R2```**

<p align="center">
  <img width="500" src="/Task 4/SUB.png">
</p>

---

**```Instruction 3: AND R8, R1, R3```**

<p align="center">
  <img width="500" src="/Task 4/AND.png">
</p>

---

**```Instruction 4: OR R9, R2, R5```**

<p align="center">
  <img width="500" src="/Task 4/OR.png">
</p>

---

**```Instruction 5: XOR R10, R1, R4```**

<p align="center">
  <img width="500" src="/Task 4/XOR.png">
</p>

---

**```Instruction 6: SLT R11, R2, R4```**

<p align="center">
  <img width="500" src="/Task 4/SLT.png">
</p>

---

**```Instruction 7: ADDI R12, R4, 5```**

<p align="center">
  <img width="500" src="/Task 4/ADDI.png">
</p>

---

**```Instruction 8: BEQ R0, R0, 15```**

<p align="center">
  <img width="500" src="/Task 4/BEQ.png">
</p>

---

**```Instruction 9: SW R3, R1, 2```**

<p align="center">
  <img width="500" src="/Task 4/SW.png">
</p>

---

**```Instruction 10: LW R13, R1, 2```**

<p align="center">
  <img width="500" src="/Task 4/LW.png">
</p>

</details>  

-----------------------------------

<details>
<summary><b>Task 5:</b> Implementation of any circuit utilizing VSDSquadron Mini and verify that the RISCV processor's C program file upload and construction are successful</summary> 

# Shipment Tracking System

## Overview
The Shipment Tracking System integrates an MPU6050 accelerometer sensor with the CH32V003 RISC-V processor to provide real-time tracking of shipment conditions. This system monitors movement, tilt, and vibrations, ensuring that shipments are handled appropriately during transit. The MPU6050 sensor communicates detected motion data to the CH32V003 processor, which processes the information and triggers alerts if any irregularities are detected. By leveraging this technology, the project offers an efficient and automated solution for shipment monitoring and tracking.

## Components Required
- CH32V003 RISC-V Processor
- MPU6050 Accelerometer and Gyroscope Sensor
- Power Supply
- Jumper Wires

## System Specifications
### CH32V003 RISC-V Processor
- Voltage: 1.8V to 3.6V
- Communication Protocols: I2C, SPI, UART
- GPIO Pins: Configurable for interfacing with external devices

### MPU6050 Accelerometer Sensor
- Voltage: 3.3V or 5V
- Features: Acceleration and angular velocity detection across three axes
- Communication Protocol: I2C

## Circuit Connections
<p align="center">
  <img width="500" src="/Task 5/circuit_image.png">
</p>

### Connections:
1. **MPU6050 VCC**: Connect to `VIN` of CH32V003.
2. **MPU6050 GND**: Connect to `GND` of CH32V003.
3. **MPU6050 SCL (I2C Clock)**: Connect to `PC2` of CH32V003.
4. **MPU6050 SDA (I2C Data)**: Connect to `PC1` of CH32V003.

### Pinout Diagram:

| Component          | CH32V003x Pin |
|--------------------|---------------|
| MPU6050 VCC       | VIN           |
| MPU6050 GND       | GND           |
| MPU6050 SCL       | PC2            |
| MPU6050 SDA       | PC1            |

## How to Program

The following code initializes the MPU6050 sensor and processes motion data to detect irregularities. If an alert condition occurs, the inbuilt LED on the CH32V003 processor blinks to indicate an issue.

```c
#include <ch32v00x.h>
#include <debug.h>
#include <stdlib.h>

/* MPU6050 Register Addresses */
#define MPU6050_ADDR 0x68
#define MPU6050_PWR_MGMT_1 0x6B
#define MPU6050_ACCEL_CONFIG 0x1C
#define MPU6050_ACCEL_XOUT_H 0x3B
#define MPU6050_WHO_AM_I 0x75

/* Tilt Detection Parameters */
#define TILT_THRESHOLD 15000  // Raw accelerometer threshold
#define I2C_TIMEOUT 1000      // Timeout for I2C operations

/* Global Variable */
int16_t accelX, accelY, accelZ;
uint8_t tiltDetected = 0;

/* Function Prototypes */
void GPIO_Config(void);
void MPU6050_Init(void);
void MPU6050_Read_Accel(void);
void Check_Tilt(void);
void I2C_WriteByte(uint8_t addr, uint8_t reg, uint8_t data);
uint8_t I2C_ReadByte(uint8_t addr, uint8_t reg);

void GPIO_Config(void) {
    GPIO_InitTypeDef GPIO_InitStructure = {0};
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE);
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_6;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOD, &GPIO_InitStructure);
}

void MPU6050_Init(void) {
    uint8_t whoAmI;
    
    // Reset the device
    I2C_WriteByte(MPU6050_ADDR, MPU6050_PWR_MGMT_1, 0x80);
    Delay_Ms(100);  // Wait for reset to complete
    
    // Wake up the device
    I2C_WriteByte(MPU6050_ADDR, MPU6050_PWR_MGMT_1, 0x00);
    Delay_Ms(100);
    
    // Verify device ID
    whoAmI = I2C_ReadByte(MPU6050_ADDR, MPU6050_WHO_AM_I);
    if (whoAmI != 0x68) {
        printf("MPU6050 not found! WHO_AM_I = 0x%02X\r\n", whoAmI);
        while(1);  // Stop if device not found
    }
    
    // Configure accelerometer for ±2g range
    I2C_WriteByte(MPU6050_ADDR, MPU6050_ACCEL_CONFIG, 0x00);
    Delay_Ms(10);
    
    printf("MPU6050 initialized successfully\r\n");
}

void MPU6050_Read_Accel(void) {
    uint8_t buf[6];
    for(int i = 0; i < 6; i++) {
        buf[i] = I2C_ReadByte(MPU6050_ADDR, MPU6050_ACCEL_XOUT_H + i);
    }
    accelX = (buf[0] << 8) | buf[1];
    accelY = (buf[2] << 8) | buf[3];
    accelZ = (buf[4] << 8) | buf[5];
}

void Check_Tilt(void) {
    if (abs(accelX) > TILT_THRESHOLD || abs(accelY) > TILT_THRESHOLD) {
        if (!tiltDetected) {
            printf("TILT WARNING!\r\n");
            tiltDetected = 1;
        }
        GPIO_WriteBit(GPIOD, GPIO_Pin_6, SET);  // LED ON
    } else {
        tiltDetected = 0;
        GPIO_WriteBit(GPIOD, GPIO_Pin_6, RESET);  // LED OFF
    }
}

void IIC_Init(u32 bound, u16 address) {
    GPIO_InitTypeDef GPIO_InitStructure = {0};
    I2C_InitTypeDef I2C_InitTSturcture = {0};

    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOC | RCC_APB2Periph_AFIO, ENABLE);
    RCC_APB1PeriphClockCmd(RCC_APB1Periph_I2C1, ENABLE);

    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_2;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_AF_OD;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOC, &GPIO_InitStructure);

    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_1;
    GPIO_Init(GPIOC, &GPIO_InitStructure);

    I2C_InitTSturcture.I2C_ClockSpeed = bound;
    I2C_InitTSturcture.I2C_Mode = I2C_Mode_I2C;
    I2C_InitTSturcture.I2C_DutyCycle = I2C_DutyCycle_2;
    I2C_InitTSturcture.I2C_OwnAddress1 = address;
    I2C_InitTSturcture.I2C_Ack = I2C_Ack_Enable;
    I2C_InitTSturcture.I2C_AcknowledgedAddress = I2C_AcknowledgedAddress_7bit;
    I2C_Init(I2C1, &I2C_InitTSturcture);

    I2C_Cmd(I2C1, ENABLE);
}

void I2C_WriteByte(uint8_t addr, uint8_t reg, uint8_t data) {
    uint16_t timeout = I2C_TIMEOUT;
    
    while(I2C_GetFlagStatus(I2C1, I2C_FLAG_BUSY) && --timeout);
    if (!timeout) {
        printf("I2C busy timeout\r\n");
        return;
    }
    
    I2C_GenerateSTART(I2C1, ENABLE);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_MODE_SELECT) && --timeout);
    if (!timeout) {
        printf("I2C start timeout\r\n");
        return;
    }
    
    I2C_Send7bitAddress(I2C1, addr << 1, I2C_Direction_Transmitter);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_TRANSMITTER_MODE_SELECTED) && --timeout);
    if (!timeout) {
        printf("I2C address timeout\r\n");
        return;
    }
    
    I2C_SendData(I2C1, reg);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_BYTE_TRANSMITTED) && --timeout);
    if (!timeout) {
        printf("I2C register timeout\r\n");
        return;
    }
    
    I2C_SendData(I2C1, data);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_BYTE_TRANSMITTED) && --timeout);
    if (!timeout) {
        printf("I2C data timeout\r\n");
        return;
    }
    
    I2C_GenerateSTOP(I2C1, ENABLE);
}

uint8_t I2C_ReadByte(uint8_t addr, uint8_t reg) {
    uint8_t data;
    uint16_t timeout = I2C_TIMEOUT;
    
    while(I2C_GetFlagStatus(I2C1, I2C_FLAG_BUSY) && --timeout);
    if (!timeout) {
        printf("I2C busy timeout\r\n");
        return 0;
    }
    
    I2C_GenerateSTART(I2C1, ENABLE);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_MODE_SELECT) && --timeout);
    if (!timeout) {
        printf("I2C start timeout\r\n");
        return 0;
    }
    
    I2C_Send7bitAddress(I2C1, addr << 1, I2C_Direction_Transmitter);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_TRANSMITTER_MODE_SELECTED) && --timeout);
    if (!timeout) {
        printf("I2C address timeout\r\n");
        return 0;
    }
    
    I2C_SendData(I2C1, reg);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_BYTE_TRANSMITTED) && --timeout);
    if (!timeout) {
        printf("I2C register timeout\r\n");
        return 0;
    }
    
    I2C_GenerateSTART(I2C1, ENABLE);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_MODE_SELECT) && --timeout);
    if (!timeout) {
        printf("I2C restart timeout\r\n");
        return 0;
    }
    
    I2C_Send7bitAddress(I2C1, addr << 1, I2C_Direction_Receiver);
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_RECEIVER_MODE_SELECTED) && --timeout);
    if (!timeout) {
        printf("I2C receive mode timeout\r\n");
        return 0;
    }
    
    I2C_AcknowledgeConfig(I2C1, DISABLE);
    I2C_GenerateSTOP(I2C1, ENABLE);
    
    timeout = I2C_TIMEOUT;
    while(!I2C_CheckEvent(I2C1, I2C_EVENT_MASTER_BYTE_RECEIVED) && --timeout);
    if (!timeout) {
        printf("I2C receive timeout\r\n");
        return 0;
    }
    
    data = I2C_ReceiveData(I2C1);
    I2C_AcknowledgeConfig(I2C1, ENABLE);
    return data;
}

int main(void) {
    USART_Printf_Init(115200);
    printf("\r\nMPU6050 Tilt Detection Starting...\r\n");
    
    Delay_Init();
    GPIO_Config();
    IIC_Init(400000, 0x00);  // Increased to 400kHz
    MPU6050_Init();
    
    while(1) {
        MPU6050_Read_Accel();
        Check_Tilt();
        Delay_Ms(100);
    }
}

void NMI_Handler(void) {}
void HardFault_Handler(void) {
    while (1) {}
}
```




