# Secure Boot for embedded systems

Secure boot is a critical security mechanism designed to protect embedded systems against various threats, such as physical memory modification and malicious code injection.

When you power on an embedded device, it initiates a boot process. This process involves the execution of boot code stored on the device’s chip, and in some cases, it simultaneously launches additional code and applications. Once the boot process concludes, the device becomes operational.

However, when Secure Boot is in place, code doesn’t run simply because it resides on the device. Secure Boot’s primary function is to ensure that only code signed by the device’s manufacturer is executed.

Once the secure code begins execution, any additional code and applications will only run if their signature is valid. This creates a hierarchical “chain of trust” where each layer of code and application is executed only if the correct key validates it.

```mermaid
flowchart TD
    A(RESET) --> B{i.MX Boot ROM Code}
    subgraph B[i.MX Boot ROM Code]
        F1[HAB Library]
    end
    B --> C{Is Signed U-Boot Valid?}
    B -- Loaded By --> K["Signed U-boot (U-Boot + CSF)"]
    C -- No --> D[STOP Execution]
    C -- Yes --> E[Signed U-Boot]
    subgraph E[Signed U-Boot]
        F2[Calls Into HAB Library]
    end
    E -- Loaded By --> L["Signed OS (OS+CSF)"]
    E --> F{Calls i.MX HAB Library}
    F --> G[Loads Signed OS]
    G --> H{Is Signed OS Valid?}
    H -- No --> D[STOP Execution]
    H -- Yes --> I[Execute Signed OS]
```

<br> <br>
