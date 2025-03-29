- based on matrix decomposition of (matrix-based) graph representation
	- e.g., adjacency matrix, degree matrix, or Laplacian matrix
- preliminaries from linear algebra
	- [[eigendecomposition of matrix]]
	- orthonormal matrix
		- A matrix $A$ is called orthonormal if its transpose is its inverse. That is, it must hold that
		  $$
		  A^T A = A A^T = I
		  $$
	- similar matrices/matrix conjugation
		- two matrices $A$ and $A'$ are called similar if there exists an invertible matrix $P$ such that $A' = PAP^{-1}$
		- both matrices represent the same linear transformation but with respect to different bases
		- $A$ and $A'$ have the same eigenvalues
		- for the eigenvectors $u$ and $v$ of $A$ and $A'$ respectively, it holds that $u = P v$
			- proof
				- for an eigenvector $u$ of $A$, it holds that
				  $$
				  \begin{align*}
				  A u &= \lambda u \\
				  PAu &= P (\lambda u) \\
				  &= \lambda (P u)
				  \end{align*}
				  $$
				- for $A' = PAP^{-1} \Leftrightarrow P^{-1}A'P = A$, we obtain
				  $$
				  \begin{align*}
				  PAu &= \lambda P u \\
				  P P^{-1} A' P u &= \lambda P u \\
				  A' (P u) &= \lambda (P u)
				  \end{align*}
				  $$
					- $Pu$ is therefore an eigenvector of $A'$, and $\lambda$ is its eigenvalue
		- LATER One of the most fundamental observations in spectral theory regard-
		  ing graph matching is that the eigenvalues and the eigenvectors of the
		  adjacency matrix of a graph are invariant with respect to node permu-
		  tations. Hence, if two graphs are isomorphic, their adjacency matrices
		  will have the same eigenvalues and eigenvectors.
			- Not really identical, no? Eigenvectors as a whole retain their structure; individual coordinates of the eigenvectors may be permuted though
	- permutation matrices
		- identity matrices with either permuted rows or columns
			- permutes rows if pre-multiplied ($PA$)
			- permutes columns if post-multiplied ($AP$)
		- permutation matrices are orthonormal
- test whether graphs are isomorphic
	- observation: two isomorphic graphs have similar adjacency matrices ("similar" in the sense of matrix conjugation)
		- if two graphs are isomorphic, their adjacency matrices (or any other [[graph representation]]) are simply permuted
			- one representation can be expressed in terms of the other through a permutation matrix: $A' = PAP^{-1}$
				- 1st interpretation: change of basis before and after the application of the linear transformation
				- 2nd interpretation: first permutation matrix permutes rows, second (transposed) permutation matrix permutes columns
			- the matrices are therefore similar
				- in other words: spectral properties are invariant under node permutations
			- since permutation matrices are orthonormal, it also holds that $A' = P A P^T$
		- if two graphs are isomorphic, their respective adjacency matrices share eigenvalues and the structure of their eigenvectors
- determine isomorphic mapping
	- overall objective: find bijective mapping $\phi: V \rightarrow V'$
		- typically defined in terms of squared 2-norm on edge labels (interpreted as weights): 
		  $$
		  J(\phi) = \sum_{i = 1}^n \sum_{j = 1}^n (\nu (v_i, v_j) - \nu' (\phi(v_i), \phi(v_j)))^2
		  $$
			- can be reformulated in terms of permutation matrix
			  $$
			  J(P) = ||P A_g P^T - A_{g'}||_2
			  $$
			  with 
			  $$
			  ||A||_2 = \left( \sum_{i = 1}^n \sum_{j = 1}^n (a_{ij})^2 \right)^{\frac{1}{2}}
			  $$
			  (root can be omitted for optimization problem)
		- graphs are isomorphic if there exists a mapping such that $J(\phi) = 0$
		- Finding optimal matching comes down to finding permutation matrix $P$ that minimizes $J(P)$. That is, we aim to solve
		  $$
		  P^* = \argmin_{P \in \mathcal{P}}{J(P)}
		  $$
		  with $\mathcal{P}$ referring to the set of all permutation matrices
			- combinatorial nature and thus hard to solve for large graphs
	- solution can be approximated through eigendecompositions of adjacency matrices
		- LATER Does $\argmin_{P \in \mathcal{P}} ||P - D^*||_2 = \argmax_{P \in \mathcal{P}} tr(P^T D^*)$ generally hold?
		- one can show that if $g$ and $g'$ are isomorphic, the optimal permutation matrix $P^*$ is the solution of 
		  $$
		  P^* = \argmax_{P \in \mathcal{P}}(tr(P^T \bar U_{g'} \bar U_g^T))
		  $$
		  with 
		  $$
		  A_g = U_g \Lambda_g U_g^T \\
		  A_{g'} = U_{g'} \Lambda_{g'} U_{g'}^T
		  $$
		  and $\bar A$ being a matrix made up the element-wise absolute values of $A$
		- instance of an LSAP problem
			- problem can be re-interpreted as problem of assigning rows to columns for all rows and columns in $\bar U_{g'} \bar U_g^T$
				- every row and every column is only contained once in assignment
					- permutation matrix $P$ permutes only rows
					- trace only considers one column per row, and each column only once overall
				- objective is to maximize sum of entries corresponding to assignments (every assignment is a pair of a row and a column) is maximized
		- yields results close to the optimum if applied to graphs that are "nearly isomorphic"
		- limitations
			- may yield bad results for graphs that are not nearly isomorphic
			- all nodes must be part of assignment (i.e., nodes may not be deleted or inserted)
			- graphs need to have identical number of nodes
		- can be solved using traditional optimization techniques by transforming discrete problem into a continuous one
			- consider domain of doubly stochastic matrices $\mathcal{D}$ rather than set of permutation matrices $\mathcal{P}$
				- doubly stochastic matrix (aka. bistochastic matrix) is a square matrix of nonnegative real numbers whose rows and columns all sum up to $1$
				- formally: a square matrix $D = (d_{ij})$ is a doubly stochastic matrix if
				  $$
				  d_{ij} \geq 0 \forall i, j
				  $$
				  and
				  $$
				  \sum_{i = 1}^n d_{ij} = \sum_{j = 1}^n d_{ij} = 1
				  $$
			- turns problem into a convex quadratic problem
				- can be solved in polynomial time (e.g., Frank-Wolfe algorithm)
			- solution needs to be projected to a solution in $\mathcal{P}$
				- can be approximated through 
				  $$
				  \begin{align*}
				  P^* &= \argmin_{P \in \mathcal{P}} J(P) \\
				  &\approx \Pi_{\mathcal{P}} (D^*)
				  \end{align*} 
				  $$
					- $\Pi_{\mathcal{P}} : \mathcal{D} \rightarrow \mathcal{P}$ is projection from domain of doubly stochastic matrices to permutation matrices
					- LATER parentheses to indicate that mapping is a function?
				- assignment can be determined through
				  $$
				  \begin{align*}
				  \Pi_{\mathcal{P}} (D^*) &= \argmin_{P \in \mathcal{P}} ||P - D^*||_2 \\
				  &= \argmax_{P \in \mathcal{P}} tr(P^T D^*)
				  \end{align*}
				  $$
					- the closer $P$ and $D$ are, the better $P^T$ becomes as an approximation of the inverse of $D$
						- for better permutation matrices $P$, the expression $P^T D^*$ becomes closer to $I$
					- as before: can be interpreted as LSAP
						- problem can be re-interpreted as problem of assigning rows to columns for all rows and columns in $D^*$
				- low quality projection step jeopardizes overall solution
			- limitations
				- nodes cannot have labels
				- edges may not have labels other than weights (or other labels for which meaningful cost functions are defined)
				- semantic information of labels could significantly improve search
	- solution can be approximated through use of spectral properties
		- through dissimilarity of feature vectors
			- compute feature vector from spectral decomposition of adjacency matrix
			- alternatively: derive set of polynomials from spectral decomposition of Laplacian matrix, derive feature vector from coefficients of polynomials
		- derive string from adjacency matrix using spectral features and calculate string edit distance
	- solution can be approximated through spectral embeddings
		- interpret $n$ rows of matrix $U_g$ as embeddings
			- cluster nodes of both graphs
			- calculate dissimilarity between nodes of the same cluster