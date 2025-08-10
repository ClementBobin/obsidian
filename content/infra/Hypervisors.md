# Introduction to Hypervisors 
A **hypervisor** is a software or hardware platform that allows you to create and run virtual machines (VMs) on a physical host machine. These virtual machines are isolated from each other and share the host machine's physical resources. 
## Types of Hypervisors 
### Type 1 Hypervisor 
Type 1 hypervisors, also known as **bare-metal hypervisors**, run directly on the host's hardware to control the hardware and to manage guest operating systems. They do not require a host operating system. Type 1 hypervisors are often used in enterprise environments and data centers due to their performance and security. 

**Examples of Type 1 Hypervisors:**

- [[infra/proxmox]]: Proxmox Virtual Environment is an open-source Type 1 hypervisor that combines two virtualization technologies: KVM (Kernel-based Virtual Machine) for virtual machines and LXC (Linux Containers) for lightweight container-based virtualization.
- [[Docker]]: Docker can also be considered a Type 1 hypervisor when using tools like Docker Desktop for Mac and Docker Desktop for Windows. It uses a lightweight Linux VM to run containers directly on the host OS.
### Type 2 Hypervisor 
Type 2 hypervisors, also known as **hosted hypervisors**, run on top of a host operating system and are ideal for desktop or development use. They are simpler to set up and are suitable for scenarios where performance is less critical. 

**Example Type 2 Hypervisor: VirtualBox** 
[[VirtualBox]] is a popular open-source Type 2 hypervisor and a logiciel developed by Oracle. It allows you to run/simulate multiple virtual machines with different guest operating systems on your desktop or laptop computer (physical). It's versatile, user-friendly, and great for testing and development. 

**Example Type 2 Hypervisor: VMware

[VMware Workstation ](obsidian://open?vault=tech&file=infra%2FVMware%20Workstation) (formerly known as VMware Infrastructure) is a leading Type 2 hypervisor. It provides a robust virtualization platform for running multiple VMs on a single physical server. 
## Key Features of Hypervisors 
1. **Isolation**: Hypervisors provide strong isolation between virtual machines, ensuring that the actions or issues in one VM do not affect others. 
2. **Resource Management**: They efficiently allocate and manage physical resources like CPU, memory, and storage among VMs. 
3. **Snapshotting**: Hypervisors often support creating snapshots, allowing you to save the state of a VM at a particular point in time and revert to it later. 
4. **Live Migration**: Advanced hypervisors enable the live migration of VMs between host machines with little to no downtime. 
5. **Hardware Emulation**: They provide virtualized hardware interfaces to VMs, abstracting physical hardware details. 
6. **Security**: Hypervisors enhance security by isolating VMs, making it difficult for malware in one VM to affect others or the host. 
## Choosing the Right Hypervisor 
The choice between Type 1 and Type 2 hypervisors depends on your use case. Type 1 hypervisors are suitable for performance-critical environments, while Type 2 hypervisors are more convenient for desktop or development purposes. VMware and VirtualBox are just two examples of hypervisors, and there are many others available, each with its own strengths and weaknesses. When selecting a hypervisor, consider factors like performance requirements, ease of use, licensing, and support. 
## Conclusion 
Hypervisors play a crucial role in modern computing by enabling the efficient use of hardware resources and the creation of isolated virtual environments. Whether you're running a data center or setting up a virtual lab on your laptop, understanding the different types of hypervisors and their features will help you make informed decisions about which one best suits your needs.