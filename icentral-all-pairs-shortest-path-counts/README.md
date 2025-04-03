# `icentral-all-pairs-shortest-path-counts` README

## Overview

`icentral-all-pairs-shortest-path-counts` is a Rust crate designed to manage and manipulate all-pairs shortest path count data in large graphs. The main structure, `AllPairsShortestPathCounts`, stores and retrieves the number of shortest paths between all pairs of nodes in an efficient manner, allowing for both indexed and mutable access to the path count data.

This crate is particularly useful for graph algorithms that require detailed tracking of shortest paths between every pair of nodes, making it ideal for centrality calculations and other graph-theoretic applications.

### Key Features

- **All-Pairs Shortest Path Counts**: Efficiently store and access the number of shortest paths between all node pairs.
- **Indexed and Mapped Data Structures**: Supports both indexed and mapped implementations for flexible distance management.
- **Flexible Access**: Provides tuple-based indexing for immutable and mutable access to path counts.

## Installation

To include `icentral-all-pairs-shortest-path-counts` in your project, add the following to your `Cargo.toml`:

```toml
[dependencies]
icentral-all-pairs-shortest-path-counts = "0.1"
```

## Example Usage

### Creating an AllPairsShortestPathCounts Structure

You can create a new `AllPairsShortestPathCounts` instance with a specified length, or use the default constructor to initialize it with a name `"default_all_pairs_shortest_path_counts"`.

```rust
use icentral_all_pairs_shortest_path_counts::AllPairsShortestPathCounts;

fn main() {
    // Create a new AllPairsShortestPathCounts with a specific length
    let path_counts = AllPairsShortestPathCounts::new(10, "graph_path_counts");

    // Access the path count between two nodes (immutable)
    let count: usize = path_counts[(NodeId::new(0), NodeId::new(1))];

    // Mutate the path count between two nodes
    path_counts[(NodeId::new(0), NodeId::new(1))] = 5;
}
```

### Methods

- **`AllPairsShortestPathCounts::new(len: usize, name: &str)`**  
  Creates a new `AllPairsShortestPathCounts` instance with the specified size `len` and `name`. Each path count map is initialized with a size of `len`.

- **`AllPairsShortestPathCounts::len()`**  
  Returns the number of path count maps stored in the structure.

### Trait Implementations

- **`Default`**  
  Provides a default instance of `AllPairsShortestPathCounts` with the name `"default_all_pairs_shortest_path_counts"`.

- **`CreateEmptyIndexed`**  
  Creates an indexed empty `AllPairsShortestPathCounts` instance.

- **`CreateEmptyMapped`**  
  Creates a mapped empty `AllPairsShortestPathCounts` instance.

- **`Index<(NodeId, NodeId)>`**  
  Provides immutable access to the shortest path counts between two nodes.

- **`IndexMut<(NodeId, NodeId)>`**  
  Provides mutable access to the shortest path counts between two nodes.

## License

This project is licensed under the MIT License.


This crate is in the process of being translated from c++ to rust. Currently, it still needs exhaustive testing.  It is likely there currently exist many glitches which need to be fixed before proper usage. This crate is based on the original icentral program developed by Fuad Jamor. Please see the following repository for details: https://github.com/fjamour/icentral.

For progress updates, see the workspacer rust project.
