# 2-Pass Assembler - Pass 1

This README file provides an overview of the Pass 1 algorithm for a 2-pass assembler and describes the C program implemented for Pass 1. Additionally, it explains the processes that occur during Pass 1.

## Pass 1 Algorithm

The Pass 1 algorithm is the initial phase of a 2-pass assembler, responsible for generating a symbol table and calculating the location counter (LC) for each instruction in the source code. Below is the algorithm for Pass 1:

1. Open the input source file (`input.txt`) and the symbol table file (`symtab.txt`) in read and write modes, respectively.

2. Initialize variables: `lc` (location counter), `sa` (starting address), `l` (line number), `op1` (operand value), `o` (operation code), and `len` (length).

3. Read the first line from the input file, which typically contains the program's starting address using the `START` directive. If `START` is present, set `sa` and `lc` accordingly. Print the information.

4. Read the next line from the input file.

5. Loop through the input file until the end is reached (EOF).

6. For each line read, parse the line into `la` (label), `m1` (operation mnemonic), and `op` (operand).

7. Print the current line's information, including `lc`, `la`, `m1`, and `op`.

8. If `la` is not equal to "-", write the line's information to the symbol table file (`symtab.txt`).

9. Open the opcode table file (`optab.txt`) in read mode.

10. Loop through the opcode table file, searching for a match between `m1` and the operation mnemonic in `otp`.

11. If a match is found, increment `lc` by 3 (assuming a standard instruction format) and break out of the loop.

12. Close the opcode table file.

13. Check if `m1` is one of the following directives: "WORD," "RESW," "BYTE," or "RESB."

14. Update `lc` based on the type of directive:
    - For "WORD," increment `lc` by 3.
    - For "RESW," convert `op` to an integer and increment `lc` by 3 times the integer value.
    - For "BYTE," calculate the length of `op` and increment `lc` accordingly.
    - For "RESB," convert `op` to an integer and increment `lc` by the integer value.

15. Read the next line from the input file.

16. Continue steps 6-15 until the end of the input file is reached.

17. If the last line of the input file contains the "END" directive, print the program's length as `lc - sa`.

18. Close both the input file and the symbol table file.

## Pass 1 C Program Description

The provided C program performs Pass 1 of the 2-pass assembler algorithm. It reads an input source file (`input.txt`), processes each line, generates a symbol table (`symtab.txt`), and calculates the location counter (`lc`). Here is a brief description of the program:

- The program begins by opening the input source file (`input.txt`) and the symbol table file (`symtab.txt`) for reading and writing, respectively.

- It initializes variables for tracking `lc`, `sa`, `l`, `op1`, `o`, and `len`, as well as character arrays for `m1`, `la`, `op`, and `otp`.

- The program reads the first line to determine the starting address (`sa`) and initializes the location counter (`lc`). If `START` is not found, `lc` starts at 0.

- It then reads each line of the source code, parsing it into `la`, `m1`, and `op`, printing the information as it goes.

- If `la` is not "-", it writes the line's information to the symbol table file (`symtab.txt`).

- The program opens the opcode table file (`optab.txt`) and searches for the operation code (`m1`) in the opcode table (`otp`). If found, it increments `lc` accordingly.

- Depending on the type of directive or operation (`m1`), the program adjusts `lc` as described in the algorithm.

- Finally, the program checks if the last line contains the "END" directive, and if so, it calculates and prints the program's length (`lc - sa`).

- The input file and symbol table file are closed after processing.

This program is designed to perform Pass 1 of the 2-pass assembler, which is responsible for generating a symbol table and calculating the location counter for each instruction. The symbol table (`symtab.txt`) will be used in Pass 2 to generate the object code.