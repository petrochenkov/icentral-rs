# `icentral-alg`

## Overview

`icentral-alg` is a Rust crate designed to perform experiments on various graph algorithms, with a primary focus on Betweenness Centrality. This crate provides an implementation for incremental and parallelized algorithms for computing betweenness centrality, including Brandes' algorithm, QUBE, and other experimental techniques for incremental centrality calculation.

The crate also supports distributed computing through MPI, enabling the scaling of experiments across multiple processes.

### Key Features

- **Incremental Betweenness Centrality**: Compute changes in betweenness centrality after edge insertions or deletions.
- **Parallel Execution**: Scale the computation across multiple threads or processes using MPI.
- **Support for Multiple Graph Algorithms**: Includes algorithms like Brandes', QUBE, and FUAD.
- **Extensible Graph Structures**: Works with various graph structures that implement a set of required traits.

## Installation

To include `icentral-alg` in your project, add the following to your `Cargo.toml`:

```toml
[dependencies]
icentral-alg = "0.1"
```

## Example Usage

### Running Betweenness Centrality Experiments

```rust
use icentral_alg::do_paper_exp;
use std::time::Duration;

fn main() -> Result<(), icentral_alg::BetweennessCentralityError> {
    let num_edges = 100;
    let num_iter = Some(10);
    let max_time = Duration::from_secs(3600);
    let rand_seed = 42;
    let graph_paths = vec![
        String::from("/path/to/graph1.net"),
        String::from("/path/to/graph2.net"),
    ];

    do_paper_exp::<MyGraphHash>(
        num_edges,
        num_iter,
        max_time,
        rand_seed,
        graph_paths,
        true,   // do_inc_brandes
        true,   // do_qube
        false,  // do_inc_qube
        false   // do_fuad
    )?;

    Ok(())
}
```

### Required Traits for Graphs

To use your own graph structures with `icentral-alg`, they must implement the following traits:

- `BccGraphHashInterface`
- `FindConnectedComponents`
- `FindSingleSourceShortestPaths`
- `InsertNode`, `InsertEdgeUpdateMuc`
- `MappedNodes`
- `ExtendWith`
- `ResetWith`
- `Debug`, `DebugIterationStep`

## Functionality

### `do_paper_exp`

The `do_paper_exp` function is the central experiment execution function. It allows running different algorithms with incremental updates on graphs and benchmarking their performance under different conditions.

```rust
pub fn do_paper_exp<GH>(
    num_edges: usize,
    num_iter: Option<usize>,
    max_time: Duration,
    rand_seed: i32,
    path_vec: Vec<String>,
    do_inc_brandes: bool,
    do_qube: bool,
    do_inc_qube: bool,
    do_fuad: bool
) -> Result<(), BetweennessCentralityError>
where
    GH: BccGraphHashInterface + GraphOperations,
    Graph<GH>: GraphStructure,
{
    // Experiment logic here
}
```

### MPI Support

For distributed computing, the crate supports MPI-based parallelization via `icentral_parallel`. This feature allows running betweenness centrality computations across multiple processes in a distributed manner.

### Additional Functions

- `maybe_do_paper_exp_inc_brandes`: Executes incremental Brandes algorithm.
- `maybe_do_paper_exp_inc_qube`: Executes incremental QUBE algorithm.
- `icentral`: Handles incremental betweenness centrality computations with serial and parallel options.
  
## License

This project is licensed under the MIT License.


This crate is in the process of being translated from c++ to rust. Currently, it still needs exhaustive testing.  It is likely there currently exist many glitches which need to be fixed before proper usage. This crate is based on the original icentral program developed by Fuad Jamor. Please see the following repository for details: https://github.com/fjamour/icentral.

For progress updates, see the workspacer rust project.
