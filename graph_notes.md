### Questions to ask yourself
- Is the graph directed or undirected?
- Does the graph have unweighted or weighted edges?
- Is the graph sparse, or dense?
- Can the graph be represented by an adjacency list, adjacency matrix, edge list, a tree or some other data structure?

### Connected Components in Undirected Graph
You can use depth first search to find all the connected components in a undirected graph. To do this, we need:
1. an array of the graph nodes
2. an array of graph nodes -> component number
3. a global count variable called component_count set to 1.

**The Algorithm**
1. Iterate through the array of graph nodes:
2. For each node, check if it is visited. If it is, then go to the next node in the list.
3. Run DFS on that node, passing in the current component_count.
4. Increment component_count
5. Go to the next node.
6. After the loop ends, return the component_count.

NOTES:
- DFS should stop running when it has no more nodes to reach or if the node is already visited.
- We need to keep track of what nodes were visited. We can use a visited array to achieve this.

### Shortest Path from node A -> node E
The easiest way to solve this is to use Breadth First Search on node A, tracking the path in an array. If node E exists in that path, then return that path.
Using BFS is better than DFS because it will find the shortest path whereas DFS might return a path, but not necessarily the shortest.

**The Algorithm**

### Topological Sort
- Top Sort is used to find the topological ordering of a graph where the order of the nodes or events matter
- Examples include class prerequisties, program dependencies etc
- topological ordering: ordering of nodes of a directed, acyclic graph where for nodes A with edges pointing to node B, node A appears before node B in the ordering.
- Toplogical orderings are not unique (ex: multiple valid ways to fulfill program dependencies)
- To detect a cycle, use Tarjan's Strongly connnected components algorithm

**The Algorithm**
- pick an unvisited node
- start at that node and do a DFS for all child nodes
- on the recursive callback, add the current node to the topological ordering

