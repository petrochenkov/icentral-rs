# `icentral-all-pairs-distance`

## Overview

`icentral-all-pairs-distance` is a Rust crate designed to efficiently manage and manipulate all-pairs distance data in large graphs. It provides a robust structure, `AllPairsDistances`, that allows indexing, mutability, and creation of both mapped and indexed distance maps. The crate is useful in graph algorithms where distances between all pairs of nodes need to be stored and retrieved efficiently.

### Key Features

- **All-Pairs Distance Management**: Supports storing distances between all node pairs in an easily indexable structure.
- **Flexible Initialization**: Provides methods for creating both mapped and indexed distance maps.
- **Indexed and Mutable Access**: Allows for direct and mutable access to distances via tuple-based indexing.

## Installation

To include `icentral-all-pairs-distance` in your project, add the following to your `Cargo.toml`:

```toml
[dependencies]
icentral-all-pairs-distance = "0.1"
```

## Example Usage

### Creating an AllPairsDistances Structure

You can create a new `AllPairsDistances` instance either with a specific length or using the default, which is initialized with the name `"default_all_pairs_distances"`.

```rust
use icentral_all_pairs_distance::AllPairsDistances;

fn main() {
    // Create a new AllPairsDistances with a specific length
    let distances = AllPairsDistances::new(10, "graph_distances");

    // Access a distance between node pairs (immutable)
    let dist: f64 = distances[(NodeId::new(0), NodeId::new(1))];

    // Mutate the distance between node pairs
    distances[(NodeId::new(0), NodeId::new(1))] = 3.5;
}
```

### Methods

- **`AllPairsDistances::new(len: usize, name: &str)`**  
  Creates a new `AllPairsDistances` instance with the specified size `len` and `name`. Each distance map is initialized with a size of `len`.

- **`AllPairsDistances::len()`**  
  Returns the number of distance maps stored in the structure.

### Trait Implementations

- **`Default`**  
  Provides a default instance of `AllPairsDistances` with the name `"default_all_pairs_distances"`.

- **`CreateEmptyIndexed`**  
  Creates an indexed empty `AllPairsDistances` instance.

- **`CreateEmptyMapped`**  
  Creates a mapped empty `AllPairsDistances` instance.

- **`Index<(NodeId, NodeId)>`**  
  Provides immutable access to the distances between two nodes.

- **`IndexMut<(NodeId, NodeId)>`**  
  Provides mutable access to the distances between two nodes.

## License

This project is licensed under the MIT License.


This crate is in the process of being translated from c++ to rust. Currently, it still needs exhaustive testing.  It is likely there currently exist many glitches which need to be fixed before proper usage. This crate is based on the original icentral program developed by Fuad Jamor. Please see the following repository for details: https://github.com/fjamour/icentral.

For progress updates, see the workspacer rust project.
