# NoC-Design-using-Round-Robin-Arbiter
Google Girl Hackathon'24
![image](https://github.com/Unnati2310/NoC-Design-using-Round-Robin-Arbiter/assets/101443031/1a256890-ad6a-49d9-8f9b-3cd29c03459b)
**Requirement: **

Using the above simulator setup, derive an optimal NOC design. Optimality is measured by:
* Measured latency is <= min_latency
* Measured bandwidth is at 95% of max_bandwidth
* Buffer sizing to support 90% occupancy
* Throttling happens only 5% of the time. Ex: for every 100 cycles, throttling should happen for 5 cycles on average. Throttling is based on get_powerlimit_theshold() being 1 or 0.


The Matlab implementation of the model is attached.

The design of NoC includes the following steps:
-   Deciding on an optimal topology: since we've been given a model beforehand we do not need to decide on the topology. However, as concluded from “Analysis and Implementation of Practical, Cost-Effective Network on Chips” by S.-J. Lee, K. Lee, and Yo", the Use of star topology and or a  mesh architecture is the most cost-effective and provides high speed serialization and programmable synchronization

-   Routing: we have already been provided with instructions to use a bidirectional network to and from CPU or IO to System memory.Howerver , using a XY dimension ordered routing has proved to be deadlock free by Glass and Ni in 1992.
-   Traffic features: the traffic features such as the Read and write latency and bandwidth have been randomly generated using Matlab code.
-   Size of buffers
-   routing Deadlock avoidance

Now our aim is to achieve the given requirements that would be achieved by the following methods:
1) Traffic modelling : networks start to clag when injected traffic approaches saturation throughput. Performance can suffer well before network throughput limits if traffic has hot spots
2) Using RL to optimise model parameters according to the traffic pattern.Parameters subjected to action primarily are the arbitration weights. However the isn't the only affecting factors towards power consumption and performance.See the design document.


About the setup model code:
- operation frequency, datawidth, number of cycles, have been taken from the example provided.
- number of bufferes =4 : CPU-> System Memory , IO-> System Memory , System Memory ->CPU, System Memory ->IO given buffer IDs :1,2,3,4
- power threshold has been assumed to be 100
- traffic and data written in the memory has been generated randomly
- throttle amends the operating frequency by 10%
- latency takes a random value between 1 and 100
- bandwidth is the sum of both CPU and Io traffics
- see the noc.m file for the Matlab implementation of the model
