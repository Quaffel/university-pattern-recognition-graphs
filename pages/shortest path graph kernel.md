- prerequisites
	- transform original graph $g = (V, E)$ into shortest-paths graph $s$
		- $s = (V, E')$
			- same set of vertices as $g$
			- two nodes are adjacent if they are connected in $g$
			- edges are labeled by ...
				- shortest distance between the two adjacent nodes ($d(v_i, v_j)$)
				- number of edges in the shortest path between the two adjacent nodes ($\text{steps}(v_i, v_j)$)
		- information on shortest paths can be obtained from [[Floyd-Warshall algorithm]]
- definition
	- Let $g_1$ and $g_2$ be two graphs that are Floyd-transformed into $s_1 = (V_1, E_1,)$ and $s_2 = (V_2, E_2)$ (i.e., $s_1$ and $s_2$ are shortest-paths graphs). We define the shortest-path graph kernel by
	  $$
	  \kappa_{SP}(s_1, s_2) = \sum_{(u, v) \in E_1} \sum_{(u', v') \in E_2} \kappa_{\text{path}^{(1)}} ((u, v), (u', v'))
	  $$
	  where $\kappa_{\text{path}^{(1)}}((u, v), (u', v'))$ is a kernel function on a path of length $1$.
- popular kernels for $\kappa_{\text{path}^{(1)}}((u, v), (u', v'))$
	- product of kernel values of all edge and node labels along the path
		- $\kappa_{\text{path}^{(1)}} (p_1, p_2) = \kappa(u, u') \bullet \kappa((u, v), (u', v')) \bullet \kappa(v, v')$
			- takes two paths as an input
			- two kernel expressions operate on nodes, one on edges
		-
- complexity
	- finding shortest paths for all pairs of paths
		- Floyd-Warshall algorithm has complexity of $\mathcal{O}(n^3)$
		- Dijkstra (only for shortest paths from one source node to all other nodes) algorithm has complexity of $\mathcal{O}(m + n \log n)$
	- computing the kernel value
		- if original graph is connected, the shortest-paths graph $s$ contains $n^2$ edges
		- we assume other graph to contain $n'$ nodes (hence $n'^2$ edges), and that $n' < n$
		- kernel value is computed by iterating over all possible pairs of edges
			- need to consider $n^2 \bullet n'^2$ pairs of edges
			- results in total runtime of $\mathcal{O}(n^4)$
		- motivates [[equal length shortest-path graph kernel]]