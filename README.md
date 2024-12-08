Name: Hoda Hussein ID:900223388
Name: Laila Sayed     ID: 900223389


Tomasulo Processor Simulator with Speculation
OVERVIEW
A simulation of Tomasulo's algorithm featuring speculative execution for a custom 16-bit instruction set architecture (ISA). This project demonstrates out-of-order execution, dynamic scheduling, and branch prediction, with an intuitive GUI for visualization.

Key Features
Dynamic Scheduling with Tomasulo's Algorithm:
Handles data hazards (RAW, WAR, WAW) using reservation stations and a reorder buffer (ROB).
Enables out-of-order execution for improved performance.
Speculative Execution:
Implements branch prediction and speculative execution for branch instructions.
16-bit Custom ISA:
Simulates a simplified RISC architecture with instructions like LOAD, STORE, ADD, NAND, and branch instructions.
GUI with Educational Features:
Visualizes reservation stations, reorder buffer, execution pipeline, and speculative branches.
Provides step-by-step simulation for educational purposes.

Architecture
The project simulates a simplified processor pipeline with the following components:
Instruction Fetch:
Fetches instructions from the input program and decodes them into their respective operation types and operands.
Reservation Stations (RS):
Temporary holding units for instructions waiting to execute.
Tracks operand availability and ensures that data hazards are resolved before issuing instructions to functional units.
Functional Units (FUs):
Simulates ALU operations (e.g., addition, multiplication, division) and memory operations (load/store).
Includes execution latency to model realistic timing.
Reorder Buffer (ROB):
Ensures in-order commit of instructions while allowing out-of-order execution.
Tracks speculative results to allow rollback in case of branch misprediction or exceptions.
Branch Prediction:
Implements a simple branch predictor (static or dynamic) to guide speculative execution.
Common Data Bus (CDB):
Facilitates communication of results from functional units to reservation stations, registers, and the ROB.

Code Structure
processor.py: Core processor simulation logic, including Tomasulo's algorithm.
memory.py: Simulates memory operations (LOAD/STORE).
gui.py: Implements the Tkinter-based graphical interface.
instruction.py: Defines the instruction format and parsing functions.


Assumptions
Branch Prediction: A basic branch prediction mechanism is used, with speculative execution rolled back on misprediction.

Functionality
What Works
Program Flow and Reservation Station Usage:
In normal cases without dependencies, the program utilizes reservation stations correctly, ensuring accurate execution start times and durations.
Correct Instruction Issuance and Execution:
Even with dependencies (RAW, WAR, WAW), the simulator issues instructions accurately, writes results back to the registers, and commits instructions in the correct order.
GUI and Educational Features:
The graphical interface is fully functional, aiding in the understanding of Tomasulo's algorithm and speculative execution by providing clear visualizations.
What Does Not Work
Return Instruction Behavior:
While the return instruction branches correctly, it terminates the program immediately afterward, rather than allowing continued execution or halting gracefully.

Known Issues
WAR (Write After Read) dependency is handled by stalling instead of the more sophisticated register renaming technique, which could improve performance and parallelism.


