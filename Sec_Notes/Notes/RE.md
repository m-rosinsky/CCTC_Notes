# Reverse Engineering Notes

## Understand x86_64 Assembly

#### General Registers

- AX - Accumulator
- BX - Base
- CX - Counter
- DX - Data

#### Index Registers

- SI - Source Index
- DI - Destination Index

#### Stack Registers

- SP - Stack Pointer
- BP - Base Pointer

#### Flag Register

- CF (0) Carry Flag
- PF (2) Parity Flag
- AF (4) Auxilliary Carry Flag
- ZF (6) Zero Flag
- SF (7) Sign Flag
- TF (8) Trace Flag
- IF (9) Interrupt Flag
- DF (10) Direction Flag
- OF (11) Overflow Flag

## Returning Values

- Return value typically stored in the AX general register.

## Common Terms

- Heap
- Stack
- General Register
- Control Register
- Flags Register

## Memory Offset

- Instruction Pointer (IP)
- Holds address of next instruction to be executed

## RE Workflow

1. Static
2. Behavioral
3. Dynamic
4. Disassembly
5. Document Findings

## Ghidra (Static Analysis)

- New Project
- Drag executable to project
- Open and analyze

String Search:
1. Search > For Strings
