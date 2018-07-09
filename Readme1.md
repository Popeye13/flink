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

Application
---
##Building Blocks for Streaming Applications

### Streams
1. Bounded and unbounded streams
2. Real-time and recorded streams

### States
1. **Multiple State Primitives**
2. **Pluggable State Backends**: different state backends that store state in memory or in RocksDB, an efficient embedded on-disk data store. Custom state backends can be plugged in as well.
3. **Exactly-once state consistency**: Flink’s checkpointing and recovery algorithms guarantee the consistency of application state in case of a failure. Hence, failures are transparently handled and do not affect the correctness of an application.
4. **Very Large State**: Flink is able to maintain application state of several terabytes in size due to its **asynchronous and incremental checkpoint algorithm**.
5. **Scalable Applications**

### Times
1. **Event-time Mode**: Compute results based on timestamps of the events. Thereby, event-time processing allows for accurate and consistent results regardless whether recorded or real-time events are processed.
2. **Watermark Support**: Flink employs watermarks to reason about time in event-time applications. Watermarks are also a flexible mechanism to trade-off the latency and completeness of results.
3. **Late Data Handling**: When processing streams in event-time mode with watermarks, it can happen that a computation has been completed before all associated events have arrived. Such events are called late events. Flink features multiple options to handle late events, such as rerouting them via side outputs and updating previously completed results.
4. **Processing-time Mode**: In addition to its event-time mode, Flink also supports processing-time semantics which performs computations as triggered by the wall-clock time of the processing machine. The processing-time mode can be suitable for certain applications with strict low-latency requirements that can tolerate approximate results.

## Layered APIs
Flink provides three layered APIs. Each API offers a different trade-off between conciseness and expressiveness and targets different use cases.
![image](https://github.com/Popeye13/flink/blob/master/api-stack.png)

### The ProcessFunctions

### The DataStream API

### SQL & Table API

Flink核心概念
---

## 1.Stateful
## 2.Asynchronous and incremental checkpoint algorithm
## 3.Event-time and processing-time
## 4.Watermark
## 5.Late Data Handling



Data source -> tramsformation -> Data sink
