# Virtualization

## Container
- create isolated user-space instances
- share the host operating system kernel
- maintain separate process trees, network interfaces, and file systems
- lightweight, faster startup time, and efficient resource utilization

## Virtual machine
- complete computing instances that include their own operating system, kernel, drivers, and applications
- strong isolation but requires significant memory and storage resources for each OS instance

## Hypervisor with Type-1 architecture
- complete virtual machines with separate guest operating systems
    - running on top of the hypervisor layer
- Type-1 hypervisors run directly on physical hardware
- strong isolation but requiring full OS instances for each virtual machine

## Network Functions Virtualization platform (NFV)
- virtualizes traditional network services like firewalls, load balancers, and routers as software applications
- NFV can utilize various virtualization technologies including containers
