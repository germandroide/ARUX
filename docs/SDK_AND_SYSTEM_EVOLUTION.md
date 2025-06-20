# ARUX: SDK, System Evolution, and Synergies

This document outlines the vision for the ARUX Software Development Kit (SDK), the evolution of the AROS ecosystem within ARUX, and the potential for synergies with other Amiga-like operating systems and the broader Linux world.

## The ARUX SDK: Bridging Classic and Modern Development

The ARUX SDK aims to empower developers to create software that feels native to the Amiga/AROS environment while leveraging the full power of the underlying Linux system and modern hardware.

**Key Goals for the SDK:**
*   **Hybrid Development Model:**
    *   Allow developers to write applications primarily targeting the AROS 68k API.
    *   Provide clear mechanisms for these 68k applications to call upon and utilize services, libraries, and resources from the host Linux system. This could involve:
        *   Proxy libraries within the Modified AROS 68k that translate calls to Linux equivalents (e.g., for file operations, network access, modern hardware interaction).
        *   Wrapper functions or an Inter-Process Communication (IPC) bridge for more complex interactions.
    *   Enable new software to be developed with a "68k soul" but with "modern power." For instance, a classic Amiga productivity app could gain support for new file formats or online services by using Linux libraries.
*   **Native Linux Development for ARUX DE:**
    *   Provide tools and APIs for developing applications and utilities that run directly as native Linux processes but are fully integrated into the ARUX Desktop Environment (Zune/MUI). These could be new system utilities, preference panels, or even larger applications designed specifically for ARUX.
*   **Simplified Access to Modern Features:**
    *   Abstract complexities of modern hardware (e.g., GPUs via Vulkan, PipeWire for multimedia) so that AROS/68k developers can benefit from them without needing deep Linux-specific knowledge.
*   **Comprehensive Documentation and Examples:** A good SDK needs excellent documentation, tutorials, and code examples to lower the barrier to entry for both existing AROS developers and those new to the ecosystem.

## System Evolution: The Future of AROS within ARUX

ARUX is not a replacement for AROS but an evolution. It provides a platform where AROS can thrive by focusing on its strengths:

*   **Preserving AROS Compatibility:** The Modified AROS 68k ensures that a vast amount of existing AROS (and classic Amiga) software can run, either in Native Integration Mode or Full Compatibility Mode.
*   **Focusing on User Experience (Zune/MUI):** By delegating low-level hardware concerns to Linux, development effort can be concentrated on refining and extending the Zune/MUI experience, making it the most polished and user-friendly Amiga-like desktop.
*   **A Path for AROS 68k Development:** ARUX offers a compelling reason to continue developing for AROS 68k, as applications can gain new life and capabilities through the hybrid model.

## Synergies with Other Systems and Linux

ARUX aims to be an inclusive platform, drawing inspiration and potentially code from various sources:

*   **MorphOS and AmigaOS 4:**
    *   While direct binary compatibility might be complex due to different low-level kernels and APIs, ARUX can learn from the innovations and user interface advancements in MorphOS and AmigaOS 4.
    *   Where licenses permit and technical feasibility exists, specific features, libraries, or applications could be ported or adapted to run within the ARUX environment (either as 68k AROS applications or as native Linux applications integrated into the ARUX DE).
    *   The goal is to unite the best aspects of the "Amiga family" user experience under one roof.
*   **Leveraging the Linux Ecosystem:**
    *   **Application Availability:** Thousands of open-source Linux applications and libraries can potentially be made available to ARUX users, either by running them directly (if they are graphical and can be managed by the ARUX DE) or by providing AROS-compatible frontends to Linux command-line tools or services.
    *   **System Enhancements:** Linux provides a wealth of features that can enhance ARUX:
        *   Advanced networking capabilities.
        *   Modern security features.
        *   Comprehensive hardware support.
        *   Filesystem innovations.
    *   **Development Tools:** The Linux platform offers a mature and powerful set of development tools that can be used to build and improve ARUX itself.

ARUX's philosophy is to build bridges, not walls. By fostering a flexible SDK, enabling AROS to evolve in a modern context, and strategically integrating strengths from the wider Amiga and Linux communities, ARUX can become a vibrant and enduring platform.
