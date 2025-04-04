- motivation
	- [[direct product graph]]s only considers pairs of vertices in $g$ and $g'$ with identical label
		- vertices with similar but unequal labels are not considered
	- problematic when dealing with continuous label values
- definition
	- the modified direct product of two graphs $g = (V, E, \mu, \nu)$ and $g' = (V', E', \mu', \nu')$ is the graph $(g \times g') = (V_\times, E_\times, \mu_\times, \nu_\times)$ defined by
		- $V_\times = V \times V'$
			- a node in $V_\times$ represents two vertices, one in $V$ and one in $V'$
			- node can be represented as a mapping
		- $E_\times$: There is an edge between the nodes $(u, u')$ and $(v, v')$ if the following holds:
			- $e \in E \wedge e' \in E'$
			- (with $e = (u, v)$ and $e' = (u', v')$)
			- (with $u \neq v, u' \neq v'$)
- adjacency matrix
	- adjacency matrix typically defined such that cells measure similarity of the corresponding edges (i.e., walks of length 1)
		- cell values are formally defined as
		  $$
		  A_\times = \left(a_{(u, u'), (v, v')} \right) = \begin{cases}
		  \kappa_{\text{walk}^{(1)}} ((u, u'), (v, v')) & \text{if } ((u, u'), (v, v')) \in E_\times \\
		  0 & \text{otherwise}
		  \end{cases}
		  $$
		- kernel function $\kappa_{\text{walk}^(1)}$ measures similarity of a walk of length 1
			- approach: compute product of kernel values of all nodes and edges encountered along the walk
				- $\kappa_{\text{walk}^{(1)}} ((u, u'), (v, v')) = \kappa(u, u') \bullet \kappa((u, v), (u', v')) \bullet \kappa(v, v')$
				- separate kernel function for nodes and edges
			- approach: compute product of kernel kernel values of all nodes encountered along the walk (if no edge kernel is available)
				- $\kappa_{\text{walk}^{(1)}} ((u, u'), (v, v')) = \kappa(u, u') \bullet \kappa(v, v')$
	- can be interpreted as a fuzzy adjacency matrix indicating adjacency and similarity
		- assigns higher adjacency values to nodes of the product graph if corresponding pairs of nodes and edges in $g$ and $g'$ are similar, and lower values otherwise
- similar but not equal to [[direct product graph]]
	- direct product graph only considers pairs of vertices in $g$ and $g'$ with identical label
-