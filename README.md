## Graph with Trie-Based Indexing

This program implements a hybrid data structure that combines the properties of a graph and a trie to store and process strings efficiently.  
The implementation follows the idea described in the project report, where a graph represents relationships and a trie structure supports prefix-based indexing.

---

## Concept

- A graph represents relationships between characters.
- A trie-like structure ensures that strings are stored based on shared prefixes.
- Each character is treated as a node.
- Consecutive characters are connected by edges.
- Edge weights represent how many times that connection occurs.

This hybrid approach improves performance for prefix search and string operations.

---

## Data Structures Used

The program maintains:

- `adj_list` → adjacency list storing character connections  
- `con_wei` → matrix storing edge weights between characters  
- `cou` → count of incoming and outgoing connections per node  
- `adj_isend` → marks characters that appear at string endings  

This allows efficient insertion, searching, deletion, and visualization.

---

## Core Operations

### 1. Insert String

```python
graphs.insert_string(s)
```
When a string is inserted:

- The first character connects to a root node (0)

- Each subsequent character is linked to the previous one

- Edge weights are incremented if the connection already exists

- Character nodes are created if missing

Time complexity depends on string length N:

Insertion = O(N)
```

## This matches the prefix-based behaviour of a trie. 

```
## 2. Search String
```
```
graphs.find_word(s)
```
```
Searching works by:

- Starting from the first character node

- Traversing edges sequentially

- Verifying each character connection

- If any connection is missing, the word does not exist.
```
```
## Time complexity:

Search = O(N)

This is equivalent to trie search complexity. 
``


## 3. Delete String
```
graphs.delete_str(s)
```
Deletion involves:

- Verifying that the string exists

- Decreasing edge weights

- Removing edges when weight becomes zero

- Removing nodes with no remaining connections

## Worst-case time complexity depends on:

- string length N

- number of vertices V
```
Deletion = O(N × V)

```


## 4. Print Graph
```
graphs.print_g()
```
Displays adjacency list showing how characters are connected.

This helps visualize the trie-like structure embedded in the graph.


## 5. Graph Visualization
```
import networkx as nx
import matplotlib.pyplot as plt
```
The program uses NetworkX to:

- Convert adjacency list into a graph

- Generate layout using spring_layout

- Draw labeled nodes and edges

This provides a visual representation of the character graph.


## 6. Applications

This structure can be useful for:

## Auto-complete systems

## Spell checkers

## Prefix matching algorithms

## Browser history indexing

