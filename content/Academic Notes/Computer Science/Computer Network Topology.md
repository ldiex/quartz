At any moment, the structure of a *network* is a [[Graph|graph]], showing what *nodes* and *edges* are in the network, and how the nodes are interconnected by the edges. This graph is also called the *topology of the network*. The topology of a network may change with time. Depending on how the network topology changes, we can classify networks into three classes:

- **Static networks**. Static networks do not change their nodes and edges. More precisely, a network $G = (V,E)$ is a static network, if the node set $V$ and the edge set $E$ do not change over time.
- **Dynamic networks**. A dynamic network does not change its nodes, but may change its edges.
- **Evolutionary networks**. Evolutionary networks change both nodes and edges
over time. An example is the network of all webpages on the *World Wide Web*. The node set $V$ (the set of all webpages) and the edge set $E$ (the set of Web links) both constantly change over time.

> [!example]  How Network Topology Helped Create Modern Search Engines
> Early search engines computed search results by matching the key-words in search queries to the contents of webpages (nodes). These *first-generation search engines* only utilized nodes of the network of webpages.
> 
> Around 1996, Jon Kleinberg, Robin Li (李彦宏), and Larry Page, independently observed a phenomenon: Web links (edges) also significantly influence the relevance of search results. They utilized both nodes and edges to develop the *second-generation search engines* with much better results. This approach more fully utilizes network thinking and created Google and Baidu companies, serving billions of users and generating annual revenue over $100 billion.



 

