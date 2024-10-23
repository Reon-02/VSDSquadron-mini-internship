# VSDSquadron-mini-internship
## INSTRUCTOR:Kunal Gosh
## Objectives
### 1:To write a C program to calculate the sum of numbers and to verify it using appropriate commands.
### 2:Compile the same code using the RISC-V compiler to generate its assembly code. Then, evaluate the RISC-V assembly code for the sample C program by using two different compilation options.
## Project Setup
- Install virtualbox
- Launch the Virual box
- Create a new Virtual Machine
- Select Linux as the operating system and under version choose Ubuntu 18.04
- Attach th VDI files to the machine
- Start the machine
##  Task 1: Write and complile a c program 
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
img
### step:4
- to focus on the main code , enter the following command and press"n"
```bash
/main
```
img
- count the number of instructions and verify a programmable calculator
img
### step:5
- return to the terminal and enter the following command
```bash
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```
- repeat the steps 3&4
  img




