# VSDSquadron Mini Internship 2024

##  Basic Details

**Name:** Rohith DR  
**College:** Global Academy of Technology  
**Email ID:** rohithrohith838@gmail.com  
**GitHub Profile:** [Rohith-DR](https://github.com/Rohith-DR?tab=repositories)  
**LinkedIN Profile:** [Rohith-DR_ECE](https://www.linkedin.com/in/rohith-dr/)

-------------------------------------------------

<details>
<summary><b>Task 1:</b> Task is to refer to C based and RISCV based lab videos and execute the task of compiling the C code using gcc and riscv compiler</summary>

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
<summary><b>Task 2:</b> Performing SPIKE Simulation and Debugging the C code with Interactive Debugging Mode using Spike</summary> 

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
 <p align="center">
  <img width="800" height="500" src="/Task 2/Objdump in -O1.png">
</p>
  
#### Objdump in -Ofast:
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


# Instructions with explaination
<details>
<summary>Now, let's analyse each instruction one by one</summary>
	
### 1) `add r6, r1, r2`
* This is an R-type instruction used for addition.
* The value in register `r1` is added to the value in register `r2`, and the result is stored in `r6`.
* Opcode for `add` = `0110011`
* rd = `r6` = `0110`
* rs1 = `r1` = `00001`
* rs2 = `r2` = `00010`
* func3 = `000`
* func7 = `0000000`

**32-bit instruction:** `0000000_00010_00001_000_0110_0110011`

---

### 2) `sub r7, r1, r2`
* This is an R-type instruction used for subtraction.
* The value in register `r2` is subtracted from the value in register `r1`, and the result is stored in `r7`.
* Opcode for `sub` = `0110011`
* rd = `r7` = `0111`
* rs1 = `r1` = `00001`
* rs2 = `r2` = `00010`
* func3 = `000`
* func7 = `0100000`

**32-bit instruction:** `0100000_00010_00001_000_0111_0110011`

---

### 3) `and r8, r1, r3`
* This is an R-type instruction used for bitwise AND.
* The value in register `r1` is ANDed with the value in register `r3`, and the result is stored in `r8`.
* Opcode for `and` = `0110011`
* rd = `r8` = `1000`
* rs1 = `r1` = `00001`
* rs2 = `r3` = `00011`
* func3 = `111`
* func7 = `0000000`

**32-bit instruction:** `0000000_00011_00001_111_1000_0110011`

---

### 4) `or r9, r2, r5`
* This is an R-type instruction used for bitwise OR.
* The value in register `r2` is ORed with the value in register `r5`, and the result is stored in `r9`.
* Opcode for `or` = `0110011`
* rd = `r9` = `1001`
* rs1 = `r2` = `00010`
* rs2 = `r5` = `00101`
* func3 = `110`
* func7 = `0000000`

**32-bit instruction:** `0000000_00101_00010_110_1001_0110011`

---

### 5) `xor r10, r1, r4`
* This is an R-type instruction used for bitwise XOR.
* The value in register `r1` is XORed with the value in register `r4`, and the result is stored in `r10`.
* Opcode for `xor` = `0110011`
* rd = `r10` = `1010`
* rs1 = `r1` = `00001`
* rs2 = `r4` = `00100`
* func3 = `100`
* func7 = `0000000`

**32-bit instruction:** `0000000_00100_00001_100_1010_0110011`

---

### 6) `slt r11, r2, r4`
* This is an R-type instruction used for set if less than.
* If the value in `r2` is less than the value in `r4`, `r11` is set to 1; otherwise, it is set to 0.
* Opcode for `slt` = `0110011`
* rd = `r11` = `1011`
* rs1 = `r2` = `00010`
* rs2 = `r4` = `00100`
* func3 = `010`
* func7 = `0000000`

**32-bit instruction:** `0000000_00100_00010_010_1011_0110011`

---

### 7) `addi r12, r4, 5`
* This is an I-type instruction used for addition with an immediate value.
* The value in register `r4` is added to `5`, and the result is stored in `r12`.
* Opcode for `addi` = `0010011`
* rd = `r12` = `1100`
* rs1 = `r4` = `00100`
* imm = `5` = `0000000000000101`
* func3 = `000`

**32-bit instruction:** `0000000000000101_00100_000_1100_0010011`

---

### 8) `sw r3, r1, 2`
* This is an S-type instruction used to store a word.
* The value in register `r3` is stored at the memory address obtained by adding `2` to the value in `r1`.
* Opcode for `sw` = `0100011`
* rs1 = `r1` = `00001`
* rs2 = `r3` = `00011`
* imm = `2` = `0000000000000010`
* func3 = `010`

**32-bit instruction:** `0000000_00011_00001_010_00010_0100011`

---

### 9) `lw r13, r1, 2`
* This is an I-type instruction used to load a word.
* A word is loaded from the memory address obtained by adding `2` to the value in `r1`, and the result is stored in `r13`.
* Opcode for `lw` = `0000011`
* rd = `r13` = `1101`
* rs1 = `r1` = `00001`
* imm = `2` = `0000000000000010`
* func3 = `010`

**32-bit instruction:** `0000000000000010_00001_010_1101_0000011`

---

### 10) `beq r0, r0, 15`
* This is a B-type instruction used for conditional branching (branch if equal).
* If the value in register `r0` equals the value in `r0`, the program counter will jump to the specified offset (`15`).
* Opcode for `beq` = `1100011`
* rs1 = `r0` = `00000`
* rs2 = `r0` = `00000`
* imm = `15` = `0000000000001111`
* func3 = `000`

**32-bit instruction:** `0000000_00000_00000_000_01111_1100011`

---

### 11) `add r14, r2, r2`
* This is an R-type instruction used for addition.
* The value in register `r2` is added to the value in `r2`, and the result is stored in `r14`.
* Opcode for `add` = `0110011`
* rd = `r14` = `1110`
* rs1 = `r2` = `00010`
* rs2 = `r2` = `00010`
* func3 = `000`
* func7 = `0000000`

**32-bit instruction:** `0000000_00010_00010_000_1110_0110011`

---

### 12) `bne r0, r1, 20`
* This is a B-type instruction used for conditional branching (branch if not equal).
* If the value in register `r0` is not equal to the value in register `r1`, the program counter will jump to the specified offset (`20`).
* Opcode for `bne` = `1100011`
* rs1 = `r0` = `00000`
* rs2 = `r1` = `00001`
* imm = `20` = `0000000000010100`
* func3 = `001`

**32-bit instruction:** `0000000_00001_00000_001_10100_1100011`

---

### 13) `addi r12, r4, 5`
* This is identical to instruction 7.

---

### 14) `sll r15, r1, r2(2)`
* This is an R-type instruction used for shift left logical.
* The value in `r1` is shifted left by the amount specified in the lower bits of `r2`, and the result is stored in `r15`.
* Opcode for `sll` = `0110011`
* rd = `r15` = `1111`
* rs1 = `r1` = `00001`
* rs2 = `r2` = `00010`
* func3 = `001`
* func7 = `0000000`

**32-bit instruction:** `0000000_00010_00001_001_1111_0110011`

---

### 15) `srl r16, r14, r2(2)`
* This is an R-type instruction used for shift right logical.
* The value in `r14` is shifted right logically by the amount specified in the lower bits of `r2`, and the result is stored in `r16`.
* Opcode for `srl` = `0110011`
* rd = `r16` = `10000`
* rs1 = `r14` = `1110`
* rs2 = `r2` = `00010`
* func3 = `101`
* func7 = `0000000`

**32-bit instruction:** `0000000_00010_1110_101_10000_0110011`

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
<summary><b>Task 4:</b> By making use of RISCV Core: Verilog Netlist and Testbench, perform an experiment of Functional Simulation and observe the waveforms</summary>  
<br>

>***NOTE:** Since the designing of RISCV Architecture and writing it's testbench is not the part of this Research Internship, so we will use the Verilog Code and Testbench of RISCV that has already been designed. The reference GitHub repository is : [iiitb_rv32i](https://github.com/vinayrayapati/rv32i/)*    
  
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
 
#### As shown in the figure below, all the instructions in the given verilog file is hard-coded. Hard-coded means that instead of following the RISCV specifications bit pattern, the designer has hard-coded each instructions based on their own pattern. Hence the 32-bits instruction that we generated in Task-2 will not match with the given instruction.  
  
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
  <img width="500" src="/Task 4/add.png">
</p>

---

**```Instruction 2: SUB R7, R1, R2```**

<p align="center">
  <img width="500" src="/Task 4/sub.png">
</p>

---

**```Instruction 3: AND R8, R1, R3```**

<p align="center">
  <img width="500" src="/Task 4/and.png">
</p>

---

**```Instruction 4: OR R9, R2, R5```**

<p align="center">
  <img width="500" src="/Task 4/or.png">
</p>

---

**```Instruction 5: XOR R10, R1, R4```**

<p align="center">
  <img width="500" src="/Task 4/xor.png">
</p>

---

**```Instruction 6: SLT R11, R2, R4```**

<p align="center">
  <img width="500" src="/Task 4/slt.png">
</p>

---

**```Instruction 7: ADDI R12, R4, 5```**

<p align="center">
  <img width="500" src="/Task 4/addi.png">
</p>

---

**```Instruction 8: BEQ R0, R0, 15```**

<p align="center">
  <img width="500" src="/Task 4/beq.png">
</p>

---

**```Instruction 9: BNE R0, R1, 20```**

<p align="center">
  <img width="500" src="/Task 4/bne.png">
</p>

---

**```Instruction 10: SLL R15, R1, R2(2)```**

<p align="center">
  <img width="500" src="/Task 4/sll.png">
</p>

</details>  
