# pygraphutils
 An Python library for solving graph theory problems

 Proper testing on this library has not been done, so this should not be used for any critical projects. Please report any bugs by submitting an [issue](https://github.com/ModEngineer/pygraphutils/issues) or [pull request](https://github.com/ModEngineer/pygraphutils/pulls).
# Installation:
 1. Download the `pygraphutils` folder or the entire repo
 2. Copy the `pygraphutils` folder to a path relative to your script or into your modules installation folder
 3. Follow the instructions below that best fit your installation method:
  * If installing to the modules installation folder, follow the steps below:
   1. In your script, use 
   ```python
   import pygraphutils
   ```
  * If installing to a path relative to your script's folder, follow the steps below:
   1. Use the relative path imports system in Python to import the module. `..` means to go up one directory, `.` means to stay in the current directory, and any text refers to either a folder or that folder's `__init__.py`. For more information, see [Python's import documentation](https://docs.python.org/3/reference/import.html#package-relative-imports)
   2. In your script, use 
   ```python
   import directorystructurehere.pygraphutils
   ```
# Usage

Graphs use the format:
```py
{node1: [node2, node3], node2: [node1], node3:[node1]}
```

### Class `GraphError(*args, **kwargs)`: 
`Exception`-based error class used by Python-GraphUtils

### Class `Auto`:
`NoneType`-like object that represents the automatic value

### Class `ExitContainer(exception, code)`:

Class which allows for the outputting of errors and exit codes without raising an exception.

#### Function `ExitContainer.raise_exception()`:
Function which raises the `ExitContainer`'s exception if it has one.

### Function `validate_graph(graphData)`:
Function which validates a graph based on formatting, object type, and connections.

### Function `remove_node(node, graphData)`:
Function which removes `node` from `graphData`

### Function `remove_edge(node1, node2, graphData)`:
Function which removes the edge from `node1` to `node2` from `graphData`

### Function `add_node(node, graphData)`:
Function which adds `node` to `graphData`

### Function `add_edge(node1, node2, graphData)`:
Function which adds the edge between nodes `node1` and `node2` to `graphData`

### Function `dfs(graphData, vertex=Auto())`:
Function which is a depth-first search based on Wikipedia's pseudocode. `vertex` is the starting vertex (not the index). Leaving `vertex` on `Auto()` will start on an arbitrary vertex(0).

### Function `is_connected(graphData)`:
Function which runs `dfs` on `graphData` to check if `graphData` is fully connected.

### Function `find_bridges(graphData)`:
Function which finds all bridges in `graphData`, does not work if `graphData` is not completely connected.

### Function `__collapse_list_list(listList, recursive=False)`:
Function which collapses all items in the lists of a list of lists into a single list.

### Function `__list_contains_list(subList, containerList)`:
Function which checks if `containerList` contains all items in `subList`

### Function `split_unconnected(graphData)`:
Function which will split `graphData` into a list of graphs if `graphData` is unconnected. Returns `[graphData]` if graph is connected.

### Function `split_at_bridge(splitNode, node2, graphData)`:
Function which splits a graph into two parts, where `splitNode` is the node shared by both graphs and where `node2` is the other node in the bridge

### Function `fleury(graphData)`:
Function based on Wikipedia's pseudocode for Fleury's algorithm for finding a Eulerian path from an undirectional graph

### Function `auto_split(graphData, returnGraphs=True, returnPaths=False)`:
Function which inefficiently and possibly inaccurately splits `graphData` into multiple subgraphs which are all Eulerian. Setting `returnGraphs` to true will make the output dictionary have the `graphs` field contain a list of the Eulerian graphs. Setting `returnPaths` to true will make hte output dictionary have the `paths` field contain a list of the Eulerian paths of the aforementioned graphs.
