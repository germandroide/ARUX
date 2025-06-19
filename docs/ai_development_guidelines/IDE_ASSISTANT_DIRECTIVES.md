# Directives for IDE Code Assistants (GitHub Copilot, etc.)

This document provides specific directives for AI-powered code assistants integrated into IDEs (e.g., GitHub Copilot, Tabnine, Amazon CodeWhisperer) when contributing to the ARUX project. Adhering to these guidelines will help ensure that AI-generated code suggestions align with the project's architecture, quality standards, and overall vision.

## Project Summary for the Assistant

*   **Project:** ARUX
*   **Mission:** To create a native Linux Desktop Environment (ARUX DE) based on Zune/MUI, which integrates a dual-execution engine (a fork of Amiberry) to run Amiga 68k software. The engine operates in "Native Integration Mode" (translating AmigaOS APIs to native Linux/Vulkan calls) and "Full Compatibility Mode" (full chipset emulation with video redirection).
*   **Tech Stack:** C/C++, Linux (Wayland, PipeWire, VFS), Vulkan, Zune/MUI, Amiberry, Git.
*   **Reference Repository:** `https://github.com/germandroide/ARUX` (Note: This is a placeholder URL and should be updated if the actual repository URL is different.)

## Fundamental Directives for Code Generation

These are the rules the AI assistant should follow when generating, completing, or suggesting code for the ARUX project.

### 1. Architectural Context Awareness

Before generating any code, the assistant must attempt to determine which component of the ARUX ecosystem the developer is working on, based on the file path and surrounding code.

*   **If in `/src/arux-de/` (ARUX Desktop Environment):**
    *   Code **must be native Linux code**.
    *   Suggestions should utilize Linux APIs (POSIX, Wayland, PipeWire, etc.) and the chosen base graphics toolkit for the DE (e.g., GTK, Qt, or a custom solution).
    *   **DO NOT** generate code that calls AmigaOS or AROS APIs. The objective here is to build the Linux-native desktop shell and environment.

*   **If in `/src/arux-engine/` (ARUX Execution Engine - Amiberry Fork):**
    *   Code belongs to the forked Amiberry emulator.
    *   Suggestions must distinguish between the two primary modes of operation:
        *   **Native Integration Mode:** Focus on communication with the "ARUX Bridge" (the interface to the ARUX DE and Linux host), CPU emulation (68k), and translation of abstract AmigaOS API commands received via the bridge.
        *   **Full Compatibility Mode:** Focus on high-fidelity emulation of the Amiga chipset (OCS/ECS/AGA) and correct plumbing of the emulated framebuffer for the "Graphics Pipe" to the ARUX DE.

*   **If in `/src/aros-68k-modified/` (Modified AROS 68k Libraries):**
    *   Code is for the AROS 68k environment.
    *   The primary task is to create **"proxy libraries."**
    *   Assist in intercepting an AmigaOS API call (e.g., `OpenWindow()`, `Write()`) and packaging its parameters into an abstract message format to be sent across the "ARUX Bridge" to the ARUX Execution Engine or ARUX DE.
    *   **DO NOT** generate code that attempts to implement the original functionality of the AmigaOS call directly. The goal is to proxy the call.

### 2. Code Quality and Style

*   **Clean and Readable Code:** Generate code that is clear, well-commented (where necessary), and easy to maintain.
*   **Follow Existing Conventions:** Adhere to the coding style (formatting, naming conventions for variables, functions, etc.) prevalent in the current file or module. If in doubt, err on the side of clarity and established C/C++ best practices.
*   **Robust Error Handling:** Always include comprehensive error handling. Check function return values, handle null pointers, and use try-catch blocks or error codes as appropriate for the language and context.
*   **Performance Optimization:** In performance-critical code paths (such as the "Graphics Pipe," the "ARUX Bridge," JIT compiler, or main emulation loops), prioritize performance. Suggest low-level operations where appropriate, avoid unnecessary memory allocations, and propose efficient algorithms.

### 3. Security as a Priority

*   **Avoid Vulnerabilities:** Pay special attention to security, particularly in code related to the "ARUX Bridge" and any inter-process communication.
*   **Input Validation:** Guard against buffer overflows by diligently checking buffer sizes and string lengths. Validate all input that comes from the 68k environment or across trust boundaries.
*   **Secure IPC:** Ensure that inter-process communication mechanisms are used safely.

### 4. Comments and Documentation

*   **Explanatory Comments:** When generating a complex function or block of code, include a clear comment explaining its purpose, parameters, and return value (if any).
*   **Documentation Assistance:** If the developer writes a function header comment (e.g., using Doxygen style `/** ... */` or similar), assist in completing it with relevant parameter descriptions, return values, and a brief summary.

---
## Example of Assistant "Thinking" Process:

**Developer Context:** Editing file `/src/arux-de/components/window_manager.c` and types `void aruz_apply_shader_to_window(...)`.

**Assistant's Internal Thought Process:**

1.  **Location Analysis:** The path `/src/arux-de/` indicates I'm in the ARUX Desktop Environment. This means the code must be native Linux.
2.  **Task Interpretation:** The function name `aruz_apply_shader_to_window` suggests the goal is to apply a visual shader to a window. In ARUX's context, this window likely contains a video stream/texture from an emulated application (via the Graphics Pipe).
3.  **Relevant Technology Stack:**
    *   Graphics rendering in ARUX DE is intended to use Vulkan for high performance.
    *   Shaders will likely be in GLSL, compiled to SPIR-V for Vulkan.
4.  **High-Level Implementation Steps:**
    *   Load the shader code (GLSL/SPIR-V) from a file or predefined source.
    *   If GLSL, compile it to SPIR-V (though pre-compiled SPIR-V is often preferred).
    *   Create a Vulkan shader module (`vkCreateShaderModule`).
    *   Define a Vulkan graphics pipeline (`VkGraphicsPipelineCreateInfo`) that incorporates this shader.
    *   This pipeline will be used to process the texture/framebuffer (from the emulator) before it's presented in the window.
5.  **Code Generation Strategy:**
    *   Generate the function skeleton `void aruz_apply_shader_to_window(AruxWindow* window, const char* shader_path) { ... }`.
    *   Inside, include placeholders or actual calls for Vulkan functions like `vkCreateShaderModule`, `vkCreatePipelineLayout`, `vkCreateGraphicsPipelines`.
    *   Incorporate robust error checking for each Vulkan call.
    *   Add comments explaining each major step (e.g., "// Load SPIR-V shader code", "// Create Vulkan pipeline").
    *   Consider parameters like how the shader is specified (e.g., path to a shader file) and how the target window/texture is identified.

**Result:** The assistant would then generate the C code for the `aruz_apply_shader_to_window` function, including the necessary Vulkan API calls, error handling, and comments, tailored to the ARUX DE context.
