# VSDSquadron Mini Internship 2024

##  Basic Details

**Name:** Rohith DR  
**College:** Global Academy of Technology  
**Email ID:** rohithrohith838@gmail.com

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
$ riscv64-unknown-elf-objdump -d sum.o | less  
```
* Open the debugger in another terminal by using the following command  
```
$ spike -d pk sum.o
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

### 1. R-type Instruction
In RV32, each instruction is 32 bits in size. R-type instructions perform operations on registers (not memory) and are used for various arithmetic and logical operations. The 32-bit instruction is divided into six fields:

#### R-type
 <p align="center">
  <img src="/Task 3/Instruction_R_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register where the result of the operation is stored.
- **func3** (3 bits): Specifies the type of operation performed.
- **rs1, rs2** (5 bits each): Source registers used in the operation.
- **func7** (7 bits): Further specifies the operation.

### 2. I-type Instruction
I-type instructions involve operations that use both registers and an immediate value (not memory). These instructions are used for immediate and load operations. The instruction format is as follows:

#### I-type
 <p align="center">
  <img src="/Task 3/Instruction_I_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register for the result.
- **func3** (3 bits): Specifies the type of operation.
- **rs1** (5 bits): Source register.
- **imm[11:0]** (12 bits): A 12-bit signed immediate value used in the operation.

### 3. S-type Instruction
S-type instructions are used for store operations where data is stored from a register to memory. The 32-bit instruction is divided as follows:

#### S-type
 <p align="center">
  <img src="/Task 3/Instruction_S_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[11:5]** (7 bits) and **imm[4:0]** (5 bits): The 12-bit immediate value is split across two fields, specifying the store offset.
- **rs1** (5 bits): The register containing the data to store.
- **rs2** (5 bits): The register containing the address where data should be stored.
- **func3** (3 bits): Specifies the type of store (byte, half-word, or word).

### 4. B-type Instruction
B-type instructions are used for conditional branching based on comparisons. The 32-bit instruction format is as follows:

#### B-type
 <p align="center">
  <img src="/Task 3/Instruction_B_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[12]** (1 bit), **imm[10:5]** (6 bits), **imm[4:1]** (4 bits), and **imm[11]** (1 bit): These bits form the 12-bit signed immediate used for the branch offset.
- **rs1, rs2** (5 bits each): Source registers involved in the comparison.
- **func3** (3 bits): Defines the condition used for branching.

### 5. U-type Instruction
U-type instructions are used to transfer an immediate value into the destination register. The format is simple and involves only two instructions: `LUI` and `AUIPC`.

#### B-type
 <p align="center">
  <img src="/Task 3/Instruction_B_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **rd** (5 bits): The destination register for the immediate value.
- **imm[19:0]** (20 bits): The 20-bit immediate value that is transferred to the destination register.

For example, the instruction `lui x15, 0x13579` would load the value `0x13579000` into the upper 20 bits of register `x15`.

### 6. J-type Instruction
J-type instructions are used for jump operations. These instructions are often used for loops and branching to a specified memory location. The format is as follows:

#### J-type
 <p align="center">
  <img src="/Task 3/Instruction_J_Type.png">
</p>

- **opcode** (7 bits): Specifies the type of instruction.
- **imm[20]** (1 bit), **imm[10:1]** (10 bits), **imm[11]** (1 bit), and **imm[19:12]** (8 bits): These bits form the 20-bit signed immediate for the jump address.
- **rd** (5 bits): The destination register (used for return addresses).

</details>

