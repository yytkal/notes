---
cards-deck: tech::performance
---

# system performance
a study of entire system, hardware, software, anything in the data path.

# performance engineer
#card
- system performance, quantify the issue
- tooling and metrics for system-wide analysis
- capacity planning

# latency
measure of time spent waiting

# dynamic tracing
#card
allows software to be instrumented, live and in production, e.g. DTrace

# response time
#card
any time spent waiting and time spent being serviced (service time), time to transfer results

# utilization
#card
a measure of how busy a resource is, based on how much time in a given interval it was actively performing work.

# saturation
#card
the degree to which a resource has queued work it cannot service

# methodology
#card
find/draw a diagram of environment of data path

## Tuning
#card
Performance tuning is most effective closet to workload. e.g. application layer
Application layer may not be most efficient to observe. e.g. system monitoring tools.

# model

## SUT
#card
input(workload) -> SUT -> performance
perturbations can happen during benchmarking

## queueing system

# timescale
CPU cycle::0.3ns
L1 cache::0.9ns
L2 cache::2.8ns
L3 cache::12.9ns
memory access::120ns
SSD(flash)::50-150us
HDD::1-10ms
network, SF-NY::40ms
network, SF-UK::80ms
network, SF-AU::180ms
TCP packet retransmit::1-3s
OS virtualization reboot::4s
SCSI command timeout::30s
Hardware virtualization system reboot::40s
Physical system reboot::5min

# Trade-offs
#card
good/fast/cheap - 2/3

## CPU/memory
#card
memory cache to safe CPU cycle
CPU compress to reduce memory usage

## file system record size(blocksize)
#card
small bs -> better random IO and better filesystem cache
large bs -> better sequential IO

## network buffer size
#card
small buffer reduce memory overhead per connection
large buffer improve throughput

# knee point
#card
boundary between linear scaling and resource contention

# saturation point
#card
resource hit 100% utilization

# linear scalability of response time
#card
application can return error when resource are unavailable instead of queueing work to remain consistent response time for serviced requests

# observer effect
#card
performance metrics are not free, cost CPU cycles to gather and store

# utilization
#card
describes device usage

## time-based
#card
U=B/T: The amount of time server or resource is busy.
Some components can service operations in parallel and performance not degrade much at 100% util. e.g. storage arrays, raid?

## capacity-based
#card
Capacity planning. A system is abble to deliver a certain amount of throughput. At any level of performance, system is performing at proportion of the capacity. The proportion is called utilization.
100% busy != 100% capacity

# saturation
#card
The degree which more work is requested than a resource can process. Happens at 100% utilization (capacity based). Any degree of saturation is bad due to queueing.

30/650
