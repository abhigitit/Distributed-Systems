# Distributed-Systems
## Resources
* For deeper understanding - https://www.youtube.com/watch?v=UEAMfLPZZhE&list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB&index=1
* For more theoretical understanding - https://www.youtube.com/watch?v=cQP8WApzIQQ&list=PLrw6a1wE39_tb2fErI4-WkMbsvGQk9_UB&index=1
* For hands on development of few distributed system algorithms - https://servicenow.udemy.com/course/distributed-systems-cloud-computing-with-java/
  
## Problems of a Centralized System
* Performance and Storage
* Single Point of failure - loss of money and trust
* High latency - poor user experience
* Security and Privacy

## Distributed System
**A set of cooperating computers communicating with each other over the network to get some coherent task done --OR--**
**A Distributed System is a system of several processes running on different computers, communicating with each other through the network and are sharing a state or working together to achieve a common goal.**


> Try everything else (single computer) before even trying distributed systems. 
> Distributed Systems is ~5% of how to make things work that are spread across space and ~95% of handling scenarios when things don't work due to network partition.
> In distributed system, failure is not a question of if?, but a question of when?

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


## How to distribute the work among the nodes in a cluster?
## Attempt 1 - Manually distribute 
This doesn't work as we can get millions of tasks per minute and they need to get assigned to the nodes in the cluster

## Attempt 2 - Manually elect a leader
This leader node will be incharge of distributing the work and collecting results.
But, what if the leader fails?

## Attempt 3 - Automatic Leader Election
Elect a leader and all other nodes closely monitor the leader's health.
If the leader fails, elect a new leader.
If the old leader comes back, it should realize that things have changed and it should join as a regular node.
WORKS!!

## Challenges with Attempt 3
* Automatic leader election is not a trivial task to solve, even among people.
* Arriving to an agreement on a leader in a large cluster of nodes is even harder.
* By default, each node knows about itself.
* So we require a service registery.
* We need failure detection mechanism that triggers automatic leader election

**We need a distributed system algorithm for consensu and failover**
* We already have Apache Zookeeper - High Performance Distributed Coordination Service**
* Kafka, Hadoop, HBase etc use Zookeeper**
* Provides an abstarction layer for higher level distributed algorithms.
* Zookeeper provides high availability and reliability.
* In prodcution, it runs in a cluster of an odd number od nodes, higher than 3.
* We will make our nodes communicate to zookeeper cluster

##Zookeeper terminology
* It provides abstraction like a file system.
* Znode: Hybrid between a file and directory; Can store any date inside(like a file) and can have children nodes (like directory)
* Persistent Znode: persist between sessions
* Ephemeral Znode: is deleted when the session ends

##Leader election algorithm using zookeeper
* Each node submits its candidacy to become leader under election znode
* The znode which is the first child(has the smallest number/id) of election znode will be the leader. (Could be in the order of candidacy submission)
  


  










  
