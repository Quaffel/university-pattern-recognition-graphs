- required abstractions
	- Weisfeiler-Lehman relabelling function $r(g)$
		- [[Weisfeiler-Lehman isomorphism test]] algorithm consists of two steps
			- multiset-label determination/propagation and sorting
			- label compression and relabeling
		- both steps are deterministic and produce equal outputs for equal graphs
			- if two graphs have identical multiset labels, the relabeling function yields identical new labels for both graphs
		- relabeling function can be thought of as graph transformation function: $r(g) = r((V, E, l_i)) = (V, E, l_i + 1)$
			- LATER Weisfeiler-Lehman iteration as a whole and not only invocation of relabeling function, right?
	- Weisfeiler-Lehman graph
		- We define the Weisfeiler-Lehman graph at height $i$ of the graph $g = (V, E, \mu) = (V, E, l_0)$ as the graph $g_i = (V, E, l_i)$.
		- $g_i$ is output of $r(g_{i - 1})$
	- Weisfeiler-Lehman sequence
		- We call the sequence of Weisfeiler-Lehman graphs
		  $$
		  \{g_0, g_1, \dots, g_h\} = \{(V, E, l_0), (V, E, l_1), \dots, (V, E, l_h)\}
		  $$
		  where $g_0 = g$ and $l_0 = \mu$, the Weisfeiler-Lehman sequence up to height $h$ of $g$
		- note that only labels are updated; nodes and edges remain unchanged
- definition
	- Let $\kappa$ be any kernel for graphs, that we will call the base kernel. Then the Weisfeiler-Lehman kernel with $h$ iterations with the base kernel $\kappa$ is defined as
	  $$
	  \kappa_{WL, h}(g, g') = \kappa(g_0, g_0') + \kappa(g_1, g_1') + \dots + \kappa(g_h, g_h')  
	  $$
	  where $h$ is the number of Weisfeiler-Lehman iterations and $g_0, \dots, g_h$ and $g_0', \dots, g_h'$ are the Weisfeiler-Lehman sequences of $g$ and $g'$, respectively.
- properties
	- positive definite (i.e., valid) if base kernel is positive definite
- variants
	- [[Weisfeiler-Lehman subtree kernel]]
- further reading
	- Weisfeiler-Lehman graph kernels ([paper](https://www.jmlr.org/papers/volume12/shervashidze11a/shervashidze11a.pdf))