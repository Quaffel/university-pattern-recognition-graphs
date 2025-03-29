- motivation
	- [[subtree kernel]] has complexity $\mathcal{O}(n^2 h 4^d)$
- intuition
	- instance of [[Weisfeiler-Lehman kernel]]
	- builds on top of [[Weisfeiler-Lehman isomorphism test]]
		- based on observation that the compressed labels $l_i(v)$ correspond to [[subtree pattern]]s of height $i$ rooted at node $v$
			- example: node with label $l_1(v) = 8 (2, 35 \rightarrow 8)$ indicates that there is a subtree pattern of height $1$ rooted at $v$, with $l_0(v) = 2$ and its neighbors have labels $3$ and $5$
- required abstractions
	- set of node labels $\Sigma_i$
		- Let $g$ and $g'$ be graphs. We have $\sum_i$ as the set of symbols that occur as node labels at least once in $g$ or $g'$ at the end of the $i$th iteration of the Weisfeiler-Lehman procedure
			- without loss of generality, we assume every $\Sigma_i = \{\sigma_{i1, \dots, \sigma_{i |\Sigma_i|}}\}$ is ordered
			- $\Sigma_0$ corresponds to $\Sigma = \mu \cup \mu'$, i.e., $\Sigma_0$ contains original labels of $g$ and $g'$
		- provided by Weisfeiler-Lehman kernel
	- map of occurrences $c_i$
		- We define a map $c_i : \mathcal{G} \times \Sigma_i \rightarrow \mathcal{N}$ such that $c_i(g, \sigma_{ij})$ is the number of occurrences of symbol $\sigma_{ij}$ in graph $g$
- definition
	- The Weisfeiler-Lehman subtree kernel on two graphs $g$ and $g'$ with $h$ iterations is defined as
	  $$
	  \kappa_{\text{WL-subtree}, h}(g, g') = \langle \Psi_{WL, h}(g), \Psi_{WL, h}(g') \rangle
	  $$
		- we define $\Psi_{WL, h}(g)$ such that
		  $$
		  \Psi_{WL, h}(g) = (c_0(g, \sigma_{01}), \dots, c_0(g, \sigma_{0 |\Sigma_0|}), \dots, c_h(g, \sigma_{h 1}), \dots, c_h(g, \sigma_{h |\Sigma_0|}))
		  $$
		  and
		  $$
		  \Psi_{WL, h}(g') = (c_0(g', \sigma_{01}), \dots, c_0(g', \sigma_{0 |\Sigma_0|}), \dots, c_h(g', \sigma_{h 1}), \dots, c_h(g', \sigma_{h |\Sigma_0|}))
		  $$
			- not directly the base kernel but yields an expression that contains the base kernels
			- recall that base kernel is of form $\kappa_{WL, h}(g, g') = \kappa(g_0, g_0') + \kappa(g_1, g_1') + \dots + \kappa(g_h, g_h')$, meaning that one summand in the dot product corresponds to one base kernel
			- LATER Should be $c_h$, no?
- complexity
	- computing kernel value for a pair of graphs: $\mathcal{O}(hm)$
		- $h$ refers to height up until which all subtrees are considered
		- $m$ refers to number of edges
		- corresponds to complexity of [[Weisfeiler-Lehman isomorphism test]]
- differences to [[subtree kernel]]
	- not an exact substitute
	- considers subtrees
		- Weisfeiler-Lehman subtree kernel considers all subtrees up to height $h$
		- subtree kernel considers all subtrees of exactly height $h$
	- accuracy
		- Weisfeiler-Lehman subtree kernel checks whether neighborhoods of $v$ and $v'$ match exactly
		- subtree kernel considers all pairs of matching subsets of the neighborhoods of $v$ and $v'$