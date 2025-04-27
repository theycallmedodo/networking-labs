# Subnetting Notes


## What is Subnetting?
Subnetting is the process of dividing a network into smaller, more efficient sub-networks (subnets).

## Why Subnet?
- Better network performance
- Easier management
- Improved security

## Key Concepts
- Subnet Mask
- Network Address
- Broadcast Address
- Range of Usable IPs

## FLSM (Fixed Length Subnet Masking)

### What is FLSM?
FLSM means using the **same subnet mask** for all subnets within a network, regardless of actual host needs.

> "All subnets are the same size."

### Why use FLSM?
- Simplicity: easy to design and manage.
- Predictable subnetting.
- Historically used in older routing protocols like RIP v1 (classful routing).

### Example:

Given `192.168.1.0/24`, and needing 4 subnets:
- Divide into 4 subnets with the **same** subnet mask `/26`.
- Each subnet has 62 usable hosts, even if some subnets need fewer.

Subnets:
- 192.168.1.0/26
- 192.168.1.64/26
- 192.168.1.128/26
- 192.168.1.192/26

Even if one subnet needs only 10 hosts, still reserves 62.

### Important:
- Simpler but wastes IP addresses if subnets have different size needs.
- Best suited for environments where uniformity is more important than efficiency.

---



## VLSM (Variable Length Subnet Masking)

### What is VLSM?
VLSM allows using different subnet masks within the same network.  
Instead of using one fixed subnet size, networks can be divided more efficiently depending on actual needs.

> "Subnetting a subnet."

### Why use VLSM?
- Optimizes IP address space.
- Reduces waste of IP addresses.
- Allows precise network design based on host requirements.

### Example:

Imagine you have the network `192.168.1.0/24` and you need:
- 1 subnet for 100 hosts
- 1 subnet for 50 hosts
- 1 subnet for 10 hosts

Using VLSM:
- First subnet: 192.168.1.0/25 → 126 usable hosts
- Second subnet: 192.168.1.128/26 → 62 usable hosts
- Third subnet: 192.168.1.192/28 → 14 usable hosts

Each subnet has the correct size without wasting IP addresses.

### Important:
- Always allocate the **largest subnets first**.
- Subnets must not overlap (each range must be separate).

---


---

