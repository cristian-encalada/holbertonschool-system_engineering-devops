# 1. Distributed web infrastructure 

## Table of contents

  * [Distributed web infrastructure](#distributed-web-infrastructure)
      * [Specifics about this infrastructure](#specifics-about-this-infrastructure)
      * [Issues about this infrastructure](#issues-about-this-infrastructure)
  * [Bibliography](#bibliography)
  * [Tools](#tools)

## Distributed web infrastructure

The following is a distributed web infrastructure that hosts the website that is reachable via `www.foobar.com`.
<div align="center">
  <a href="https://github.com/cristian-encalada/holbertonschool-system_engineering-devops/blob/main/web_infrastructure_design/1-distributed_web_infrastructure.jpg">
    <img src="1-distributed_web_infrastructure.jpg" alt="distributed_web_infrastructure">
  </a>
</div>

### Specifics about this infrastructure

- __Explain why are you adding every additional element__
  - `A second server` is added as a replica server in order to have redundancy with the primary server.
  - `A load balancer is added` to distribute the work-load of the primary server to multiple servers, to reduce the amount of load or traffic.

- __What distribution algorithm your load balancer is configured with and how it works__

The load balancer is using a `Round Robin algorithm`, which means it sequentially distributes requests to each server one by one. After sending a request to the last server, the algorithm starts again from the first server.

This results in an approximately equal distribution of server load, with each server handling 50% of the workload in a two-server configuration.

- __Is your load-balancer enabling an Active-Active or - Active-Passive setup, explain the difference between both__

 In an Active-Active setup with a load balancer like HAProxy, workloads are distributed evenly across all available nodes to prevent any single node from becoming overwhelmed. This setup improves performance and response times because there are multiple nodes actively serving requests.

<div align="center">
  <a>
    <img src="https://www.jscape.com/hubfs/images/active_active_high_availability_cluster_load_balancer.png" alt="active-active">
  </a>

__Source__: [https://www.jscape.com/blog/](https://www.jscape.com/blog/active-active-vs-active-passive-high-availability-cluster)
</div>

However, in an Active-Passive setup, not all nodes are actively serving requests at the same time. Instead, one node remains active while the others are on standby. If the active node becomes inactive, one of the standby nodes becomes active to take over the workload.

<div align="center">
  <a>
    <img src="https://www.jscape.com/hubfs/images/active_passive_high_availability_cluster.png" alt="active-passive">
  </a>

__Source__: [https://www.jscape.com/blog/](https://www.jscape.com/blog/active-active-vs-active-passive-high-availability-cluster)
</div>

In our case we have a Round Robin algorithm with an `Active-Passive` setup, but this may not provide the same level of load balancing benefits as in an Active-Active setup. 

- __How a database Primary-Replica (Master-Slave) cluster works__

In a primary-replica (master-slave) database cluster, multiple database servers are configured to work together.

 The `primary server`, also known as the master, is responsible for handling read and write operations. 
 
 The `replica servers`, also known as slaves, replicate data from the primary server and serve as backup or standby servers.

- __What is the difference between the Primary node and the Replica node in regard to the application__

The `primary node` handles both read and write operations, acts as the authoritative source for data modifications, and maintains data integrity. 

`Replica nodes` replicate data changes from the primary node, serve read queries, and provide failover capabilities to ensure high availability and fault tolerance for the application.

### Issues about this infrastructure

- __SPOF(Single Points of Failure)__

The load balancer is still a single point of failure. The failure of a single component can lead to the entire system becoming non-functional.

- __Security issues (no firewall, no HTTPS)__

Without a firewall, there is no barrier to filter incoming and outgoing network traffic. This means that unauthorized access attempts or malicious attacks can reach the servers directly, increasing the risk of security issues.

Without SSL encryption (HTTPS), data transmitted between the client and the server is not securely encrypted. This means that the data can be intercepted and read by unauthorized individuals who have access to the network, potentially exposing sensitive information such as passwords, personal data, or confidential information.

- __No monitoring__

No server monitoring has several problems such as:
- There is a lack of visibility into the status, performance, and health of the servers
- Increased Downtime and Service Disruptions:
- Is difficult to identify Performance Bottlenecks such as high CPU usage, memory leaks, or network congestion.

## Bibliography:

- https://en.wikipedia.org/wiki/HAProxy
- https://www.jscape.com/blog/active-active-vs-active-passive-high-availability-cluster
- https://www.thegeekstuff.com/2016/01/load-balancer-intro/

## Tools:
- https://app.diagrams.net/
