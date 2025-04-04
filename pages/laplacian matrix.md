- general properties
	- derived from adjacency matrix and degree matrix
	- also known as laplacians
- variants
	- unnormalized laplacian
		- $L = D - A$
		- $$l_{ij} = \begin{cases}
		  deg(v_i) &\text{ if } i = j \\
		  -1 &\text{ if } i \neq j \text{ and } (v_i, v_j) \in E\\
		  0 &\text{ otherwise}
		  \end{cases}$$
	- symmetrically normalized laplacian matrix
		- vertices with large degrees result in large diagonal entries in laplacian, which may dominate matrix properties
		- normalization reduces this effect
		- $L^{sym} = (D^+)^{1 /2} L(D^+)^{1 /2}$
			- $D^+$ being the Moore-Penrose inverse (also known as pseudoinverse, even though concept of pseudoinverses is broader)
		- $$l_{ij} = \begin{cases}
		  1 &\text{ if } i = j \text{ and } deg(v_i) \neq 0\\
		  \frac{-1}{\sqrt{deg(v_i) deg(v_j)}} &\text{ if } i \neq j \text{ and } (v_i, v_j) \in E\\
		  0 &\text{ otherwise}
		  \end{cases}$$
		- either in- or out-degree can be used for normalization
- properties
	- all presented variants
		- let $L$ be the Laplacian matrix of the undirected graph $g = (V, E)$
			- eigenvectors of $L$ are real
			- $L$ is an [[orthonormal matrix]] (since $L$ is symmetric)
			- $L$ has exactly $n$ eigenvectors
				- holds since $L$ is diagonalizable, which follows from its symmetry
			- all eigenvalues of $L$ are non-negative
				- i.e., $\forall i \in [1, n] : \lambda_i \geq 0$
				- holds since $L$ is ...
					- ... symmetric
					- ... positive-semidefinite
						- holds since $L$ is is Hermitian (as $L$ is symmetric) and a diagonally dominant matrix
			- number of connected components of $g$ is equal to number of zero-valued eigenvalues $\lambda_i$
				- $\lambda_2 \neq 0$ (with $2$ being the eigenvector's eigenmode) if and only if $g$ is connected
				- holds as number of zero-valued eigenvalues corresponds to rank deficiency of matrix
					- having more than one connected component necessarily implies rank deficiency of at least 2
						- e.g., consider adjacency matrix of graph with 4 nodes and two connected components
					- every connected component increases rank deficiency by one as maximum degree is bounded by $|C| - 1$ (with $C$ being the number of nodes in a connected component)
				- eigenvectors corresponding to zero-valued eigenvalues are indicator vectors of the corresponding connected component
					- eigenvector corresponding to the zero-valued eigenvalue in a connected graph has all coordinates set to 1
			-