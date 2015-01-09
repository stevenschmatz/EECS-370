# Lecture 1: Introduction and Overview

## Purpose of the Course

EECS 370 teaches a *holistic* view of what a computer looks like, including:

* Instruction set architecture (**ISA**)
* Processor microarchitecture
* Systems architecture
    * I/O systems (how the computer interfaces with the world)
    * Memory systems (where things are stored)

## Organization of Computers

This is a general overview of the stages of design that go into making a computer:

* **Material design**: Picking the material for low-level devices such as transistors involves a knowledge of what happens at the quantum level. Which materials are effective conductors or insulators or semiconductors?
* **Devices**: Design of diodes, transistors, and other useful building blocks of circuits.
* **Circuits**: Simple gates (AND, OR, NOT), and the implementation of Boolean logic.
* **Logic and VLSI**: Implementation of combinatorial logic, clocks, sequential logic, and state machines. 
* **Microarchitecture**: Processor control, computer architecture (ISA and processor microarchitecture)

## Information about Transistors

We were asked to find statistics about the CPU chip of our phone. For reference, at the time of this writing I have an iPhone 6+, which has the Apple A8 processor with the M8 motion co-processor.

* **Clock speed** (GHz): The number of instructions that can be executed per second. For my phone, this was 1.4 GHz or \\(1.4*10^9 \approx \\) 1.4 billion instructions per second.
* **Number of cores**: The number of processing cores on the phone, where a single-threaded program can be run.
    * In 2005, physical constraints according to Denard Scaling made processors with temperatures approaching the temperature of the surface of the sun. The development of computer chips moved to more *specialized* chips working together, rather than a single chip that does everything.
    * Hence, a program will run at roughly the same speed on a computer in 2005 compared to a computer today.
    * Increasing **throughput**, not **latency**
* **Process technology** (nm): Size of the smallest device in the processor. For my phone, this was 20nm, which is on the order of hundreds of atoms.

## History of Computers

* "Astrolavos" Antikythera Mechanism (65 BC)
    * **First computer**
    * Purpose: Chronological data entry to calculate moon phases, rise/set of moon and planets
    * Brass cogwheel system
* Charles Babbage's *envisioned* Analytic Engine (1834)
    * **First modern computer**
    * Takes a large polynomial and distributes smaller computations to human computers
* ENIAC (1946)
    * **First electronic computer**
    * In fact, a part of it can be found at the entrance of the BBB at the University of Michigan!
    * 18000 vacuum tubes, 1800 instructions/sec, 3000 cubic feet
    * Problem: could not store information
* EDSAC (1949)
    * **First stored program computer**
    * Stored information in mercury
    * 650 instructions/sec, 1400 cubic feet
* IBM Mainframe computer or IBM 360 (1970)
    * **First backwards compatible computer**
    * Important because you didn't have to rewrite software every time for a new machine
    * Standardized the instruction set architecture

## Random Stuff

* NAND gates are *universal gates*: that is, you can build any logical circuit with them.
