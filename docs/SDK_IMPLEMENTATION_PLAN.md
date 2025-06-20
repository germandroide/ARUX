# ARUX SDK: Implementation Plan

This document provides the technical implementation plan for the vision outlined in `SDK_AND_SYSTEM_EVOLUTION.md`. It details the architecture of the proxy libraries and bridge components that form the core of the ARUX SDK.

## 1. SDK Repository Structure

The SDK will reside in the `/sdk` directory, structured as follows:

* `/sdk/include`: Public API headers (`.h`) for developers.
* `/sdk/libs`: Source code for our reimplemented proxy libraries.
* `/sdk/tools`: Helper utilities for the SDK (e.g., build scripts, converters).
* `/sdk/examples`: Example applications demonstrating SDK usage.

## 2. Proxy Library Architecture

As per the hybrid development model, we will create a set of shared Linux libraries (`.so`) that act as a proxy or bridge between the AROS 68k API and the native Linux kernel/services.

### 2.1. `libarux-exec.so` (Exec Proxy)
* **Purpose:** To proxy the core functions of `exec.library`.
* **Implementation:**
    * `AddTask()`: Creates a native Linux `pthread`.
    * `AllocMem()`/`FreeMem()`: Manages memory using `malloc` but respects Amiga memory flags (`MEMF_PUBLIC`, `MEMF_CLEAR`) and implements memory pooling for efficiency.
    * `Ports` & `Messages`: Implements the message-passing API using efficient Linux primitives like `eventfd` and `epoll` for asynchronous I/O, forming a core part of the IPC bridge.

### 2.2. `libarux-dos.so` (DOS Proxy)
* **Purpose:** To bridge `dos.library` calls to the Linux Virtual File System (VFS).
* **Implementation:**
    * Translates Amiga-style paths (`DF0:`, `Work:`) to their corresponding Linux mount points (`/mnt/df0`, `/home/user/Work`).
    * Wraps standard C library file I/O calls (`fopen`, `fread`) to implement `Open()`, `Read()`, etc., ensuring seamless file access.

### 2.3. `libarux-intuition.so` (Intuition Proxy - The Graphics Pipe)
* **Purpose:** To translate `intuition.library` and `graphics.library` calls into modern graphics commands.
* **Implementation:**
    * `OpenWindow()`/`OpenScreen()`: Communicates with the Wayland compositor to request a window surface.
    * `Drawing functions`: Batches drawing commands and translates them into a Vulkan rendering pipeline for full hardware acceleration.
    * `IDCMP Messages`: Listens for Wayland input events (mouse, keyboard) and translates them into Intuition messages, which are then sent to the appropriate application task via the `libarux-exec` message-passing system.

This architecture enables applications written against the AROS 68k API to run with a "68k soul" but with the "modern power" of native Linux performance and integration.
