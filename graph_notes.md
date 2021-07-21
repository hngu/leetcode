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
