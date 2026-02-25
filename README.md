## Graph-Based Route Planning Using BFS

This program models a road network as an undirected graph and computes:

1. The path with the **minimum number of intersections** between a source and destination.
2. A **non-overlapping alternative path** that avoids previously used nodes and edges.

The solution uses **Breadth-First Search (BFS)** because BFS guarantees the shortest path in an unweighted graph.

---

## Problem Representation

- Each **location/intersection** → represented as a graph vertex
- Each **road** → represented as an undirected edge
- The graph is stored using an **adjacency matrix**

```cpp
adjacent[u][v] = 1;
adjacent[v][u] = 1;

This means travel is possible in both directions.

---
Key Components of the Program
1. Graph Class

The Graph class handles:

Graph creation

Adding roads between intersections

Finding the minimum path using BFS

Finding a non-overlapping path

2. Minimum Interaction Path (BFS)

This function:

Uses BFS to explore nodes level by level

Stores parent nodes to reconstruct the path

Stops when the destination is reached

Returns the shortest path in terms of number of intersections

Why BFS is used:

Works efficiently for unweighted graphs

Guarantees minimum hops

Time complexity: O(V + E)

3. Path Reconstruction

After reaching the destination:

The algorithm traces back using the parent array

Stores nodes in reverse order

Reverses them to get the correct path from source to destination

4. Non-Overlapping Path
int* nonoverlappath(int source, int destination, bool* blockednode, bool** blockededge)

This function computes an alternate route that avoids:

Nodes used in the first path

Edges used in the first path

It performs BFS again but ignores blocked nodes and edges.

This simulates real-world routing scenarios where:

Roads may be closed

Intersections may be congested

A second independent path is needed

5. Blocking Logic

After finding the first path:

Nodes in that path are marked as blocked

Edges in that path are marked as blocked

blockednode[path[i]] = true;
blockededge[path[i]][path[i+1]] = true;

This ensures the second search avoids overlapping with the first.

6. User Input Flow

The program performs the following steps:

Input number of intersections (nodes)

Input number of roads (edges)

Enter all road connections

Enter source and destination for minimum path

Compute shortest path

Block nodes/edges from that path

Enter new source and destination

Compute non-overlapping alternate path

Output

The program prints:

Minimum-intersection path

Non-overlapping alternate path (if available)

If no path exists, it reports:

No path found
Concepts Demonstrated

Graph representation using adjacency matrix

Breadth-First Search traversal

Shortest path in unweighted graphs

Parent tracking for path reconstruction

Alternative routing with constraints

Dynamic memory management in C++
Implementation is owned by **Nandhakumar**.

```cpp
int* mininteractionpath(int source, int destination)
