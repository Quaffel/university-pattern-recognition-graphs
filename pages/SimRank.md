- idea
	- two nodes $u, v \in V$ are similar if their neighbors are similar
	- similarity score $s_{SimRank}(u, v)$ is high if $u$ and $v$ have neighbors that themselves have high similarity
- definition
	- Let $g = (V, E)$ be a graph. SimRank is recursively defined as
	  $$
	  s_{SimRank} (u, v) = \begin{cases} \\
	  1 & \text{if } u = v \\
	  \frac{C}{|\mathcal{N}(u)| |\mathcal{N}(v)|} \sum_{w \in \mathcal{N}(u)} \sum_{q \in \mathcal{N}(v)} s_{SimRank}(w, q) & \text{otherwise}
	  \end{cases}
	  $$
	  where $C$ is a decay factor with $0 < C < 1$ which penalizes longer paths
	- alternative iterative formulation
		- $$
		  s_{SimRank}^{(k)} (u, v) = \begin{cases} \\
		  1 & \text{if } u = v \\
		  \frac{C}{|\mathcal{N}(u)| |\mathcal{N}(v)|} \sum_{w \in \mathcal{N}(u)} \sum_{q \in \mathcal{N}(v)} s_{SimRank}^{(k - 1)} (w, q) & \text{otherwise}
		  \end{cases}
		  $$
		- equivalent with previous formulation if function is repeatedly applied til convergence
			- practically only performed for a fixed number of iterations (chosen in terms of $C$)
			- previous formulation would never return a value ("endless loop") if it didn't converge
- properties
	- value range
		- between $0$ and $1$
		- SimRank of value $1$ indicates that ...
			- ... $u = v$ or
			- $u$ and $v$ have a common clique and that $u$ and $v$ have no neighbors outside of that clique (?)