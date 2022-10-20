# Graph

## Graph Types:

* Acyclic
  * Directed
  * Undirected
* Cyclic
  * Directed
  * Undirected
* With Edge Labels

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Graph Types</p></figcaption></figure>

## Graph Problems:

* What is the shortest / longest route from S to T?
* Are there cycles?
* Is there a tour you can take that only uses each node / edge exactly once?

More theoretically

* **s-t Path**. Is there a path between vertices s and t?
* **Connectivity.** Is the graph connected, i.e. is there a path between all vertices?
* **Biconnectivity.** Is there a vertex whose removal disconnects the graph?
* **Shortest s-t Path.** What is the shortest path between vertices s and t?
* **Cycle Detection.** Does the graph contain any cycles?
* **Euler Tour.** Is there a cycle that uses every edge exactly once?(Best is O(#edges)
* **Hamilton Tour.** Is there a cycle that uses every vertex exactly once?
* **Planarity**. Can you draw the graph on paper with no crossing edges?
* **Isomorphism**. Are two graphs isomorphic (the same graph in disguise)?

## Traversal / Search Graph

### Depth First Traversal / Search&#x20;

#### DFS PreOrder

#### DFS PostOrder



### Breadth First Traversal / Search

#### BFS Order

* Initialize a queue with a starting vertex s and mark that vertex.
  * A queue is a list that has two operations: enqueue(add) and dequeue(removeFirst)
* Repeat until queue is empty:
  * Remove vertex v from the front of the queue.&#x20;
  * For each unmarked neighbor n of v:
    * Mark n.
    * Set edgeTo\[n] = v(and or disTo\[n] = disTo\[v]+1
    * Add n to end of queue





