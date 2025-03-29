- definition
	- for graph-based use cases
		- intuition
			- labels are assigned to graphs as a whole, i.e., every candidate graph has a label $\omega \in \Omega$
			- we first determine the set of the $k$ closest graphs among all candidate graphs
				- note the use of parentheses in the index to distinguish between graphs in the entire training set and the $k$ closest graphs
			- among the $k$ closest graphs, we count how often every label occurs, and select the label with the highest count
		- Let $G$ be a graph domain, $d: G \times G \rightarrow \mathbb{R}$ be a graph distance, and $\{(g_i, \omega_i)\}_{1 \leq i \leq N} \subseteq G \times \Omega$ a labeled set of N training graphs. If $\{(g_{(1)}, \omega_{(1)}), \dots, (g_{(k)}, \omega_{(k)})\} \subseteq \{(g_i, \omega_i)\}_{1 \leq i \leq N}$ are those $k$ graphs in the training set that have the smallest distance $d(g, g_{(i)})$ to an input graph $g \in G$, the $k$-NN classifier $f: G \rightarrow \Omega$ is defined by
		  $$
		  f(g) = \argmax_{\omega \in \Omega} |\{(g_{(i)}, \omega_{(i)}) : \omega_{(i)} = \omega\}|
		  $$
		-
- ties can be ...
	- ... resolved by assigning class of 1-NN
	- ... resolved by assigning class of closest center (mean vector)
	- ... avoided using a $k$ that is not divisible by the number of classes
- optimizations
	- determine a subset of the original training set
	- eliminate elements that don't affect classification result for training elements
	- both techniques can be applied to the same dataset, as both effects are desirable (and perhaps complementary)
	- condensing
		- start with an empty set, and only add elements that are wrongly classified
			- if they are correctly classified, the surrounding elements already ensure correct classification
	- editing
		- start with complete set and mark all elements for deletion that are wrongly classified
			- if element is wrongly classified, the surrounding elements supersede the tested element
		- typically more conservative than condensing