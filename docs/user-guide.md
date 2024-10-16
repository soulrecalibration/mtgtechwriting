# MTG Secure Boot Protector : Introduction & User Guide

Manufacturers of embedded systems should ensure that their devices only start with original and unmodified firmware and that only authorized configuration files and updates can be used. The original software may run on counterfeit hardware or, vice versa, counterfeit or manipulated software may run on the original hardware.

Conventional tools that are typically shipped for/with embedded systems, do not typically address the secure handling of keys used for signing the respective software. During the development lifecycle you need to apply the signatures on different SW Components (add sw components here).

MTG Secure Boot Protector offers a solution behind the tools provided by chip vendors, interfacing them using proprietary interfaces, enabling the secure life cycle management of digital certificates and secret keys needed for the secure boot management process. The securely stored and newly generated keys are then used for the application of the firmware signatures.

It is responsible for all crypto operations (encryption, signing, key generation…), which are needed for secure boot, configuration and update of embedded systems. It covers all needed elements to fully protect the firmware:

- Boot Process
- Update Process
- Protection of secret keys
- Protection of bootloader and operating system
- Encryption of the executed code (e.g., bootloader or Linux Kernel)

<br> A complete user guide for the SBP UI tool can be found [here](https://drive.google.com/file/d/1vvbeeW6nCPnptE6vyq8Dq5rl-4zgQSgg/view?usp=drive_link).
