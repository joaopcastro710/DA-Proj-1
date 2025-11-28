# DA Project 1
## Water Supply Management Analysis Tool

This project implements an analysis tool for studying and optimizing the Portuguese continental water supply network.  
The system is based on graph algorithms, with a focus on maximum-flow techniques and greedy approaches covered in the DA course.

The tool helps management evaluate:
- how much water each city can receive,
- whether the network meets total demand,
- load balancing across pipelines,
- sensitivity to failures (reservoirs, pumping stations, and pipelines).

The project uses the official dataset of reservoirs, pumping stations, delivery sites, and pipelines, modeling the system as a directed graph.

### Dataset (Project1Data.zip)

The water supply network is modeled as a directed graph containing:

#### Water Reservoirs (WR)
- Provide water to the network
- Max delivery: X m³/s

#### Pumping Stations (PS)
- Intermediate nodes that redirect flow

#### Delivery Sites (Cities / DS)
- Have a demand Z m³/s
- Represent residential consumers

#### Pipelines
- Connections between WR, PS, and DS
- Each with a maximum capacity
- May be directed or bidirectional (0 = bidirectional, 1 = unidirectional)

### Features

#### T1 — Base Functionality
- Menu interface for selecting analyses
- CSV parsing for all network components
- Graph construction (one or multiple graphs as needed)
- Full Doxygen documentation with time-complexity annotations

#### T2 — Basic Service Metrics
- Compute maximum water delivery to **each city** using Max-Flow (Edmonds–Karp)
- Check whether **the entire network** can meet total city demand
- Identify cities with **water deficit**
- Apply a load-balancing heuristic and compare:
  - average capacity–flow difference  
  - variance  
  - max difference

#### T3 — Reliability & Failure Sensitivity
- Simulate **removing a reservoir** and list affected cities
- Simulate **removing a pumping station** and compute deficits
- Identify **critical pipelines** whose failure blocks supply to a given city

### Algorithms Used

- **Edmonds–Karp (BFS-based Max Flow)**  
  Used for T2.1 and all failure simulations that require recomputation.

- **Greedy load balancing heuristic**  
  Minimizes the variance in pipe utilization.

- **Graph Traversal & Sensitivity Analysis**  
  Recomputing flow after removing nodes/edges.  
  Optional optimization: store residual graphs and reuse computations.
