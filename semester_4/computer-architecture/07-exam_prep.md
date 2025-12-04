## **Components of CPU**

The Central Processing Unit (CPU) is the brain of a computer and consists of several key components:

1. **Arithmetic Logic Unit (ALU)**: Performs arithmetic (addition, subtraction, etc.) and logical operations (AND, OR, NOT).
    
2. **Control Unit (CU)**: Directs the operation of the processor. It fetches, decodes, and executes instructions.
    
3. **Registers**: Small, fast storage locations within the CPU used to hold data and instructions temporarily.
    
    - Examples: Program Counter (PC), Instruction Register (IR), Accumulator (ACC).
        
4. **Cache Memory**: A small, high-speed memory that stores frequently accessed data to speed up processing.
    
    - Levels: L1 (fastest, smallest), L2, L3 (larger, slower).
        
5. **Clock**: Synchronizes the operations of the CPU. Measured in Hertz (Hz), it determines how many instructions the CPU can execute per second.
    
6. **Bus Interface Unit (BIU)**: Manages data transfer between the CPU and other components via buses.
    

---

## **Alternative Computational Architecture**

These are non-von Neumann architectures that differ from the traditional sequential processing model:

1. **Harvard Architecture**: Separates memory for instructions and data, allowing simultaneous access. Used in DSPs and microcontrollers.
    
2. **Quantum Computing**: Uses qubits to perform computations based on quantum mechanics principles like superposition and entanglement.
    
3. **Neural Networks/Neuromorphic Computing**: Mimics the human brain’s structure and function for AI and machine learning tasks.
    
4. **Dataflow Architecture**: Executes instructions based on data availability rather than a fixed sequence.
    
5. **Parallel Processing**: Uses multiple processors or cores to execute tasks simultaneously.
    
    - Examples: SIMD (Single Instruction, Multiple Data), MIMD (Multiple Instruction, Multiple Data).
        

---

## **GPUs (Graphics Processing Units)**

- **Purpose**: Designed to handle parallel tasks, especially graphics rendering and complex mathematical computations.
    
- **Architecture**: Contains thousands of smaller, efficient cores optimized for parallel processing.
    
- **Applications**:
    
    - Graphics rendering (gaming, 3D modeling).
        
    - Machine learning and AI (training neural networks).
        
    - Scientific simulations and data analysis.
        
- **Comparison with CPUs**:
    
    - CPUs: Fewer cores, optimized for sequential tasks.
        
    - GPUs: Many cores, optimized for parallel tasks.
        

---

## **Peripherals**

Peripherals are external devices that interact with the computer:

1. **Input Devices**: Keyboard, mouse, scanner, microphone.
    
2. **Output Devices**: Monitor, printer, speakers.
    
3. **Storage Devices**: Hard drives, SSDs, USB flash drives.
    
4. **Communication Devices**: Modems, network cards, routers.
    

---

## **RAM (Random Access Memory)**

- **Purpose**: Volatile memory used to store data and instructions temporarily while the computer is running.
    
- **Types**:
    
    1. **SRAM (Static RAM)**:
        
        - Built with latches (flip-flops).
            
        - Faster and more expensive than DRAM.
            
        - Does not need to be refreshed.
            
        - Used in cache memory.
            
    2. **DRAM (Dynamic RAM)**:
        
        - Built with capacitors.
            
        - Slower and cheaper than SRAM.
            
        - Requires periodic refreshing to maintain data.
            
        - Used in main memory (RAM sticks).
            

---

## **Data Buses**

- **Definition**: A communication system that transfers data between components inside a computer.
    
- **Types**:
    
    1. **Address Bus**: Carries memory addresses from the CPU to RAM.
        
    2. **Data Bus**: Transfers actual data between the CPU, memory, and peripherals.
        
    3. **Control Bus**: Carries control signals (read, write, interrupt).
        
- **Width**: Determines how much data can be transferred at once (e.g., 32-bit, 64-bit).
    

---

## **Assembly: Addressing Modes**

Addressing modes define how the CPU accesses operands:

1. **Immediate Addressing**: Operand is a constant value (e.g., `MOV AX, 5`).
    
2. **Direct Addressing**: Operand is a memory address (e.g., `MOV AX, [1234]`).
    
3. **Register Addressing**: Operand is in a register (e.g., `MOV AX, BX`).
    
4. **Indirect Addressing**: Operand’s address is in a register (e.g., `MOV AX, [BX]`).
    
5. **Indexed Addressing**: Operand’s address is calculated using a base address and an index (e.g., `MOV AX, [BX+SI]`).
    
6. **Relative Addressing**: Operand’s address is relative to the program counter (e.g., `JMP +10`).
    

---

## **Heap and Stack**

- **Stack**:
    
    - A LIFO (Last In, First Out) data structure.
        
    - Used for function calls, local variables, and control flow.
        
    - Managed automatically by the CPU.
        
    - Fast access but limited in size.
        
- **Heap**:
    
    - A dynamic memory area for allocating memory at runtime.
        
    - Used for global variables and objects.
        
    - Managed manually (in languages like C) or automatically (in garbage-collected languages like Java).
        
    - Slower access but larger in size.
        

---

## **Memory Address Maps**

- **Definition**: A layout of how memory is allocated to different components (RAM, ROM, peripherals).
    
- **Purpose**: Ensures that each device has a unique address range.
    
- **Example**:
    
    - RAM: 0x0000 to 0x7FFF.
        
    - ROM: 0x8000 to 0xFFFF.
        
    - Peripherals: 0x10000 to 0x1FFFF.
        

---

## **Semaphore**

- **Definition**: A synchronization tool used in concurrent programming to control access to shared resources.
    
- **Types**:
    
    1. **Binary Semaphore**: Acts as a mutex (mutual exclusion) with two states (0 or 1).
        
    2. **Counting Semaphore**: Allows a fixed number of threads to access a resource.
        
- **Operations**:
    
    - **Wait (P)**: Decrements the semaphore value. If the value is negative, the thread is blocked.
        
    - **Signal (V)**: Increments the semaphore value and wakes up a waiting thread