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