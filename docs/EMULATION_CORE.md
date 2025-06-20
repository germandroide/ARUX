# ARUX: The Emulation Core

ARUX is designed not just with an Amiga look and feel, but with emulation at its heart. This document details how ARUX plans to integrate Amiberry as its primary Amiga emulation engine and how it will extend its capabilities to manage other emulators and cores, providing a unified and powerful retro-computing experience.

## Amiberry: The Heart of Amiga Emulation in ARUX

ARUX will feature a deeply integrated and optimized fork of **Amiberry** as its core engine for Amiga 68k software compatibility. The choice of Amiberry is based on several factors:

*   **High Compatibility:** Amiberry offers excellent compatibility with a wide range of Amiga hardware (OCS, ECS, AGA) and software.
*   **Actively Developed:** It's a vibrant open-source project with ongoing development and improvements.
*   **Performance:** Particularly on ARM platforms like the Raspberry Pi (relevant for PiStorm integration), Amiberry is highly optimized.
*   **Feature-Rich:** It supports many features crucial for a good user experience, such as WHDLoad support, JIT compilation, custom controls, and more.
*   **Open Source:** Its GPL license aligns with ARUX's open-source nature, allowing for the necessary forking and modification.

Within ARUX, the Amiberry fork will serve dual purposes as the **ARUX Execution Engine**:
1.  **Full Compatibility Mode:** Providing high-fidelity Amiga hardware emulation for games and demos.
2.  **Native Integration Mode:** Acting as a 68k "process container" for desktop applications, translating AmigaOS API calls to native Linux calls.

## Beyond Amiga: Multi-Emulator Capabilities

While Amiga emulation is central, ARUX aims to be a versatile retro-computing platform. It will draw inspiration from systems like EmulationStation to manage and launch other emulators and cores, but with a deeper OS-level integration.

*   **RetroArch Core Integration:** ARUX will be designed to seamlessly run RetroArch cores. This instantly provides access to emulation for a vast number of other classic consoles and computers.
*   **Standalone Emulator Support:** Where a RetroArch core might not be the best option, ARUX will allow for the integration of specific standalone emulators.
*   **Unified Interface:** The goal is to launch and manage these different emulators from within the ARUX Desktop Environment, providing a consistent user experience. Users shouldn't have to drop to a different interface to launch different types of emulated systems.

## Centralized Emulation Configuration Panel

A key feature of ARUX will be a centralized system configuration panel dedicated to emulation. This panel, accessible from the ARUX DE, will allow users to manage:

*   **BIOS Management:**
    *   Easy uploading, organization, and assignment of BIOS/Kickstart ROM files for different emulated systems (Amiga, various consoles, etc.).
    *   Verification of BIOS files.
*   **Display Options:**
    *   **Bezels and Overlays:** Applying graphical bezels or overlays for a more authentic or customized visual experience, applicable per emulator or globally. This can be for windowed mode or fullscreen.
    *   **Shaders:** Application of pixel shaders (e.g., CRT shaders, upscaling filters) to enhance or modify the visual output of emulators. These can be configured globally or on a per-system/per-game basis.
    *   **Aspect Ratio and Scaling:** Fine-grained control over aspect ratio, integer scaling, and other display parameters.
*   **Core/Emulator Settings:**
    *   Predetermining which core or emulator to use for specific game/file types.
    *   Access to common settings for individual emulators/cores without needing to delve into each emulator's native UI (where possible).
*   **Controller Configuration:** Centralized mapping of game controllers for different emulated systems.
*   **Save State Management:** Potentially a unified interface for managing save states across different emulators, if feasible.

This centralized approach simplifies the management of a diverse emulation library, making ARUX a powerful yet user-friendly hub for all things retro. The deep OS integration means that features like the "Graphics Pipe" (redirecting emulator output to a native ARUX DE window) can be leveraged for all integrated emulators, ensuring a consistent look and feel.

## Advanced Per-Window Emulation Controls

Beyond global settings in the centralized panel, ARUX aims to provide fine-grained control over emulated content directly at the window level. When an application or game is running within an ARUX DE window via the ARUX Execution Engine (especially in Full Compatibility Mode or for other integrated emulators), users will have access to context-specific options for that window:

*   **Per-Window Display Options:**
    *   **Shader Application:** Quickly apply or change pixel shaders specifically for that window. This allows, for example, trying out different CRT effects or scaling filters on the fly for a particular game without altering global defaults.
    *   **Aspect Ratio & Scaling:** Adjust aspect ratio or scaling for the content within that specific window.
*   **Emulator/Core Specific Settings (Contextual):**
    *   Access to a subset of relevant settings for the active emulator or core directly from its window frame or a context menu. This could include things like controller profiles, specific compatibility hacks, or performance adjustments relevant to the running software.
*   **Output Target Control (Key for PiStorm/Multi-monitor):**
    *   **Render to Specific Monitor:** A crucial feature, especially for PiStorm integration, will be the ability to direct the rendering output of a specific emulated window to a designated monitor.
        *   For a PiStorm setup, this would allow a game window running in ARUX (on the Pi) to be displayed on the physical monitor connected to the Amiga's native video output (e.g., Denise/Lisa).
        *   In a multi-monitor Linux setup, this would allow users to drag emulated systems to different screens or assign them specific displays.
    *   This feature enhances the flexibility of ARUX, allowing seamless integration with both modern multi-monitor setups and authentic retro hardware displays.

These per-window controls aim to provide an intuitive and powerful way to manage and customize the emulation experience directly where the user is focused, complementing the global settings available in the main configuration panel.
