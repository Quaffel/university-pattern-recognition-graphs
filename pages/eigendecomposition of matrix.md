- eigenvector and eigenvalue
	- A (nonzero) vector $u$ of dimension $n$ is an eigenvector of a $n \times n$ square matrix $A$ if it satisfies a linear equation of the form
	  $$
	  Au = \lambda u
	  $$
	  for some scalar $\lambda$. Then $\lambda$ is called the eigenvalue corresponding to eigenvector $u$
- eigendecomposition of a matrix
	- Let $A$ be a $n \times n$ square matrix with $n$ linearly independent eigenvectors $u_i$ (with $i = 1, ..., n$). Then, $A$ can be factorized as
	  $$
	  A = U \Lambda U^{-1}
	  $$
	  where $U$ is a $n \times n$ square matrix whose $i$-th column is the eigenvector $u_i$ of $A$, and $\Lambda$ is a diagonal matrix whose diagonal elements are the eigenvalues corresponding to the $i$-th eigenvector $u_i$, i.e., $\Lambda(i, i) = \lambda_i$
	- If $A$ is symmetric, then...
		- ... the eigenvectors and eigenvalues are real
		- ... $U$ is orthonormal
- eigenmode index
	- ethymology
		- The term is closely linked to oscillatory systems where eigenvectors describe inherent patterns of motion, deformation, or propagation. Since many systems described by differential equations (such as vibrating strings or wave equations) naturally produce discrete, distinct solutions, these solutions are referred to as modes.
	- when sorting the eigenvalues in decreasing order, the eigenmode index indicates the index of an eigenvalue (and its corresponding eigenvector) in the sorted order
		- that is, in an order of eigenvalues $|\lambda^1| > |\lambda^2| > \dots > |\lambda^{|V|}|$, the index $i$ in $\lambda$ is termed the eigenmode index
	- ordering eigenvalues helps to overcome the correspondence problem when comparing spectral features of multiple matrices
- modal matrix
	- generally a matrix composed of the eigenvectors $u_1, \dots, u_{|V|}$ of some matrix $A$
	- here: matrix composed of a column-wise concatenation of eigenvectors in order of the eigenvectors' eigenmode index
		- $U = (u_1 | u_2 | \dots | u_{|V|})$
		- can also be truncated to only include the eigenvectors with the $n < |V|$ largest eigenvalues