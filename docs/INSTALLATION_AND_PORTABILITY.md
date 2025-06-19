# ARUX: Installation and Portability

ARUX is designed with flexibility in mind, catering to different user needs and use cases. This document outlines the planned approaches for installing and running ARUX.

## Standard Installation (Like a Common Linux Distribution)

For users who wish to use ARUX as their primary or a regularly used operating system on a dedicated machine or partition, ARUX will offer a standard installation process similar to many common Linux distributions.

*   **Installer:** A user-friendly graphical installer will be developed or adapted to guide users through the installation process.
    *   Partitioning options (use existing partitions, guided partitioning).
    *   Bootloader installation (e.g., GRUB).
    *   User account creation.
    *   Localization options (language, keyboard layout).
*   **Underlying Linux Base:** The installation will set up the necessary Linux base system (kernel, drivers, core utilities) upon which the ARUX Desktop Environment and Execution Engine will run. The specific base distribution (e.g., Debian, Arch) is yet to be determined but will be chosen for stability, hardware compatibility, and ease of maintenance.
*   **Post-Installation:** Once installed, ARUX will boot directly into the Zune/MUI desktop environment, providing an immediate Amiga-like experience.

This method is ideal for:
*   Desktop computers or laptops dedicated to ARUX.
*   Dual-boot setups alongside other operating systems.
*   Virtual machine installations.

## Portable USB Mode (Live System like Batocera)

Inspired by successful portable emulation systems like Batocera Linux, ARUX will also be designed to run as a fully functional, live operating system from a USB flash drive or external hard drive.

*   **Live Environment:** The USB version will contain the complete ARUX system, requiring no installation to the host computer's internal storage.
*   **Persistence (Optional):**
    *   Users will have the option to enable persistence on the USB drive. This means that any changes made (system settings, installed software, saved games, user files) will be saved back to the USB drive and will be available across sessions.
    *   If persistence is not enabled, ARUX will run in a pristine state on each boot from the USB.
*   **Bootable on Various Hardware:** The live USB will be configured to be bootable on a wide range of PC hardware (x86/64) and potentially ARM devices that support USB booting (like the Raspberry Pi).
*   **"Plug and Play" Amiga Experience:** This mode allows users to carry their ARUX environment with them and use it on different computers, transforming them temporarily into ARUX/Amiga machines.

This method is ideal for:
*   Trying out ARUX without making changes to a host computer.
*   Portable retro gaming and Amiga setups.
*   Demonstrations and presentations.
*   Users who prefer not to install additional operating systems on their main machines.

## Unified System, Flexible Deployment

It's important to note that both the installable version and the portable USB version will run the same core ARUX system. The difference lies in the deployment method and storage handling, not in the features or capabilities of ARUX itself. This ensures a consistent experience regardless of how ARUX is launched.

This dual approach to availability aims to make ARUX accessible to the widest possible audience, from dedicated enthusiasts to casual users looking for an easy way to experience a modern Amiga-like system.
