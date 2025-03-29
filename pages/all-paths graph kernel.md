- motivation
	- [[random walk graph kernel]]s may suffer from tottering
		- by iteratively visiting the same cycle of nodes, a walk can produce artificially high similarity values
		- walks allow for repeated nodes, paths don't
- definition
	- Given two graphs $g_1$ and $g_2$, let $\mathcal(P_1)$ and $\mathcal(P_2)$ be the set of all paths in graphs $g_1$ and $g_2$, respectively. We then define the all-paths kernels as
	  $$
	  \kappa_{AP}(g_1, g_2) = \sum_{p_1 \in \mathcal{P}(g_1)} \sum_{p_2 \in \mathcal{P}(g_2)} \kappa_{\text{path}}(p_1, p_2)
	  $$
		- $\kappa_{path}$ is a positive definite (i.e., valid) kernel on two paths, defined as the product of kernels on edges and nodes along the path
			- For paths of length 1, it holds that
			  $$
			  \kappa_{\text{path}^{(1)}} (p_1, p_2) = \kappa(u, u') \bullet \kappa((u, v), (u', v')) \bullet \kappa(v, v')
			  $$
		- i.e., all-paths kernel is defined as the sum over all kernels on pairs of paths from $g_1$ and $g_2$
- properties
	- all-paths graph kernel is positive definite (i.e., valid)
- complexity
	- finding all paths
		- NP-hard
		- finding special subsets of graphs is not necessarily NP-hard, which motivates [[shortest path graph kernel]]s