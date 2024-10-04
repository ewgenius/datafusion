

# Profiling Cookbook

The section contains examples how to perform CPU profiling for Apache DataFusion on different operating systems.

## MacOS

### Building a flamegraph

[Video: how to CPU profile DataFusion with a Flamegraph](https://youtu.be/2z11xtYw_xs)

A flamegraph is a visual representation of which functions are being run
You can create flamegraphs in many ways; The instructions below are for
[cargo-flamegraph](https://github.com/flamegraph-rs/flamegraph) which results
in images such as this:

![Flamegraph](../_static/images/flamegraph.svg)

To create a flamegraph, you need to install the `flamegraph` tool:

```shell
cargo install flamegraph
```

Then you can run the flamegraph tool with the `--` separator to pass arguments
to the binary you want to profile.

Example: Flamegraph for `datafusion-cli` executing `q28.sql`. Note this
must be run as root on Mac OSx to access DTrace.

```shell
sudo flamegraph -- datafusion-cli -f q28.sq
```

You can also invoke the flamegraph tool with `cargo` to profile a specific test or benchmark.

Example: Flamegraph for a specific test:

```bash
CARGO_PROFILE_RELEASE_DEBUG=true cargo flamegraph --root --unit-test datafusion  -- dataframe::tests::test_array_agg
```

Example: Flamegraph for a benchmark

```bash
CARGO_PROFILE_RELEASE_DEBUG=true cargo flamegraph --root --bench sql_planner -- --bench
```

### CPU profiling with XCode Instruments

[Video: how to CPU profile DataFusion with XCode Instruments](https://youtu.be/P3dXH61Kr5U)

## Linux

## Windows
