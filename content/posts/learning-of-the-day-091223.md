+++
title= "Learnings of the Day 09/12"
date= '2023-12-09'
draft= 'false'
tags= ["learning", "OS", "queue"]
categories= ["OS"]
+++

# Learnings of the Day

Today's exploration led to insightful learnings in the realm of operating systems, process lifecycles, creation of processes, termination, and scheduling algorithms.

## Process Lifecycle:

### Importance:
1. **Resource Management:**
   - Efficient allocation and deallocation of resources prevent leaks and ensure availability for other processes.
   
2. **Multitasking and Concurrency:**
   - Understanding lifecycles supports concurrent execution and efficient context switching, crucial for multitasking.

3. **System Stability and Reliability:**
   - Lifecycle stages ensure isolation, preventing interference between processes and contributing to system stability.
   - Facilitates error handling, enhancing system reliability.

4. **Security:**
   - Lifecycle supports process isolation, a key factor in enforcing security measures.

5. **Scheduling and Prioritization:**
   - Directly influences scheduling decisions, optimizing fairness and efficiency.

## Creation of Processes:

### Key Components:
1. **Parent Process:**
   - Initiates the creation of a new process and may handle responsibilities such as resource initialization.

2. **Child Process:**
   - Newly created process, often sharing the same memory space initially.

3. **Process ID (PID):**
   - Unique identifier assigned to each process.

4. **Address Space:**
   - Processes have distinct address spaces, including memory for code, data, and stack.

5. **Execution Context:**
   - Includes registers, program counter, and necessary information for execution.

## Termination of Processes:

### Process Termination:
1. **Exit System Call:**
   - Primary mechanism for terminating a process, involves cleanup and optional exit code.

2. **Process Termination by Parent:**
   - Parent processes can explicitly terminate child processes using system calls.

3. **Abnormal Termination:**
   - Occurs due to errors or exceptional conditions, may result in core dumps.

### Key Concepts:
1. **Process Exit Status:**
   - Numerical value indicating termination status.

2. **Cleanup Operations:**
   - Involves releasing resources and closing open files.

3. **Parent Process Handling:**
   - Uses the `wait` system call to wait for child processes to terminate.

4. **Graceful Shutdown:**
   - Processes implement procedures for saving data or notifying other processes before termination.

## Introduction to Scheduling Algorithms:

### Importance of Scheduling:
1. **Resource Utilization:**
   - Maximizes CPU utilization for efficient task execution.

2. **Throughput:**
   - Enhances the system's capacity to complete more processes in a given time frame.

3. **Fairness:**
   - Ensures equitable access to the CPU for all processes, preventing resource starvation.

4. **Responsiveness:**
   - Influences how quickly processes can start and complete execution.

### Common Scheduling Algorithms:
1. **FCFS, SJF, Priority, RR, Multilevel Queue, Multilevel Feedback Queue:**
   - Varied algorithms with distinct principles and trade-offs.

### Considerations in Scheduling:
1. **Preemption, Starvation, Turnaround Time, Waiting Time, Burst Time:**
   - Factors influencing scheduling decisions and overall system performance.

Today's journey encompassed foundational OS concepts, process management, and the intricacies of scheduling algorithms, contributing to a holistic understanding of system dynamics.
