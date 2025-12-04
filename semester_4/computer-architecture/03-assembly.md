# Addressing Modes in Assembly

## Implied Addressing Mode
- **Definition**: In this mode, the data used by the instruction is inherent in the instruction itself, and no operand is explicitly mentioned.
- **Explanation**: The operation acts on a predefined or implicit data location (e.g., accumulator) or performs a specific action that doesn't require additional data.
- **Example**:
  - **Instruction**: `CLR` (Clear accumulator)
  - **Operation**: Clears the contents of the accumulator without referencing any memory or register explicitly.

---

## Immediate Addressing Mode
- **Definition**: In this mode, the operand is directly specified in the instruction as a constant value.
- **Explanation**: The data is part of the instruction, so the CPU doesn't need to fetch it from memory or a register.
- **Example**:
  - **Instruction**: `MOV A, #10`
  - **Operation**: Moves the immediate value `10` into the accumulator (`A`).

---

## Register Addressing Mode
- **Definition**: In this mode, the operand is stored in a CPU register, and the instruction specifies the register.
- **Explanation**: Accessing data in registers is faster than accessing memory, as registers are located inside the CPU.
- **Example**:
  - **Instruction**: `ADD A, B`
  - **Operation**: Adds the contents of register `B` to the accumulator (`A`).

---

## Direct (or Absolute) Addressing Mode
- **Definition**: In this mode, the operand is located at a specific memory address, which is explicitly mentioned in the instruction.
- **Explanation**: The instruction provides the exact address where the data is located.
- **Example**:
  - **Instruction**: `MOV A, 0x2000`
  - **Operation**: Moves the value at memory address `0x2000` into the accumulator (`A`).

---

## Register Indirect Addressing Mode
- **Definition**: In this mode, a register contains the memory address of the operand, and the instruction accesses the data indirectly via the register.
- **Explanation**: The register acts as a pointer to the memory location.
- **Example**:
  - **Instruction**: `MOV A, @R0`
  - **Operation**: Moves the value at the memory address stored in register `R0` into the accumulator (`A`).

---

## Indexed Addressing Mode
- **Definition**: In this mode, the effective address of the operand is calculated by adding a constant (offset) to the contents of a register.
- **Explanation**: Commonly used for accessing arrays or data structures in memory.
- **Example**:
  - **Instruction**: `MOV A, 0x2000[R1]`
  - **Operation**: Moves the value at the memory address `0x2000 + R1` into the accumulator (`A`).

---

## Summary Table

| **Addressing Mode**      | **Description**                                                                                     | **Example Instruction**       |
|--------------------------|----------------------------------------------------------------------------------------------------|--------------------------------|
| **Implied**              | Data is implicit in the instruction.                                                              | `CLR`                         |
| **Immediate**            | Data is a constant value specified in the instruction.                                            | `MOV A, #10`                  |
| **Register**             | Operand is stored in a register.                                                                  | `ADD A, B`                    |
| **Direct (Absolute)**    | Data is at a specific memory address mentioned in the instruction.                                 | `MOV A, 0x2000`               |
| **Register Indirect**    | Register contains the memory address of the operand.                                              | `MOV A, @R0`                  |
| **Indexed**              | Effective address is calculated by adding a constant (offset) to a register's contents.           | `MOV A, 0x2000[R1]`           |

