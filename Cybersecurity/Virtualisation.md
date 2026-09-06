# Virtualization

## What I learned

I learned that virtualisation allows multiple virtual computers to share the resources of one physical computer.

Before virtualisation, organisations often needed a separate physical server for each application. This could be expensive and inefficient because many servers were not using all of their available resources.

## Hypervisor

A **hypervisor** is software that creates and manages virtual machines (VMs).

It can:

* Allocate CPU, memory and storage to VMs
* Keep VMs isolated from each other
* Start, stop, pause, clone and delete VMs
* Manage the resources used by each VM

## Types of Hypervisors

There are two main types:

### Type 1

A Type 1 hypervisor runs directly on the physical hardware.

It is commonly used in servers and data centres.

### Type 2

A Type 2 hypervisor runs on top of an existing operating system.

It is useful for learning, testing and running virtual machines on a personal computer.

Examples include VirtualBox and VMware Workstation.

## Virtual Machines

A **virtual machine (VM)** is a virtual computer created by a hypervisor.

A VM can have its own:

* CPU
* RAM
* Storage
* Network
* Operating system

For example, I can run a Kali Linux VM on a computer without needing a separate physical computer.

VMs are also isolated from each other, so an issue with one VM should not normally affect the others.

## Containers

I also learned about containers.

A container is a lightweight, isolated environment used to run an application and its dependencies.

Unlike a VM, a container shares the host operating system's kernel. This makes containers faster to start and generally less resource-intensive than full VMs.

## Docker

**Docker** is a platform used to build, deploy and run applications using containers.

## Practical Learning

I used a virtualisation management environment to investigate a VM that had entered an error state, restart it, create a new VM with specific resources, and examine the resource usage of physical hosts.

This helped me understand how virtual machines are managed in a practical environment.
