# Implementation

### Directed Graph and Strongly Connected Components

A Directed Graph is a type of graph in which edges have a direction or orientation assigned to them. Each edge connects a source node to a destination node, indicating the direction of the relationship between the two nodes. Below is an example.

<figure><img src="../../../.gitbook/assets/water_gitbook1 (1).png" alt=""><figcaption><p>Directed Graph</p></figcaption></figure>

Strongly Connected Components (SCC) is a concept in graph theory that refers to a group of vertices in a directed graph. Every vertex in the graph is reachable from every other vertex in the same group. In other words, an SCC is a subgraph of a directed graph in which every vertex is reachable from every other point within the same subgraph. The part of the diagram above beyond point E forms a SCC, as shown below.

<figure><img src="../../../.gitbook/assets/water_gitbook2 (1).png" alt=""><figcaption><p>SCC of "A Directed Graph"</p></figcaption></figure>

### **Processes for Arbitrage Identification:**

* Parse the transfers in the transaction, including transfers using ERC20, ERC721 and internal transactions.
* Draw a directed graph based on the transfers.
* Use an algorithm to identify the strongly connected components in the graph. A graph is strongly connected if every vertex can be reached from every other vertex.
* Find the closest point to the "from" or "to" address of the transaction in the above strongly connected components. The "distance" metric is the number of nodes on the shortest path in the strongly connected component. When the "from" or "to" address is already in the graph, the closest point is the "from" or "to" address itself.
* Calculate the token profit and loss for this closest point in the strongly connected component.
* If the token profit and loss for this closest point are positive, we identify this transaction as an Arbitrage.
