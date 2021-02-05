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
^1611302967797

# latency
measure of time spent waiting

# dynamic tracing
#card
allows software to be instrumented, live and in production, e.g. DTrace
^1611302967806

# response time
#card
any time spent waiting and time spent being serviced (service time), time to transfer results
^1611302967814

# utilization
#card
a measure of how busy a resource is, based on how much time in a given interval it was actively performing work.
^1611302967823

# saturation
#card
the degree to which a resource has queued work it cannot service
^1611302967831

# methodology
#card
find/draw a diagram of environment of data path
^1611302967839

## Tuning
#card
Performance tuning is most effective closet to workload. e.g. application layer
Application layer may not be most efficient to observe. e.g. system monitoring tools.
^1611302967846

# model

## SUT
#card
input(workload) -> SUT -> performance
perturbations can happen during benchmarking
^1611302967854

## queueing system

# timescale
CPU cycle::0.3ns
^1611302967861
L1 cache::0.9ns
^1611302967868
L2 cache::2.8ns
^1611302967875
L3 cache::12.9ns
^1611302967884
memory access::120ns
^1611302967892
SSD(flash)::50-150us
^1611302967899
HDD::1-10ms
^1611302967905
network, SF-NY::40ms
^1611302967912
network, SF-UK::80ms
^1611302967919
network, SF-AU::180ms
^1611302967929
TCP packet retransmit::1-3s
^1611302967935
OS virtualization reboot::4s
^1611302967942
SCSI command timeout::30s
^1611302967951
Hardware virtualization system reboot::40s
^1611302967959
Physical system reboot::5min
^1611302967967

# Trade-offs
#card
good/fast/cheap - 2/3
^1611302967976

## CPU/memory
#card
memory cache to safe CPU cycle
CPU compress to reduce memory usage
^1611302967984

## file system record size(blocksize)
#card
small bs -> better random IO and better filesystem cache
large bs -> better sequential IO
^1611302967991

## network buffer size
#card
small buffer reduce memory overhead per connection
large buffer improve throughput
^1611302967999

# knee point
#card
boundary between linear scaling and resource contention
^1611302968006

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
