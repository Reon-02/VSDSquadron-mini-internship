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
- 

  
  









