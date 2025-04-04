- motivation
	- number of common neighbors reflects core idea of [[structural equivalence]]
		- number of nodes that two nodes $u_i, u_j \in V$ of some graph $g = (V, E)$ have in common is given by
		  $$
		  n_{ij} = |\mathcal{N}(u_i) \cap \mathcal{N}(u_j)| = \sum_{k = 1}^N a_{ik} a_{kj}
		  $$
		  with $A(i, j) = (a_{ij})$ being the adjacency matrix of $g$
		- $n_{ij}$ corresponds to the element indexed by $ij$ in the squared adjacency matrix $A^2$
			- any vertex that two nodes $u$ and $j$ have in common connects $u$ and $j$ with a unique path of length 2
- idea
	- use normalization to put number of common neighbors into perspective (e.g., in terms of node degrees or number of common nodes that other graphs share)
	- cosine similarity provides normalized similarity measure on vector spaces
		- dot product between two vectors $x, y$ is defined as $\langle x, y \rangle = |x| |y| \cos \theta$
			- $|\bullet|$ designates magnitude of vector (typically L2 norm)
			- $\theta$ represents angle between $x$ and $y$
		- cosine of angle between vectors is hence given by
			- $\cos \theta = \frac{\langle x, y \rangle}{|x| |y|}$
		- interpretation
			- $\cos \theta = -1$ means that vectors point to opposite directions
				- indicates minimum similarity / maximum dissimilarity
				- recall that $\cos^{-1} (-1) = 180 \degree$
			- $cos \theta = 1$ means that vectors point to identical direction
				- indicates maximum similarity / minimum dissimilarity
				- recall that $cos^{-1}(1) = 0 \degree$
- definition
	- Let $g = (V, E)$ be an undirected graph and $u_i, u_j \in V$. Then, the cosine similarity of $u_i$ and $u_j$ is given by
	  $$
	  s_{cos} (u_i, u_j) = \frac{n_{ij}}{\sqrt{\deg (u_i) \bullet \deg(u_j)}}
	  $$
- intuition
	- apply cosine similarity to rows (or columns) of adjacency matrix that correspond to the two nodes to be compared
	- Let $b_k$ represent the $k$-th row (or column) of the adjacency matrix. The cosine similarity of two nodes $u_i, u_j$ is defined as
	  $$
	  \begin{align*}
	  s_{cos} (u_i, u_j) &= \frac{\langle b_i^T b_j \rangle}{{||b_i||}_2 \bullet {||b_j||}_2} \\
	  &= \frac{\langle b_i^T b_j \rangle}{\sqrt{b_i^T b_i} \bullet \sqrt{b_j^T b_j}}
	  \end{align*}
	  $$
	- we observe that $b_i^T b_j = \sum_{k = 1}^N a_{ik} a_{kj}$, which allows us to further simplify as
	  $$
	  \begin{align*}
	  s_{cos} (u_i, u_j) &= \frac{\sum_{k = 1}^N a_{ik} a_{kj}}{\sqrt{\sum_{k = 1}^N a_{ik}^2} \bullet \sqrt{\sum_{k = 1}^N a_{jk}^2}}
	  \end{align*}
	  $$
	- In this context, the adjacency matrix only contains zeros and ones. Therefore, we conclude that $a_{ik}^2 = a_{ik}$, which implies that $\sum_{k = 1}^N a_{ik}^2 = \sum_{k = 1}^N a_{ik} = \deg(u_i)$. We simplify further such that
	  $$
	  \begin{align*}
	  s_{cos} (u_i, u_j) &= \frac{\sum_{k = 1}^N a_{ik} a_{kj}}{\sqrt{\deg (u_i)} \bullet \sqrt{\deg(u_j)}}
	  \end{align*}
	  $$
	- We finally note that $\sum_{k = 1}^N a_{ik} a_{kj} = n_{ij}$, which leaves us with above expression
- properties
	- value range
		- cosine similarity of $1$ indicates that two nodes have exactly the same neighbors
		- cosine similarity of $0$ indicates that two nodes have no neighbors in common
		- between $0$ and $1$
			- cosine similarity on real vector spaces may take values in $[-1, 1]$
			- cosine similarity on nodes is always positive as the expression only contains positive factors (i.e., $n_{ij}$ is positive, but $\langle x, y \rangle$ isn't necessarily)
		-