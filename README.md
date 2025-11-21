# CI2025_lab3

## Computational Intelligence Lab 3

### Overview
This lab explores shortest path algorithms and their performance on randomly generated graphs. The notebook is fully modular and automates the analysis and comparison of two algorithms: NetworkX (Dijkstra/Bellman-Ford) and a custom Bellman-Ford implementation.

**Note:** Due to high computational demands and time constraints, the tests reported in this repository were restricted to graph sizes ranging from **10 to 50** nodes.

### Features Implemented

**1. Problem Generation**
- Random weighted directed graphs are generated with configurable parameters:
	- Number of nodes (`size`)
	- Edge density (`density`)
	- Noise level (`noise_level`)
	- Option for negative edge weights (`negative_values`)


**2. Algorithms**
- NetworkX shortest path (Dijkstra for non-negative weights, Bellman-Ford for negative weights)
- **Custom Bellman-Ford implementation:**
	- Computes shortest paths even in graphs with negative edge weights.
	- Explicitly detects negative cycles: if a negative cycle is found, the path is reported as unreachable (`None`) and the cost as infinite (`np.inf`).
	- Performs edge relaxation for V-1 iterations (where V is the number of nodes), then checks for further improvements to detect negative cycles.
	- Reconstructs the shortest path using predecessor tracking.
	- Returns both the path and the cost for each source-target pair.
	
**3. Incremental Sampling**
- For large graphs, only a subset of source nodes is sampled to keep computation feasible. The number of samples increases with graph size.

**4. Statistics and Aggregation**
- For each problem instance, aggregate statistics are computed for both algorithms:
	- Average, sum, min, max, and count of path costs

**5. Results Saving**
- All results are automatically saved to `result.csv` for further analysis and reproducibility.

**6. Visualization**
- Dedicated cell loads the results and generates comparison plots:
	- Average cost for each algorithm
	- Difference in average cost between NetworkX and Bellman-Ford custom

### How to Use
1. Run the notebook cells in order to generate problems, compute statistics, and save results.
2. Use the final plotting cell to visualize and compare the algorithms.
3. Inspect `result.csv` for all aggregated data.

### Customization
- You can adjust parameters (sizes, densities, noise levels, sampling rates) at the top of the main cell.
- Add more plots or statistics as needed in the visualization cell.

