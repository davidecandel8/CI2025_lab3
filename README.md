# CI2025_lab3 - (UPDATE AFTER PEER REVIEW)

## Computational Intelligence Lab 3

### Overview
This lab explores shortest path algorithms and their performance on randomly generated graphs. The notebook is fully modular and automates the analysis and comparison of two algorithms: NetworkX (Dijkstra/Bellman-Ford) and a custom Bellman-Ford implementation.

**Note:** Due to high computational demands and time constraints, the tests reported in this repository were restricted to graph sizes ranging from **10 to 200** nodes.

### Features Implemented

**1. Problem Generation**
Random weighted directed graphs are generated with configurable parameters:
- Number of nodes (`size`)
-  Edge density (`density`)
- Noise level (`noise_level`)
- Option for negative edge weights (`negative_values`)

**2. Algorithms**
- NetworkX shortest path (Dijkstra for non-negative weights, Bellman-Ford for negative weights)
- **Custom Bellman–Ford implementation**
	- Computes shortest paths on graphs with negative edge weights
	- Explicit detection of negative cycles  
	- Performs standard relaxation for `V - 1` iterations followed by a final check for cycle detection  
	- Reconstructs the shortest path using predecessor tracking  
	- Returns both path and cost, or `(None, inf)` if a negative cycle is reachable  

**3. Incremental Sampling**
For large graphs, only a subset of source nodes is sampled to keep computation feasible. The number of samples increases with graph size.

**4. Statistics and Aggregation**
For each problem instance, aggregate statistics are computed for both algorithms:
	- Average, sum, min, max, count of path costs and time of execution.

**5. Results Saving**
All results are automatically saved to `result_optimized.csv` for further analysis and reproducibility. **Note:** `result.csv` is the oldest file before update, after peer review. 

**6. Visualization**
Dedicated cell loads the results and generates comparison plots:
- Average path cost for NetworkX and the custom Bellman–Ford implementation
- Absolute difference between the two averages
- Mean execution time for each algorithm (in milliseconds)
- Performance ratio, defined as: (custom_time / networkx_time)