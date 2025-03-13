Refrence: https://stormagic.com/company/blog/all-about-hypervisors-esxi-vs-hyper-v-xenserver-proxmox-kvm-ahv/

Virtualization is a technology that allows multiple virtual machines (VMs) to run on a single physical machine, sharing its resources like CPU, memory, and storage. This enables efficient use of hardware resources, improved flexibility, and better management of IT infrastructure.


## How Server Virtualization Works

1. **Hypervisor**:  A special software called a **hypervisor** (like VMware, VirtualBox, or Proxmox) divides these resources into smaller parts.
    
2. **Virtual Machines (VMs)**: Each VM runs its own operating system and applications, isolated from other VMs on the same host.
    
3. **Resource Allocation**: The hypervisor dynamically allocates resources like CPU, memory, and storage to each VM based on demand.
    

## Use Cases

1. **Server Consolidation**: Reduce the number of physical servers by consolidating them into fewer, more efficient virtual servers.
    
2. **Development and Testing**: Create isolated environments for development and testing without affecting production systems.
    
3. **Disaster Recovery**: Use virtualization to quickly recover servers in case of hardware failures or disasters.


 ## How does virtualization work?
*Virtualization depends on 2 important concepts: virtual machines and hypervisors.*

### Virtual machines

A **virtual machine (VM)** is like a "computer within a computer." It’s a software-based environment that acts like a real computer with its own:

- **CPU** (processing power),
    
- **Memory** (RAM),
    
- **Storage** (hard drive),
    
- **Operating System** (like Windows, Linux, or macOS),
    
- **Network Interface** (to connect to the internet or other devices).
    

Even though it’s just software, it behaves like a separate, independent computer.

### **How Does a VM Work?**

1. **Hardware Resources**:
    
    - A physical computer (called the **host**) has resources like CPU, RAM, and storage.
        
    - A special software called a **hypervisor** (like VMware, VirtualBox, or Proxmox) divides these resources into smaller parts.
        
2. **Creating a VM**:
    
    - The hypervisor creates a virtual machine by allocating some of the host’s resources (e.g., 2 CPU cores, 4GB RAM, 50GB storage).
        
    - You can install an operating system (like Windows or Linux) on the VM, just like you would on a physical computer.
        
3. **Isolation**:
    
    - Each VM is isolated from the host and other VMs. If one VM crashes, it won’t affect the others.
        
4. **Portability**:
    
    - A VM is essentially a **single file** (or a set of files). You can move this file to another computer, open it there, and it will work the same way.

### **Example of a VM in Action**

Imagine you have a powerful laptop running **Windows** as the host operating system. You want to:

- Test a **Linux** program without installing Linux on your laptop.
    
- Run an old **Windows XP** application that doesn’t work on modern Windows.
    

Here’s how you can do it with VMs:

1. **Install a Hypervisor**:
    
    - Install software like **VirtualBox** or **VMware** on your Windows laptop.
        
2. **Create Two VMs**:
    
    - **VM 1**: Install Linux (e.g., Ubuntu) and allocate 2 CPU cores, 4GB RAM, and 50GB storage.
        
    - **VM 2**: Install Windows XP and allocate 1 CPU core, 2GB RAM, and 20GB storage.
        
3. **Run the VMs**:
    
    - You can now run both Linux and Windows XP on your Windows laptop at the same time.
        
    - Each VM will behave like a separate computer, and you can switch between them easily.

### **Real-World Use Cases**

1. **Software Development**:
    
    - Developers use VMs to test software on different operating systems without needing multiple physical devices.
        
2. **Server Virtualization**:
    
    - Companies use VMs to run multiple servers (like web servers, database servers) on a single physical machine.
        
3. **Legacy Applications**:
    
    - Businesses use VMs to run old software that only works on outdated operating systems (like Windows XP).
        
4. **Education and Training**:
    
    - Students and IT professionals use VMs to learn about different operating systems and networking.


### Hypervisors

A **hypervisor** is like a **traffic cop** for your computer’s resources (CPU, memory, storage, etc.). It manages these resources and divides them among multiple **virtual machines (VMs)**, so each VM can run its own operating system (OS) and applications.

### **How Does a Hypervisor Work?**

1. **Physical Resources**:
    
    - Your computer or server has physical resources like CPU, RAM, and storage.
        
    - The hypervisor takes these resources and splits them into smaller parts.
        
2. **Allocating Resources**:
    
    - It assigns these smaller parts to different VMs.
        
    - For example, if your computer has 16GB of RAM, the hypervisor might give 4GB to one VM, 8GB to another, and keep 4GB for itself.
        
3. **Managing VMs**:
    
    - The hypervisor ensures that each VM runs smoothly without interfering with others.
        
    - If a VM needs more resources (e.g., more CPU power), the hypervisor handles the request.

### **Types of Hypervisors**

There are **two types** of hypervisors, depending on where they are installed:

---

#### **Type 1: Bare-Metal Hypervisor**

- **What it is**:
    
    - Installed directly on the physical hardware (no need for an operating system).
        
    - Acts as the **operating system** for the hardware.
        
- **Example**:
    
    - Imagine you have a powerful server in a data center.
        
    - You install a Type 1 hypervisor (like **VMware ESXi** or **Microsoft Hyper-V**) directly on the server.
        
    - Now, you can create multiple VMs on that server, each running its own OS (like Windows, Linux, etc.).
        
- **Use Case**:
    
    - Commonly used in **data centers** and **enterprise environments** for running multiple servers on a single machine.
        

---

#### **Type 2: Hosted Hypervisor**

- **What it is**:
    
    - Installed on top of an existing operating system (like Windows, macOS, or Linux).
        
    - Acts as a **software application**.
        
- **Example**:
    
    - Imagine you have a laptop running **Windows**.
        
    - You install a Type 2 hypervisor (like **VirtualBox** or **VMware Workstation**) as an application.
        
    - Now, you can create VMs on your laptop, like running **Linux** or **macOS** inside Windows.
        
- **Use Case**:
    
    - Great for **individual users** who want to run multiple operating systems on their personal computer.


### **Real-World Example**

#### **Type 1 Hypervisor (Bare-Metal)**:

- A company has a powerful server in its data center.
    
- They install **VMware ESXi** (a Type 1 hypervisor) directly on the server.
    
- Now, they can run:
    
    - A **web server** (Linux),
        
    - A **database server** (Windows),
        
    - And a **development environment** (macOS),
        
    - All on the same physical server.
        

#### **Type 2 Hypervisor (Hosted)**:

- You have a Windows laptop.
    
- You install **VirtualBox** (a Type 2 hypervisor) as an application.
    
- Now, you can run:
    
    - A **Linux VM** for programming,
        
    - A **Windows XP VM** for running old software,
        
    - And a **macOS VM** for testing,
        
    - All on your laptop.
        

## Types of Virtualization

There are several types of virtualization, each serving different purposes:

1. **Server Virtualization:**
    
    - **Purpose:** Divide a physical server into multiple virtual servers, each running its own operating system.
        
    - **Benefits:** Increased resource utilization, easier management, and improved scalability.
        
    - **Examples:** VMware ESXi, Microsoft Hyper-V, KVM.
        
2. **Desktop Virtualization:**
    
    - **Purpose:** Run multiple desktop environments on a single physical machine.
        
    - **Benefits:** Centralized management, improved security, and easier deployment of desktops.
        
    - **Examples:** VMware Horizon, Citrix Virtual Apps and Desktops.
        
3. **Application Virtualization:**
    
    - **Purpose:** Run applications in isolation from the underlying operating system.
        
    - **Benefits:** Simplified deployment, reduced conflicts between applications, and improved security.
        
    - **Examples:** VMware ThinApp, Microsoft App-V.
        
4. **Network Virtualization:**
    
    - **Purpose:** Create virtual networks that are independent of the physical network infrastructure.
        
    - **Benefits:** Improved network management, increased flexibility, and better security.
        
    - **Examples:** VMware NSX, Cisco ACI.
        
5. **Storage Virtualization:**
    
    - **Purpose:** Abstract storage resources into a single pool, making them easier to manage.
        
    - **Benefits:** Improved storage utilization, simplified management, and enhanced data protection.
        
    - **Examples:** SAN (Storage Area Network), NAS (Network-Attached Storage).
        
6. **Hardware Virtualization:**
    
    - **Purpose:** Use hardware components like CPUs and GPUs to support virtualization.
        
    - **Benefits:** Improved performance for VMs, better support for virtualized environments.
        
    - **Examples:** Intel VT-x, AMD-V.
        
7. **OS-Level Virtualization (Containerization):**
    
    - **Purpose:** Run multiple isolated systems on a single kernel.
        
    - **Benefits:** Lightweight, efficient, and fast deployment.
        
    - **Examples:** Docker, Kubernetes.


## Server Virtualization
Server virtualization is a technology that allows multiple virtual servers to run on a single physical server, sharing its resources like CPU, memory, and storage. This enables efficient use of hardware resources, improved flexibility, and better management of IT infrastructure.

### Key Benefits of Server Virtualization

1. **Resource Utilization**: By running multiple VMs on a single server, you can maximize resource usage and reduce hardware costs.
    
2. **Flexibility and Scalability**: Easily add or remove virtual servers as needed, without having to purchase new hardware.
    
3. **Improved Management**: Simplify server management by using a single interface to manage multiple VMs.
    
4. **Enhanced Security**: Isolate VMs from each other, improving security by containing potential issues within individual VMs.
    
5. **Disaster Recovery**: Easily backup and restore VMs, reducing downtime in case of failures.
    

###
Popular Server Virtualization Platforms

1. **VMware ESXi**: A leading commercial virtualization platform known for its robust features and scalability.
    
2. **Microsoft Hyper-V**: A popular choice for Windows environments, offering strong integration with Microsoft products.
    
3. **KVM (Kernel-based Virtual Machine)**: An open-source solution integrated into the Linux kernel, offering cost-effective virtualization.
    
4. **Xen**: Another open-source hypervisor known for its high performance and security features.
    