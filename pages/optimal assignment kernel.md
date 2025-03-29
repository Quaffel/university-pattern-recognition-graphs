- intuition
	- decompose two graphs $g_1 = (V_1, E_1, \mu_1, \nu_1)$ and $g_2 = (V_2, E_2, \mu_2, \nu_2)$ into substructures $X = \{x_1, \dots, x_n\}$ and $Y = \{y_1, \dots, y_m\}$
		- simplest case: $X = V_1$, $Y = V_2$
	- we define $\pi$ to be a permutation of the natural numbers $\{1, 2, \dots, \min{(n, m)}\}$ that assigns elements in $X$ to elements in $Y$
	- we then apply a base kernel on those substructures
		- $$
		  \kappa_A(g_1, g_2) = \begin{cases}
		  \max_\pi \sum_{i = 1}^n \kappa(x_i, y_{\pi_{(i)}}) & \text{if } m \geq n \\
		  \max_\pi \sum_{i = 1}^m \kappa(y_i, x_{\pi_{(i)}}) & \text{otherwise} \\
		  \end{cases}
		  $$
		- kernel value is taken for permutation that maximizes the sum
- complexity
	- optimal assignment of substructures is a linear sum assignment problem
		- can be solved in polynomial time
- properties
	- generally not positive definite (i.e., valid)