- intuition
	- [[node embedding]]s can be represented as matrices (cf. ((67ef9376-afce-44be-9d75-e7ff34042c22)))
	- use matrix of eigenvectors resulting from eigendecomposition (cf. [[eigendecomposition of matrix]]) of [[laplacian matrix]] as embedding
		- as eigenvectors are orthogonal to each other, they span a coordinate system of a node embedding
- definition
	- Let $L$ be the (normalized or unnormalized) Laplacian matrix of a graph $g = (V, E)$ with $|V| = n$. For the eigendecomposition $L = U \Lambda U^T$ of $L$, the spectral embedding $Z$ of $L$ is given by
	  $$
	  Z = U
	  $$
	- practically truncated to reduce dimensionality
		- eigenvectors with zero-valued eigenvalues are not informative and can be omitted
		- consider $d$ smallest, non-zero eigenvalues
			- i.e., consider $0 < \lambda_{(1)} < \dots < \lambda_{(d)}$
		- stack $d$ considered eigenvectors to form a new embedding $Z_d \in \mathbb{R}^{|V| \times d}$
			- $d$ represents dimensionality of embedding
			- embedding value of node is composed of one coordinate per eigenvector (i.e., the one that corresponds to the node in the adjacency matrix)
- interpretation
  id:: 67ef9cf6-1bbb-48fd-a290-da44625a19b8
	- eigenvectors corresponding to smaller eigenvalues capture information about the global graph structure (and are hence more informative)
		- small eigenvalue indicates that eigenvector is comparatively insensitive to changes
		- Recall that every row in the Laplacian matrix sums up to zero and may contain exactly one element that is not of value $0$ or $-1$. Assuming that an eigenvector has a non-zero coordinate for that element, increasing the number of considered elements brings the resulting vector closer to the zero vector
- properties
	- minimizes ((67ef7a78-1e73-4492-b613-de8c601b66b1))
		- does not directly optimize for cosine similarity (or other measures quantifying structural equivalence) but indirectly
	- does not reduce dimensionality per-se
		- $Z$ is of dimension $|V| \times |V|$
		- reduce computational effort by only considering a subset of eigenvectors (cf. ((67ef9cf6-1bbb-48fd-a290-da44625a19b8)))