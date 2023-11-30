# Distributed-Systems
## Problems of a Centralized System
* Performance and Storage
* Single Point of failure - loss of money and trust
* High latency - poor user experience
* Security and Privacy

## Distributed System
**A set of cooperating computers communicating with each other over the network to get some coherent task done --OR--**
**A Distributed System is a system of several processes running on different computers, communicating with each other through the network and are sharing a state or working together to achieve a common goal.**


> Try everything else (single computer) before even trying distributed systems

## Why do we consider ds?
* Parallelism (performance; lots of disk arms moving parallelly, lots of cpu cores working for single task)
* Fault Tolerance (two computers exactly do the same thing and if one of them fails, we have a backup)
* Problems thats are naturally spread out in space(Inter bank transfer; two machines need to communicate; machines are inherently distant and communicate over narrowly defined network protocols)
* Security (isolated; if code in one computer is corrupted or injected; code in another machine is safe)

## Challenges with distributed systems:
Failure patterns: In a single computer, either computer is working or not working; but in ds, we have multiple systems and networks. so we can have partial failures
Performance: Requires careful design to achieve Parallelism.

## What is a process?
**A program loaded into the memory is then called a process. --OR-- Running instance of a program.**

**All the processes running on single computer share the resources of the host and communicate via file system, network or some advanced techniques provided by the OS. This is not
a distributed system as all the processes belong to a single host**

**What if we launch processes on different host machines and make them communicate via network to perform a job? -> That's it! this is distributed system.**



  
