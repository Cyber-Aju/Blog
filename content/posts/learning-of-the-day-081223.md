+++
title= "Learnings of the Day 08/12"
date= '2023-12-08'
draft= 'false'
tags= ["learning", "OS"]
categories= ["OS"]
+++

# Operating System Concepts Overview

## Introduction to Operating System (OS):

### 1. Definition of OS:
- **OS (Operating System):** A software that acts as an intermediary between computer hardware and user applications.

### 2. Why OS?
- **User-Friendly Interface:** OS provides a user-friendly interface.
- **Efficient Resource Management:** Manages hardware resources efficiently.
- **Security and Virtualization:** Ensures security and provides virtualization.

### 3. Functions of OS:
- **Resource Management:** Efficiently allocates and manages hardware resources.
- **Virtualization:** Creates a virtual environment for applications.
- **Concurrency:** Manages multiple tasks concurrently.
- **Security:** Ensures the security and integrity of the system.

## What happens when we write a program in C++:

### 1. Write Program:
- Develop code in a programming language like C++.

### 2. Compile:
- Compiler translates high-level code to machine code.

### 3. Fetch-Decode-Execute Cycle:
- CPU fetches, decodes, and executes machine code instructions.

### 4. Software Requirements:
- **RAM**
- **CPU core(s)**
- **Drivers/HDD**

## Memory Management:

### 1. System Call:
- Commands like `mmap` are system calls used to allocate memory.

### 2. How Memory Needs Are Applied:
- Determined and applied through system calls.

### 3. Language Wrapping:
- Direct system calls aren't typically used; functions like `scanf()` wrap them.

## CPU Virtualization:

### 1. Number of Programs Running:
- Infinite due to virtualization.
- Switching between programs occurs.

## Memory Virtualization:

### 1. Fetch-Decode-Execute Cycle:
- Fetch process from RAM for faster access.

### 2. Large Game, Limited RAM:
- Virtualization techniques manage memory efficiently.
- Portions of the game are loaded into RAM as needed.

## Concurrency:

### 1. Concurrency vs. Parallelism:
- Basic terms in concurrent programming.

## Running Programs and CPU Core Allocation:

### 1. Processes:
- Programs are converted into processes for execution.
- OS selects a program to run and allocates CPU.

### 2. Context Switching:
- Occurs when switching between processes.
- Involves swapping out and swapping in processes.

## Process Control Block (PCB):

### 1. Data Structure for Process Details:
- Contains information about a process.
- Relies on memory layout, registers, and metadata.

### 2. Memory Layout:
- **Stack:** Statically allocated variables like local variables.
- **Heap:** Dynamically allocated memory like pointers.
- **Data:** Global/static variables.
- **Text:** Machine code of each process.
- Intersection of stack and heap can lead to segmentation errors.

### 3. Registers:
- **Program Counter:** Current statement number that we execute.
- **Stack Pointer:** Stores the current activation record.
- **Frame Pointer:** Position in the stack where the function starts and ends.

### 4. Metadata:
- **ID:** ID of the current process.
- **Priority:** Priority of the process.
- **IO States:** Input/output states.
- **Status:** Current status of the process.
- **Limits:** Memory or time limits for the process.
