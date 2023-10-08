# 2-Pass Assembler - Pass 2

This README file provides an overview of the Pass 2 algorithm for a 2-pass assembler and describes the C program implemented for Pass 2. Additionally, it explains the processes that occur during Pass 2.

## Pass 2 Algorithm

The Pass 2 algorithm is the second phase of a 2-pass assembler, responsible for generating the final object code using the information obtained in Pass 1. Below is the algorithm for Pass 2:

1. Open necessary files, including the input source file (`input.txt`), opcode table file (`optab.txt`), symbol table file (`symtab.txt`), and length file (`length.txt`).

2. Read the first line of the input source file, which typically contains the program's starting address using the `START` directive. Record the starting address (`start`) and the program's length (`len`) from the length file.

3. Initialize variables for storing addresses (`add`), labels (`label`), operation mnemonics (`mne`), operands (`operand`), and other necessary data.

4. Print the header record (`H^`) with the program name (`label`), starting address (`start`), and program length (`len`).

5. Read the next line from the input source file, which contains the first executable instruction.

6. Loop through the input source file until the "END" directive is encountered.

7. Search the opcode table (`optab.txt`) for the operation mnemonic (`mne`) to find the corresponding machine code (`op`). If found, associate the operation code with the instruction.

8. Search the symbol table (`symtab.txt`) for the operand in the current instruction to find its address (`symadd`). If found, associate the operand's address with the instruction.

9. If the operation mnemonic is "BYTE" or "WORD," handle these special cases:
   - For "WORD," print the operand as the machine code.
   - For "BYTE," extract the value from the operand and print it as the machine code.

10. Read the next line from the input source file.

11. Repeat steps 7-10 for each executable instruction in the source file.

12. After processing all instructions, print the end record (`E^`) with the starting address (`start`).

13. Close all open files.

## Pass 2 C Program Description

The provided C program performs Pass 2 of the 2-pass assembler algorithm. It reads the results of Pass 1 (symbol and length information), the input source file (`input.txt`), and the opcode table file (`optab.txt`) to generate the final object code. Here is a brief description of the program:

- The program starts by opening the input source file (`input.txt`), the opcode table file (`optab.txt`), the symbol table file (`symtab.txt`), and the length file (`length.txt`) for reading.

- It reads the first line to obtain the program's starting address (`start`) and program length (`len`) from the length file.

- The program initializes variables for storing addresses, labels, mnemonics, operands, and other necessary data.

- It prints the header record (`H^`) with the program name (`label`), starting address (`start`), and program length (`len`).

- The program then enters a loop to process each executable instruction in the input source file.

- Inside the loop, it searches for the operation code (`op`) associated with the operation mnemonic (`mne`) in the opcode table.

- It also searches for the address (`symadd`) of the operand in the symbol table.

- Depending on the instruction type, such as "BYTE" or "WORD," the program handles the operand accordingly and prints it as the machine code.

- The loop continues until the "END" directive is encountered in the input source file.

- After processing all instructions, the program prints the end record (`E^`) with the starting address (`start`).

- Finally, it closes all open files.

This program is designed to perform Pass 2 of the 2-pass assembler, which is responsible for generating the final object code using the results obtained in Pass 1. The object code is printed in the specified format, and the resulting output is a complete machine-readable program.