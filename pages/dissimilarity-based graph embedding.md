- build vector by calculating a graph's distance to a set of prototype graphs $\mathcal{P}$ (i.e., training graphs)
	- Let $\mathcal{G}$ be a graph domain. If $\mathcal{P} = \{p_1, \dots, p_n\} \subseteq \mathcal{G}$ is a prototype set with $n$ graphs, the mapping $\varphi : \mathcal{G} \rightarrow \mathcal{R}^n$ is defined as the function
	  $$
	  \varphi(g) = (d(g, p_1), \dots, d(g, p_n))
	  $$
	  where $d(g, p_i)$ is any graph dissimilarity measure (e.g., a distance, such as a [[graph edit distance]]) between graph $g$ and the $i$-th prototype graph
	- Can be alternatively defined as
	  $$
	  \varphi(g) = \frac{1}{\sqrt{n}}(d(g, p_1), \dots, d(g, p_n))
	  $$
	  When calculating the Euclidean distance between two such dissimilarity vectors, it is guaranteed that the distance is at most the original graph dissimilarity $d(g, g')$
- observations
	- the more similar two graphs $g$ and $g'$ are, the smaller is the Euclidean distance of the resulting dissimilarity vectors
		- $$
		  \begin{align*}
		  ||\varphi(g) - \varphi(g')|| &= (\langle \varphi(g), \varphi(g) \rangle + \langle \varphi(g'), \varphi(g') \rangle - 2 \langle \varphi(g), \varphi(g') \rangle)^{\frac{1}{2}} \\
		  &= \left( \sum_{i = 1}^n d(g, p_i)^2 + \sum_{i = 1}^n d(g', p_i)^2 - 2 \sum_{i = 1}^n d(g, p_i) d(g', p_i) \right)^{\frac{1}{2}} \\
		  &= \left( \sum_{i = 1}^n (d(g, p_i) - d(g', p_i))^2 \right)^{\frac{1}{2}}
		  \end{align*}
		  $$
		- provided $d$ is a metric: the more similar $g$ and $g'$ are, the smaller will be the difference in the term and hence also the overall Euclidean distance
	- provided $d$ is a metric: Euclidean distance of the resulting dissimilarity vectors is bound by $\sqrt{n} \bullet d(g, g')$
		- $$
		  \begin{align*}
		  ||\varphi(g) - \varphi(g')|| &= \left( \sum_{i = 1}^n (d(g, p_i) - d(g', p_i))^2 \right)^{\frac{1}{2}} \\
		  &\leq (n \bullet d(g, g')^2)^{\frac{1}{2}} \\
		  &= \sqrt{n} \bullet d(g, g')
		  \end{align*}
		  $$
		- follows from triangle inequality
			- $$
			  \begin{align*}
			  d(g, p_i) &\leq d(g, g') + d(g', p_i) \\
			  d(g, p_i) - d(g', p_i) &\leq d(g, g')
			  \end{align*}
			  $$
- selection of prototype graphs
	- quality of prototype graphs and number of prototype graphs are crucial for quality of embedding
	- prototype graphs should not be redundant and should include as much information as possible (with a reasonable number of prototypes)
		- prototypes should be uniformly distributed over the whole set of graphs
	- approach: start with set median graph, add graph with maximum minimal distance
		- ![dissimilarity-graph-embedding-prototype-selection-implementation.png](../assets/dissimilarity-graph-embedding-prototype-selection-implementation_1742563849989_0.png)
		- initialize set with set median graph
			- Let $\mathcal{G}$ be a set of graphs. The median set graph is defined as
			  $$
			  \text{median}(\mathcal{G}) = \argmin_{g_1 \in \mathcal{G}} \sum_{g_2 \in \mathcal{G}} d(g_1, g_2)
			  $$
			- set median graph is the graph whose sum of distances to all other graphs in $\mathcal{G}$ is minimal
			- intuitively, set median graph is located in the center of a given graph set
		- add graph that is the furthest away from already selected prototype graphs
			- e.g., select graph that maximizes the minimal distance to the already selected prototypes