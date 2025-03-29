- build vector using statically determined features of the graph
	- statistical key figures
		- number of nodes or edges (optionally per label)
		- number of edges between nodes labeled with a certain label
		- minimum, maximum, and average degree of nodes
	- constitutional descritpors
		- numerical quantifiers of the graph topology that...
			- ... are independent of the actual node ordering
			- ... sensitive to one or more structural features of the graph
				- e.g., size, shape, symmetry, branching, cyclicity
- LATER Difference between constitutional and topological descriptors?
- any graph can be represented as an $n$-dimensional vector of real numbers by combining $n$ topological descriptors
	- $\varphi(g) = (D_1(g), \dots, D_n(g)) \in \mathbb{R}^n$ for $n$ topological descriptors $D_i$ with $i = 1, \dots, n$
- topological descriptors
	- Zagreb index
		- sum of squared node degrees
		- $Z_1(g) = \sum_{v \in V} \text{deg}(v)^2$
	- Narumi simple topological index
		- product of node degrees
		- $N(g) = \prod_{v \in V} \text{deg}(v)$
	- polarity number
		- number of pairs of nodes that are connected via a path of length 3
		- $P(g) = \sum_{u \in V} \sum_{v \in V} \sigma(d(u, v))$
			- $d(u, v)$ denotes length of the shortest path between $u$ and $v$ (can be determined through distance matrix)
			- $$
			  \sigma = \begin{cases}
			  1 &\text{if } x = 3 \\
			  0 &\text{otherwise}
			  \end{cases}
			  $$
	- Wiener index
		- sum of the lengths of the shortest paths between all pairs of nodes in the graph
		- $W(g) = \sum_{u \in V} \sum_{v \in V} d(u, v)$
			- $d(u, v)$ denotes length of the shortest path between $u$ and $v$ (can be determined through distance matrix)
	- Randic index / connectivity index
		- considers the product of the degrees of the nodes $u$ and $v$ that are incident to an edge $(u, v) \in E$
		- $R(g) = \sum_{(u, v) \in E} \frac{1}{\sqrt{\text{deg}(u) \bullet \text{deg}(v)}}$
	- Balaban-J-index
		- $B(g) = \frac{m}{m - n + 2} \sum_{(u, v) \in E} \frac{1}{\sqrt{s(u) \bullet s(v)}}$
			- $s(u)$ denotes the sum of the lengths of the shortest path between $u$ and all other nodes in the graph
				- $s(u) = \sum_{v \in V, v \neq u} d(u, v)$
			- $d(u, v)$ denotes length of the shortest path between $u$ and $v$ (can be determined through distance matrix)
			- $n$ denotes number of nodes, $m$ denotes number of edges