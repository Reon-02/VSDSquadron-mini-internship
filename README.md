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
-To navigate to the home directory,enter the following command
```bash 
cd
```
-To open a blank file for typing C program,enter the following command
```bash
leadfpad sum1ton.c
```
![Screenshot from 2024-10-23 00-24-08](https://github.com/user-attachments/assets/4817ccc5-8ed1-47d5-b548-e953a3ec52aa)

-After writing the program,save it and return to the terminal and enter the following command
```bash
gcc sum1ton.c
./a.out
```
![Screenshot from 2024-10-23 18-04-21](https://github.com/user-attachments/assets/37976102-6f90-4cc3-a6ef-f7182a7340d8)
-verify the result using a calculator <br>
-after verifying it go back to the editor and check the result for different values of n<br>
-recompile it and verify the output

![Screenshot from 2024-10-23 17-58-22](https://github.com/user-attachments/assets/b9f4dd62-28e7-4a34-8a6f-3cf89823f2d2)

##  Task 2:To compile the C code using RISC-V compiler 
### Step:1
-To display the content of the C code in the terminal,use the following command
```bash
cat sum1ton.c
```
![Screenshot from 2024-10-21 19-19-04 - 3](https://github.com/user-attachments/assets/4de3e364-be40-4e2d-af7b-18b75c4a369a)
### Step:2
-TO run the C code using RISC-V compiler,enter the following command
```bash
riscv64 -unknown -elf -gcc -01 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```








