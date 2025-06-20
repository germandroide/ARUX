# ARUX: A Strategic Proposal for the Future of AROS

## Introduction: A New Horizon for AROS

For years, the AROS community has kept the spirit of the Amiga alive, striving to create a lightweight, efficient, and compatible operating system. However, we have faced persistent historical obstacles: limited modern hardware support and the dilemma of 68k software compatibility, especially with software that directly accesses the hardware.

ARUX is not a proposal to replace AROS, but to allow it to reach its full potential. It is a strategic vision to transform AROS from a niche operating system into a cutting-edge, modern, powerful, and fully integrated desktop environment, solving its fundamental challenges once and for all.

The premise is simple: Delegate the solved problems (drivers, kernel) to the best tool available (Linux) and focus all development efforts on what makes AROS unique: its exceptional user experience (Zune).

## The Final Concept of ARUX

ARUX is a complete software ecosystem that presents itself to the user as a native Desktop Environment for Linux, with the unmistakable look and feel of Zune/MUI. Under this unified interface lies a powerful and versatile dual-execution engine, designed to offer both unprecedented integration for desktop applications and full compatibility with games and demos.

The user turns on their computer and sees the Zune desktop. They manage their files with Wanderer. They launch their applications from the dock. For them, the experience is AROS. However, beneath the surface, it is a robust and modern Linux system that provides universal access to all current hardware and software.

## The Components of ARUX

ARUX is composed of three fundamental pillars that work in perfect synergy:

1.  **ARUX DE (Desktop Environment):**
    *   A native and optimized port of Zune/MUI for Linux. It becomes a complete desktop environment that runs directly on the Linux graphics server (Wayland/X11). It is responsible for the entire user interface: window management, the Wanderer file manager, the dock, and preferences applications.

2.  **ARUX Execution Engine (Amiberry Fork):**
    *   The heart of the system. It is a fork of Amiberry that operates in two distinct modes:
        *   **Native Integration Mode:** It disables chipset emulation and acts as a 68k "process container," translating AmigaOS API calls into native Linux/Vulkan calls through a high-performance bridge.
        *   **Full Compatibility Mode:** It behaves as a high-fidelity emulator, enabling full Amiga chipset emulation to ensure maximum compatibility with games and demos that directly access the hardware.

3.  **Modified AROS 68k:**
    *   A special version of AROS 68k whose libraries (intuition, graphics, dos) have been converted into "proxies." Instead of controlling emulated hardware, these libraries communicate with the ARUX Execution Engine to request resources from the Linux host system.

## Strategies and Operation

The magic of ARUX lies in how it combines these components transparently for the user.

### Strategy 1: Native Integration for Desktop Applications
When the user launches a productivity application like PageStream or TVPaint, the ARUX engine operates in Native Integration Mode. The calls to open windows or draw graphics are intercepted by the Modified AROS 68k and translated in real-time into native Linux commands. The result is a 68k application that runs with native performance, in a real Zune window, using the GPU's hardware acceleration via Vulkan.

### Strategy 2: Full Compatibility for Games and Demos
When the user launches a game in ADF/HDF format or a WHDLoad slave, the ARUX engine operates in Full Compatibility Mode. To ensure a consistent visual experience, the emulator's final video output is redirected through a "Graphics Pipe" (using technologies like PipeWire) and painted inside a native ARUX DE window. This gives us the best of both worlds: perfect emulation and a window that seamlessly integrates into the desktop, allowing for the application of shaders and bezels from AROS.

## Key Benefits of the ARUX Model

*   **Definitive Solution to the Driver Problem:** Instant access to the world's most comprehensive hardware support. GPUs, Wi-Fi, Bluetooth, USB-C... everything works from day one.
*   **Effortless Architectural Portability:** By relying on Linux, ARUX becomes architecture-independent. Porting ARUX to x64, ARM (for devices like Raspberry Pi), RISC-V, or any future architecture becomes a much simpler task, as the heavy lifting of hardware support is already done.
*   **Real Integration and Native Performance:** Classic desktop applications run faster than ever, benefiting from modern hardware acceleration.
*   **Universal Compatibility with 68k Software:** The dilemma that has held back other Amiga-like operating systems is solved, ensuring that the vast catalog of games and the demoscene are preserved and functional.
*   **Unified User Experience:** All underlying complexity is hidden. The user lives in a coherent and elegant Zune environment, no matter what they are running.
*   **Platform for the Future:** With a native SDK, ARUX opens the door to a new generation of software that combines the design philosophy of Amiga with the power of modern hardware and APIs.

## Conclusion: The Next Logical Step

AROS was born from a passion for a vision: an elegant, efficient, and user-centric operating system. The ARUX project does not seek to abandon that vision, but to free it from the chains that have held it back.

It is time to make a bold strategic decision. To stop reinventing the wheel of low-level systems and to focus our talent and passion on what truly matters: building the most refined and powerful user experience possible. ARUX is more than a technical plan; it is a declaration that the spirit of the Amiga is not only alive but is ready to evolve and thrive in the 21st century.

Let's unite to build ARUX. Let's unite to build the future of AROS.
