# ARUX Project Roadmap

This document outlines the phased development plan for ARUX. ARUX is an ambitious project, but it can be approached pragmatically and in stages.

## Phase 1: The Foundation

*   **Create the ARUX DE (Desktop Environment):**
    *   Port Zune as a basic desktop environment for Linux. This involves adapting Zune/MUI to run natively on a Linux graphics server (Wayland/X11).
    *   Focus on core functionalities: window management, basic Wanderer file manager operations, and essential preferences applications.
*   **Implement the "Graphics Pipe":**
    *   Develop a mechanism to redirect the video output of a standard Amiberry (or a compatible 68k emulator) into a native window managed by the ARUX DE.
    *   Technologies like PipeWire could be explored for efficient video stream handling.
    *   This step aims to provide an integrated visual experience even before full native integration is achieved.

## Phase 2: The Dual Engine

*   **Fork Amiberry to create the ARUX Execution Engine:**
    *   Establish a dedicated fork of the Amiberry emulator which will serve as the base for the ARUX Execution Engine.
    *   This fork will diverge to incorporate the dual execution modes.
*   **Develop "Native Integration Mode":**
    *   Implement the necessary modifications in the Amiberry fork to disable chipset emulation selectively.
    *   Create the high-performance bridge to translate AmigaOS API calls (from 68k applications) into native Linux/Vulkan calls.
    *   This mode will act as a 68k "process container."
*   **Develop Proxy Libraries for Modified AROS 68k:**
    *   Adapt AROS 68k libraries (initially focusing on `intuition.library`, `graphics.library`, `dos.library`) to become "proxies."
    *   These proxy libraries will not interact with emulated hardware but will instead communicate with the ARUX Execution Engine to request resources and actions from the Linux host system.
    *   Initial focus should be on supporting popular productivity applications.

## Phase 3: The Ecosystem

*   **Refine the ARUX SDK:**
    *   Develop and document a Software Development Kit (SDK) for ARUX.
    *   This SDK should facilitate the creation of new native software that leverages the ARUX architecture, combining Amiga's design philosophy with modern hardware capabilities.
    *   Provide tools, examples, and documentation for developers.
*   **Create Configuration and Management Tools:**
    *   Develop user-friendly tools for managing and configuring ARUX.
    *   This includes a centralized control panel for the ARUX Execution Engine, allowing users to manage settings for both Native Integration Mode and Full Compatibility Mode.
    *   Tools for managing software installation and system updates.
*   **Community Engagement and Expansion:**
    *   Actively engage with the AROS and Amiga communities to gather feedback and encourage contributions.
    *   Expand hardware compatibility and software support based on community needs and contributions.

This roadmap is a living document and may be updated as the project progresses.
