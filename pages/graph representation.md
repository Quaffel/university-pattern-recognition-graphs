- A _representation_ of a graph $G = (V, E)$, with $V = \{v_1, v_2, \dots, v_n\}$, is any object $R(G; v_1, v_2, \dots, v_n)$ such that, given any other graph $G' = (V', E')$ with $V' = \{w_1, w_2, \dots, w_n\}$, then $G \tilde{=} G'$ with an isomorphism $f: V \rightarrow V'$ such that $f(v_i) = w_i$ (cf. [[graph isomorphism]]) if and only if
  $$
  R(G; v_1, v_2, \dots, v_n) = R(G'; w_1, w_2, \dots, w_n)
  $$
- adjacency matrix
	- $A = a(i, j) (i, j = 1, \dots, n)$
	- matrix in which every vertex indexes a particular row and column
	- $$a_{ij} = \begin{cases}
	  1 &\text{ if } (v_i, v_j) \in E \\
	  0 &\text{ otherwise}
	  \end{cases}$$
	- for labelled graphs, the edge label can be encoded as well
	  $$a_{ij} = \begin{cases}
	  \nu((v_i, v_j)) &\text{ if } (v_i, v_j) \in E \\
	  0 &\text{ otherwise}
	  \end{cases}$$
- degree matrix
	- $D = d(i, j) (i, j = 1, \dots, n)$
	- matrix in which every vertex indexes a particular row and column
	- diagonal specifies degree of vertices, rest of matrix is zeroed out
	- $$d_{ij} = \begin{cases}
	  deg(v_i) &\text{ if } i = j \\
	  0 &\text{ otherwise}
	  \end{cases}$$
- [[laplacian matrix]]
- adjacency list
	- useful for sparse graphs
		- graphs are sparse if they have a low density or (equivalently) that the average degree of the graph is much lower than the number of nodes in the graph
	- list of "neighbor sets" for all vertices: $(\mathcal{N}(v_1), \mathcal{N}(v_2), \dots, \mathcal{N}(v_n))$
	- implications on operation efficiency
		- listing neighbors: linear in number of neighbors
			- as opposed to adjacency list, where operation is linear in number of vertices in the graph
		- adjacency test: linear in number of neighbors
			- as opposed to adjacency matrix, where operation is constant
	-