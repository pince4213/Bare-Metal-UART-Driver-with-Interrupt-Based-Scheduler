# Bare-Metal UART Driver with Interrupt-Based Scheduler (ARM Cortex-M)

## 📌 Project Overview

This project demonstrates pure bare-metal embedded firmware development
on an ARM Cortex-M microcontroller without using any RTOS or high-level
abstraction libraries.

The system implements:

-   Interrupt-driven UART communication
-   Memory-mapped register programming
-   Circular buffer management
-   Hardware timer interrupt
-   Lightweight cooperative scheduler (without RTOS)
-   Low-level debugging using GDB

This project is designed to showcase real-time embedded system
fundamentals and low-level firmware development skills.

------------------------------------------------------------------------

## 🎯 Objectives

-   Understand memory-mapped peripheral configuration
-   Implement interrupt-driven communication
-   Design a cooperative task scheduler
-   Perform register-level debugging
-   Analyze stack behavior during ISR execution

------------------------------------------------------------------------

## 🧠 Key Features

-   Bare-metal ARM Cortex-M programming
-   Direct UART register configuration
-   Interrupt Service Routine (ISR) design
-   Circular buffer for non-blocking TX/RX
-   Timer-based periodic interrupt
-   Cooperative task scheduling without RTOS
-   GDB-based debugging and stack inspection

------------------------------------------------------------------------

## 🛠 Hardware Requirements

-   ARM Cortex-M board (e.g., STM32F103 / STM32F4 / LPC1768) OR
-   QEMU ARM simulation

------------------------------------------------------------------------

## 💻 Software Requirements

-   ARM GCC Toolchain
-   Make
-   OpenOCD (for flashing)
-   GDB (for debugging)
-   Serial monitor (PuTTY / Minicom)

------------------------------------------------------------------------

## 📂 Project Structure

baremetal-uart-scheduler/ │ ├── src/ │ ├── main.c │ ├── uart.c │ ├──
uart.h │ ├── timer.c │ ├── timer.h │ ├── scheduler.c │ ├── scheduler.h │
├── circular_buffer.c │ ├── circular_buffer.h │ ├── startup/ │ ├──
startup.s │ ├── linker/ │ ├── linker.ld │ ├── Makefile └── README.md

------------------------------------------------------------------------

## ⚙️ System Architecture

### UART Driver

-   Configured via memory-mapped registers
-   Interrupt-driven TX/RX
-   Circular buffer for safe data handling
-   Tested up to 921600 baud (\~90 KB/s sustained throughput)

### Timer Interrupt

-   Periodic hardware timer
-   Generates system tick
-   Drives cooperative scheduler timing

### Cooperative Scheduler

-   Round-robin execution model
-   No context switching overhead
-   Deterministic execution timing

------------------------------------------------------------------------

## 🚀 Performance

-   \~90 KB/s sustained UART throughput @ 921600 baud
-   Deterministic interrupt latency
-   Minimal RAM footprint
-   Static memory allocation strategy

------------------------------------------------------------------------

## 🔄 Execution Flow

1.  Reset → Startup handler initializes stack
2.  UART peripheral configured
3.  Timer configured
4.  Interrupts enabled
5.  Main loop executes scheduler
6.  ISR handles UART events

------------------------------------------------------------------------

## 🔐 Memory Layout

-   .text → Flash memory
-   .data → RAM (initialized variables)
-   .bss → RAM (zero-initialized variables)
-   Stack → Top of RAM

Custom linker script ensures complete memory control.

------------------------------------------------------------------------

## 🧪 Debugging

Performed using GDB:

-   Breakpoints inside ISR
-   Register inspection
-   Stack frame analysis
-   Peripheral register monitoring

Example:

break UART_IRQHandler continue info registers x/16x \$sp

------------------------------------------------------------------------

## ⚠️ Design Constraints

-   No RTOS → Lower overhead
-   Cooperative scheduling → Simpler logic
-   Interrupt-driven I/O → Better CPU utilization
-   Static allocation → Prevent heap fragmentation
-   Volatile usage for hardware registers

------------------------------------------------------------------------

## 🎓 Learning Outcomes

-   Real-time embedded system behavior
-   Interrupt flow control
-   Memory-mapped I/O fundamentals
-   Stack and register analysis
-   Bare-metal firmware debugging

------------------------------------------------------------------------

## 📈 Future Improvements

-   DMA-based UART transfer
-   Preemptive scheduler
-   CLI interface
-   Support for multiple Cortex-M variants

------------------------------------------------------------------------

## 👨‍💻 Author

Prince Viradiya\
Electronics & Communication Engineering

------------------------------------------------------------------------
