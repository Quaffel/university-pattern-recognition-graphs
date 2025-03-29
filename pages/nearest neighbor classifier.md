- discriminative classifier
- in case of statistical representation
	- $X = \mathbb{R}^n$
	- $\theta$ is set of learning samples
	- $f_\theta$ assign the class of the most similar known sample
		- LATER $$
		  f_\theta (x) = C_i \Leftrightarrow \text{argmin}
		  $$
- ties can be resolved by random classification or rejection
- results in Voronoi partition of Euclidean space
- distance measures
	- LATER Euclidean distance $L_n (x, p)$
		- special cases
	- dissimilarity measures
		- e.g., string edit distance (levenshtein distance), graph edit distance
		- relevant for structural pattern recognition