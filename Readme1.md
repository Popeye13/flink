Flink学习笔记
===

什么是Flink?
---
Apache Flink is a framework and distributed processing engine for stateful computations over unbounded and bounded data streams.
Flink has been designed to run in all common cluster environments, perform computations at in-memory speed and at any scale

Flink特性
---

## Process bounded and unbounded data
  
  ### 1.Unbounded data
  有明确的起始点但没有终止点
  
  ### 2.Bounded data
  有明确的起始点与终止点
  
  ![image](https://github.com/Popeye13/flink/blob/master/bounded-unbounded.png)
  
## Deploy Applications Anywhere
  支持YARN、Mesos、Kubernetes
  
## Run Applications at any Scale
  Flink is designed to run stateful streaming applications at any scale. 
  Applications are parallelized into possibly thousands of tasks that are distributed and concurrently executed in a cluster. 
  Therefore, an application can leverage virtually unlimited amounts of CPUs, main memory, disk and network IO. 
  Moreover, Flink easily maintains very large application state. Its asynchronous and incremental checkpointing 
  algorithm ensures minimal impact on processing latencies while guaranteeing exactly-once state consistency.
  
## Leverage In-Memory Performance
  Stateful Flink applications are optimized for local state access. Task state is always maintained in memory or, 
  if the state size exceeds the available memory, in access-efficient on-disk data structures. 
  Hence, tasks perform all computations by accessing local, often in-memory, state yielding very low processing latencies. 
  Flink guarantees exactly-once state consistency in case of failures by periodically and asynchronously checkpointing 
  the local state to durable storage.

![image](https://github.com/Popeye13/flink/blob/master/local-state.png)
