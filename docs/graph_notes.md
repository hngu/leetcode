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

### Floyd-Warshall Algorithm
- Computes Shortest path for all pair of nodes
- Works with negative weights

**The Algorithm**
- First, setup an adjacency matrix with default values set to infinity or a really large number to avoid integer overflow
- We will use this adj matrix to store shortest path between i and j: `mat[i][j]`
- For each node, `i` in the graph:
  - Each `mat[i][i]` to denote that it does not cost anything to visit itself
  - Set the distance between i and its neighbors to its current weight. For example if node i is connected to neighboring node j with a weight of 2, set it to `mat[i][j] = 2` and remember this is for neighboring nodes only
 - Now to compute the rest of the distances, we set 3 for loops:
 - For each i in nodes:
 - For each j in nodes:
 - For each k in nodes:
  - `mat[i][j] = min(mat[i][j], mat[i][k] + mat[k][j])`
- And thats it! It works because we try every intermediary node to see if there is a shorter path and we try it forwards (i -> k -> j) and backwards (j -> k -> i) in case we didn't compute it correctly the first time going forward because the intermediary node distances aren't computed yet     

### Prim's Algorithm
- A minimum spanning tree is a graph that is undirected with weighted edges that connects all nodes in a graph with no cycles. If it has cycles, then it is not a tree. 

**The Algorithm**
- Create a Priority Queue of edges sorted by edge cost. This will be used to determine the next node to visit and the edge to get there.
- Start the algorithm at any node S. Mark S visited and push all of S's edges to the PQ.
- while the PQ is not empty:
  - dequeue the next smallest edge and get the node it is connected to.
  - If that new node is visited, then skip continue the loop
  - otherwise, mark the new node as visited
  - add the selected edge as part of the MST 
  - and push all of its nodes to the PQ. do not add edges that point to visited nodes.
