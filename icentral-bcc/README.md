# icentral-bcc

`icentral-bcc` is a Rust crate designed for the efficient identification and management of biconnected components within graph structures. Leveraging advanced graph theory concepts and algorithms, this crate facilitates the extraction of biconnected subgraphs and edge-based component disaggregation, valuable for computations involving network robustness and structural analysis.

## Overview

Graphs are fundamental data structures used extensively in computational applications, from network communications to structural modeling. Biconnected components are maximal subgraphs where removing any single vertex will not disconnect the graph. This property is critical in assessing the resilience and connectivity of networks.

This crate introduces:

- `BccGraphHashInterface`: A trait structuring the interaction with graph hash operations.
- `FindBiconnectedComponent`: A trait providing functionality to discover biconnected components within a graph.
- `FindEdgeBccSubgraph`: A trait enabling the identification of the biconnected component subgraph containing a specific edge.

## Usage

The `BccDfsVisitorContext` structure manages the context of depth-first searches (DFS) necessary for computing biconnected components. Types implementing graph traits can utilize these methods to determine their biconnected structures. Integration into existing graph frameworks is streamlined, given trait-based extensibility.

To employ the core functionalities:

```rust
let mut graph = YourGraphType::new();
let mut bccs: Vec<YourBccGraphHash> = vec![];
graph.find_bicon_component(&mut bccs);
```

Implement `BccGraphHashInterface` for your specific graph representation to integrate seamlessly with this crate.

## Advanced Features

- **DFS-based component analysis**: Uses advanced DFS strategies to identify subcomponents efficiently.
- **Performance metrics**: Track performance statistics through `BiconnectedComponentsStat`, providing insight into the computational efficiency of the operations.

## License

This project is licensed under the MIT License.

## Disclaimer

This README.md content was algorithmically generated and may not fully represent the `icentral-bcc` crate. However, it provides an extensive overview for academic and practical exploration.

This crate is in the process of being translated from c++ to rust. Currently, it still needs exhaustive testing.  It is likely there currently exist many glitches which need to be fixed before proper usage. This crate is based on the original icentral program developed by Fuad Jamor. Please see the following repository for details: https://github.com/fjamour/icentral.

For progress updates, see the workspacer rust project.
