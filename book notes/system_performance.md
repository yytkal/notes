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
Physical system reboot::5s

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

page 25
