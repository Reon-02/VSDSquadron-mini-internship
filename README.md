# VSDSquadron-mini-internship
## INSTRUCTOR:Kunal Gosh
## LAB:1
## Objectives
### 1:To write a C program to calculate the sum of numbers and to verify it using appropriate commands.
### 2:Compile the same code using the RISC-V compiler to generate its assembly code. Then, evaluate the RISC-V assembly code for the sample C program by using two different compilation options.<br>
## Project Setup
- Install virtualbox
- Launch the Virual box
- Create a new Virtual Machine
- Select Linux as the operating system and under version choose Ubuntu 18.04
- Attach th VDI files to the machine
- Start the machine
##  Task 1: Write and complile a C program 
- open a terminal
- Install LeafPad,a simple text editor by running the following command<br>
``` bash
sudo-get install leafpad 
```
- To navigate to the home directory,enter the following command
```bash 
cd
```
- To open a blank file for typing C program,enter the following command
```bash
leadfpad sum1ton.c
```
![Screenshot from 2024-10-23 00-24-08](https://github.com/user-attachments/assets/4817ccc5-8ed1-47d5-b548-e953a3ec52aa)

- After writing the program,save it and return to the terminal and enter the following command
```bash
gcc sum1ton.c
./a.out
```
![Screenshot from 2024-10-23 18-04-21](https://github.com/user-attachments/assets/37976102-6f90-4cc3-a6ef-f7182a7340d8)
- verify the result using a calculator <br>
- after verifying it go back to the editor and check the result for different values of n<br>
- recompile it and verify the output

![Screenshot from 2024-10-23 17-58-22](https://github.com/user-attachments/assets/b9f4dd62-28e7-4a34-8a6f-3cf89823f2d2)

##  Task 2:To compile the C code using RISC-V compiler 
### Step:1
- To display the content of the C code in the terminal,use the following command
```bash
cat sum1ton.c
```
![Screenshot from 2024-10-23 18-20-39](https://github.com/user-attachments/assets/b1f63152-e60f-408e-af26-3a4381350fcb)
### Step:2
- To run the C code using RISC-V compiler and to generate the object file,enter the following command 
```bash
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
ls -ltr sum1ton.o
```
![Screenshot from 2024-10-23 20-24-15](https://github.com/user-attachments/assets/84aba6ea-6603-4bb1-9c7f-928219be2695)
### Step:3
- Create a new tab and enter the following command to generate the assembly code
```bash
riscv64 -unknown-elf-onjdump-d sum1ton.o
```
![Screenshot from 2024-10-23 20-26-16](https://github.com/user-attachments/assets/2ab9c361-f074-4b24-8d48-9dd9cff65fa8)
- the system will generate huge assembly code
- to get the main parts of the program, enter the following command
```bash
riscv64 -unknown-elf-objdump -d sum1ton.o | less
```
![Screenshot from 2024-10-23 20-27-01](https://github.com/user-attachments/assets/9e3ac1e7-07bb-446f-a2cd-db782070ab32)
### step:4
- to focus on the main code , enter the following command and press"n"
```bash
/main
```
![Screenshot from 2024-10-23 20-28-15](https://github.com/user-attachments/assets/1ebcfcd6-220e-4e32-a36e-4f53f62a78a3)
- count the number of instructions and verify using programmable calculator
### step:5
- return to the terminal and enter the following command
```bash
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
- repeat the steps 3&4
![Screenshot from 2024-10-23 20-31-40](https://github.com/user-attachments/assets/47e45154-cf90-48d7-80ca-aade2e0cf9a8)

## LAB 03: Debugging RISC-V Assembly Program
### Objectives
- To compile and debug a  C code in RISC-V and verify its output.
## Step:1
- Compile the following C code in the terminal
```bash
  #include<stdio.h>
  int main(){
  int i,sum=0,n=100;
  for(i=1;i<=n;++i){
  sum+=i;
  }
  printf("sum of numbers from 1  to %d is %d\n",n,sum);
  return 0;
  }
```
![1](https://github.com/user-attachments/assets/fb3a7119-249e-456d-881d-eeaf20640a7c)
## Step:2
- Compile the code using the RISC-V compiler with the following command.
```bash
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.c sum1ton.o
```
## Step:3
- Execute on spike with the following command
- This should yield the same results as before, verifying that the instructions are functioning correctly.
```bash
spike pk sum1ton.o
```
![2](https://github.com/user-attachments/assets/a21f3a5b-d6f9-401e-998d-302d0565dc56)
## Step:4
- First, open the objdump of the file using the following command.
```bash
riscv64-unknown-elf-objdump -d -sum1ton.o
riscv64-unknown-elf-objdump -d -sum1ton.o | less
```
![3](https://github.com/user-attachments/assets/a00aec28-076f-4879-80da-0ddd6c4822c1)
- To debug the assembly code, using Spike
```bash
spike -d pk sum1ton.o
```
## Step:5
### Set Prograam Counter for Debugging
- To start debugging from a specific address, check the initial memory location of the first instruction.
![3](https://github.com/user-attachments/assets/5fd5c96d-c2f7-4589-90d9-9cc36b39e919)
-As indicated in the highlighted code above, this is the initial memory location of the first instruction
- The command ```bash "until pc 0 bc100" ```is used to run the program counter until it reaches the first instruction
- ![4](https://github.com/user-attachments/assets/b3c445b9-1f3c-482d-acaf-9199e549ccc1)
## Step:6
### Inspect Register A2 Before and After Execution
-To find the content of a2, use the following command 
```bash
reg 0 a2
```
- It will start from the zero bit and press enter to run the next instruction
![5](https://github.com/user-attachments/assets/c2257b91-7bd3-4795-a75b-3800c5688c0f)
- run the following command to get the content o of a2
```bash
reg 0 a2
```
![1](https://github.com/user-attachments/assets/5c064994-2a03-4613-aab8-4c1cb6e9de2d)
- Press enter to load the next instruction
 ![2](https://github.com/user-attachments/assets/1884e55e-eb52-4f6a-a9ee-8672c571bce5)
-enter the following command and press enter to load the next instruction
```bash
reg 0 a0
```
![4](https://github.com/user-attachments/assets/84780367-c11a-4135-9d17-dd21b92aada6)

-To retrieve the content of the stack pointer, enter the following command:
```bash
reg 0 sp
```
![1](https://github.com/user-attachments/assets/50cc8766-3694-496a-bdb3-683101776b99)
- The "addi" instruction updates the stack pointer by adding an immediate value to it.
- the command "addi sp,sp,16 decreases the stack pointer by 16 in decimal or 10 in hexadecimal
### Step:6
-quit and enter the command
```bash
spike -d pk sum1ton.o
until pc 0 100b8
reg 0 b8
```
![2](https://github.com/user-attachments/assets/227ef06d-0f58-4d57-bd9c-e3dfbcffbde5)
-enter the following command to look into stack pointer
```bash
reg 0 sp
```
-Using a calculator to confirm
```bash
0xffffffb50 - 0x10 = 0xffffffb40
```
![Screenshot 2024-10-27 001322](https://github.com/user-attachments/assets/f3cf95d6-4555-4b00-8b77-182c611fd642)
- the result confirms that the command successfully decrements the stack pointer register by 0*10.

##  LAB:03
### Objectives
#### 1) List various RISC-V instruction type (R, I, S, B, U, J) after going through RISC-V software documentation

#### 2) Identify 15 unique RISC-V instructions from riscv-objdmp of your application code 

#### 3) Identify exact 32-bit instruction code in the instruction type format for 15 unique instructions

### Task:1
## - To list various RISC-V instruction types
- RISC-V (Reduced Instruction Set Computer - V) instructions are the set of commands used in RISC-V processors to perform various operations, including arithmetic, data movement, control flow, and more. RISC-V instructions are designed to be simple, modular, and extensible, making it easy to customize for specific applications or add new features.
- RISC-V instructions are divided into different categories based on functionality.
- 
### 1. R-Type (Register-Register)
- Purpose: Used for arithmetic and logical operations between two registers.<br>
- Format: opcode | rd | funct3 | rs1 | rs2 | funct7<br>
#### Fields:<br>
- opcode: Operation type (7 bits)<br>
- rd: Destination register (5 bits)<br>
- funct3: Specifies the function (3 bits)<br>
- rs1: First source register (5 bits)<br>
- rs2: Second source register (5 bits)<br>
- funct7: Additional function code (7 bits)<br>


### 2. I-Type (Immediate)
- Purpose: Used for operations involving an immediate value (constant), such as load and arithmetic with constants.
- Format: opcode | rd | funct3 | rs1 | immediate
#### Fields:
- opcode: Operation type (7 bits)
- rd: Destination register (5 bits)
- funct3: Specifies the operation (3 bits)
- rs1: Source register (5 bits)
- immediate: Immediate value (12 bits, sign-extended)


### 3. S-Type (Store)
- Purpose: Used for store operations, writing data from a register to memory.
- Format: opcode | immediate[4:0] | funct3 | rs1 | rs2 | immediate[11:5]
 #### Fields:
- opcode: Operation type (7 bits)
- funct3: Specifies the store type (3 bits)
- rs1: Base address register (5 bits)
- rs2: Source register to store (5 bits)
- immediate: Split into two parts to form a 12-bit address offset (5+7 bits) 


### 4. B-Type (Branch)
- Purpose: Used for conditional branching, changing control flow based on comparisons.
- Format: opcode | immediate[11] | immediate[4:1] | funct3 | rs1 | rs2 | immediate[10:5]
#### Fields:
- opcode: Operation type (7 bits)
- funct3: Specifies the branch condition (3 bits)
- rs1, rs2: Registers to compare (5 bits each)
- immediate: Split into multiple parts, sign-extended to 13 bits to specify the branch offset

### 5. U-Type (Upper Immediate)
- Purpose: Used to handle large immediate values, mainly for setting the upper 20 bits of a register.
- Format: opcode | rd | immediate[31:12]
#### Fields:
- opcode: Operation type (7 bits)
- rd: Destination register (5 bits)
- immediate: Immediate value, upper 20 bits (20 bits)

### 6. J-Type (Jump)
- Purpose: Used for unconditional jumps, typically for function calls.
- Format: opcode | rd | immediate[20 | 10:1 | 11 | 19:12]
#### Fields:
- opcode: Operation type (7 bits)
rd: Register to store the return address (5 bits)
immediate: 20-bit offset, sign-extended and reordered to specify the jump target address.

### Task-2:To Identify 15 unique RISC-V instructions from riscv-objdmp of your application code 
1. **`addi sp,sp,16`**
- Instruction Type:I-type (used for immediate arithmetic and load instructions)
| Field                  | value                              |
|------------------------|---------------------------------   |
|opcode                  |	0010011 (for I-type arithmetic)   |
|funct3	                 |000 (for addi)                      |
|rd	                     | sp (x2)                            | 
|rs1	                   | sp (x2)                            |
|imm[11:0]	             | -16 (0xFF0) in 12-bit signed format|
2.**`auipc a5, 0xFFFF0 `**
3.**`sub a2, a2, a0`**
4.**`jal ra, 0x102EC `**
5.**`lw a0, 0(sp) `**
6.**`lbu a5, 1944(gp) `**
7.**`bnez a5, 0x1018C `**
9.**`sd ra, 8(sp) `**
10.**`xori a5, a5, -2000 `**
11.**`slli a5, a3, 0x30 `**
12.**`bqez a5, 101f4 `**
13.**`bltu a3, a5, 138ac `**
14.**`ld a3, 16(a2) `**
15.**`add s1, s0, s1 `**











