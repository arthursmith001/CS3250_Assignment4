# graphs_asmith

A Python library implementing graph algorithms including Dijkstra's shortest path algorithm.

## Description

This library provides efficient implementations of fundamental graph algorithms. The primary focus is on Dijkstra's algorithm for finding shortest paths in weighted graphs, along with a custom heap implementation for priority queue operations.

## Features

- **Dijkstra's Shortest Path Algorithm**: Find the shortest paths from a source vertex to all other vertices in a weighted graph
- **Custom Heap Implementation**: Complete priority queue implementation with heappush, heappop, heapify operations
- **Flexible Graph Input**: Supports graph representation as adjacency dictionaries
- **Path Reconstruction**: Returns both distances and actual shortest paths

## Installation

You can install this package using pip:

```bash
pip install graphs_asmith
```

For development installation:

```bash
git clone https://github.com/arthursmith001/CS3250_Assignment4
cd CS3250_Assignment4
pip install -e .
```

## Usage

### Basic Example

```python
from graphs_asmith import sp

# Define a graph as adjacency dictionary
# graph[u][v] = weight of edge from u to v
graph = {
    0: {1: 4, 7: 8},
    1: {0: 4, 2: 8, 7: 11},
    2: {1: 8, 3: 7, 8: 2, 5: 4},
    3: {2: 7, 4: 9, 5: 14},
    4: {3: 9, 5: 10},
    5: {2: 4, 3: 14, 4: 10, 6: 2},
    6: {5: 2, 7: 1, 8: 6},
    7: {0: 8, 1: 11, 6: 1, 8: 7},
    8: {2: 2, 6: 6, 7: 7}
}

# Find shortest paths from vertex 0
source = 0
distances, paths = sp.dijkstra(graph, source)

print(f"Shortest distances from {source}:")
print(distances)

print("Shortest paths:")
for destination in paths:
    print(f"Path to {destination}: {paths[destination]}")
```

### Using with Graph Files

The library includes a test script that can read graph data from files:

```bash
python test.py graph_file.txt
```

Graph file format:
```
9
0 1 4
0 7 8
1 0 4
1 2 8
...
```

Where the first line is the number of vertices, and each subsequent line contains: `source destination weight`

## Algorithm Details

### Dijkstra's Algorithm

The implementation uses Dijkstra's algorithm with the following characteristics:

- **Time Complexity**: O((V + E) log V) where V is vertices and E is edges
- **Space Complexity**: O(V) for distance and path storage
- **Uses a min-heap** for efficient priority queue operations
- **Handles disconnected graphs** gracefully
- **Returns both distances and paths** for complete shortest path information

The algorithm:
1. Initializes all distances to infinity except the source (distance 0)
2. Uses a priority queue to always process the vertex with minimum distance
3. For each vertex, updates distances to all neighbors if a shorter path is found
4. Tracks the actual shortest path for path reconstruction

### Heap Implementation

The library includes a complete heap implementation with:
- `heappush(heap, item)`: Add item to heap
- `heappop(heap)`: Remove and return smallest item
- `heapify(x)`: Transform list into heap in-place
- Additional utilities for heap manipulation

## Project Structure

```
src/
└── graphs_asmith/
    ├── __init__.py      # Package initialization
    ├── heapq.py         # Heap implementation
    └── sp.py            # Shortest path algorithms
test.py                  # Test script for file-based graphs
pyproject.toml          # Package configuration
README.md               # This file
```

## Development

This project was developed as part of CS3250 coursework focusing on software packaging and algorithm implementation.

### Requirements

- Python 3.7+
- No external dependencies (uses custom heap implementation)

### Testing

Run the test script with a sample graph:

```bash
python test.py sample_graph.txt
```

## License

MIT License

## Author

Arthur Smith (asmit360@msudenver.edu)

## Repository

[https://github.com/arthursmith001/CS3250_Assignment4](https://github.com/arthursmith001/CS3250_Assignment4)
