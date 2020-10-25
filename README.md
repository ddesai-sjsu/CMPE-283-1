# CMPE-283-1
Assignment-1

### Functionality to be Implemented
--> Read the VMX configuration MSRs to ascertain support capabilities/features - Entry / Exit / Procbased / Secondary Procbased / Pinbased controls
--> For each group of controls above, interpret and output the values read from the MSR to the system
via printk(..), including if the value can be set or cleared.

Following are the steps to be followed for the same:

1)Use the following command to clone the master linux git repository in your system.
    --> git clone https://github.com/torvalds/linux.git

2)Switch to the "linux" folder:
    --> cd linux

3) Create a new directory named “CMPE-283-1” in the “linux” folder using following command.
    --> mkdir CMPE-283-1

4)Copy the files “Makefile” and cmpe283-1.c into this newly created directory.

5)Quering all the MSRs:
---> Create different structures with name and bit positions for probased, secondry procbased, entry and exit controls. Refer SDM to get the instructions.

-->In order to detect VMX capabilities of the CPU, "detect_vmx_features" function is written which inturn calls  the function "report_capability" with appropriate parameters to print pinbased, procbased, entry and exit controls, 

--> In order to check if Secondary Procbased controls are available, a new function, "check_bit_63" is called to check 63rd bit of IA32_VMX_PROCBASED MSR. If this bit is set, then secondary procbased controls are available and another function will be called to print the corresponding secondary procbased capabilities.

6) Switch to the CMPE-283-1 folder:
--> cd CMPE-283-1

7) Build the module using the following command in the  CMPE-283-1 folder:
--> make all

8) Load and unload the module using below commands:

When a module is inserted into the kernel, the module_init macro would be invoked, which will call the function init_module.
Similarly, when the module is removed with rmmod, module_exit macro will be invoked, which will call the cleanup_module.

---> sudo insmod cmpe283-1.ko

---> sudo rmmod cmpe283-1.ko

9)      The VMX features gets logged in the kernel log and which can be verified using the dmesg command:
> dmesg
