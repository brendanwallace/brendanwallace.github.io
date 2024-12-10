---
title: "Research"
draft: false
---

## Dissertation

My dissertation research is focused on general patterns in mobility and its applications for epidemiology, ecology, and sociology.

### I. Hot-spot disease superspreading

Many diseases spread more readily in certain "hot-spot" locations, like bars and restaurants. Some people go more frequently to these hot-spots, which creates a risk structure in the population. This project investigates this particular risk structure, taking advantage of known patterns in human mobility.


![Hotspot figure 1](/research/hotspot.png)


<!-- (A) The model assigns each individual a fixed risk tolerance value between 0 and 1. Each day, individuals visit the hotspot with probability equal to their risk tolerance. Infected agents in the hotspot spread the disease with high transmission rate to susceptible agents in the hotspot. At the same time, all infected agents spread the disease to all susceptible agents with low transmission rate. Infected agents eventually recover and cannot be infected again, and the simulation ends when no agents are infected. (B) We consider different risk tolerance distributions for the population using beta distributions with low, medium and high mean; and low, medium and high variance. See methods for more details.


![Hotspot figure 2](/research/hotspot2.png)

Top panels show how $R_t$ in the hotspot model (purple dotted lines) rises and falls sharply, contrasted with the homogeneous model (black solid lines) in which $R_t$ declines monotonically. Middle and bottom panels show how this affects the peak and total number of infections respectively. From left to right, with hotspot dynamics: low $R_0$ diseases peak higher and affect more people; medium $R_0$ diseases peak higher but affect fewer people; and high $R_0$ diseases peak lower and affect fewer people. Figures made with scenario of risk tolerance mean of 0.25, “high” risk tolerance distribution variance and 0.5 fraction of hotspot spread (middle right panel in figure 1 B, purple dotted lines in the center column in figures 2 and 3). -->

### II. Emergent trail networks

When a person or animal walk through rough terrain, they flatten it down, making it easier for subsequent travelers to walk the same way. When multiple individuals walk between multiple destinations, this positive feedback leads to the emergence of a network of trails. This project investigates the topology, dynamics, stability and other properties of such emergent trail networks using a computational modeling approach.

![Trails figure](/research/trails.png)
<!-- (A) Snapshots of trail development between fixed points in low-cost (left column) and high-cost (right column) environments. (B) Lines show trail development over time plotted in travel-cost (average cost of travel between points) vs infrastructure (amount of trail used) space. Final networks (large dots) show an efficient tradeoff between infrastructure use and travel cost along a pareto front. (C) Walkers move between _dynamically shifting_ locations, producing a network that connects all of the 2-D space. -->

<!-- This project describes a computational modeling approach to understanding the dynamics of these networks that builds on a classic "active-walker" model \[1\]. Simulated agents take the least-cost path between points of interest across a continuous 2D space; as they move they decrease the "cost" of traveling over the same patch of ground. We consider the dual optimization problem of simultaneously minimizing travel costs between points of interest in the network and total amount of path improvement, as in \[2\]; within this framework we try to understand the efficiencies of the emergent networks, and how efficiencies vary with environmental parameters, behavioral parameters, and other network measures. We discuss implications to urban planning, transportation system design, and animal behavior. Finally, we show that when points of interest are randomly and dynamically placed, the emergent transportation network may take on novel fractal shapes.

\[1\] Helbing, Dirk, Joachim Keltsch, and Péter Molnár. “Modelling the Evolution of Human Trail Systems.” Nature 1997

\[2\] Perna, Andrea, and Tanya Latty. “Animal Transportation Networks.” Journal of the Royal Society 2014 -->

<!-- \begin{figure}[!h]
  \centering
  \includegraphics[width=.95\textwidth]{netsci2025.pdf}
  \caption{ }
\end{figure} -->




### III. Scales of Animal Mobility

I'm working to expand upon the approach taken in [_The scales of human mobility_](https://www.nature.com/articles/s41586-020-2909-1), to look for scales in animal mobility, and to investigate anthropological invariants.

## Selected publications

Althouse, B.M., __Wallace, B.__, Case, B.K.M. et al. _The unintended consequences of inconsistent closure policies and mobility restrictions during epidemics._ BMC Global Public Health 1, 28 (2023). https://doi.org/10.1186/s44263-023-00028-z
  
M. Nunkesser, __B. Wallace__, S. Stylianidou, inventors; Google Llc.,
  applicant; _Machine learning model for predicting speed based on vehicle type_; World Patent
  WO 2019/112566 A1, filed December 5, 2017, and issued June 13, 2019.