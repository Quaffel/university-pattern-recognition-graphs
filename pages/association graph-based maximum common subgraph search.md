- finding maximum common subgraph is equivalent to finding maximum clique in [[association graph]]
	- vertex in association graph $(u_1, u_2)$ can be interpreted as mapping $f(u_1) = u_2$
	- if two vertices are connected in association graph, both mappings satisfy the edge structure and label constraints
	- clique in association graph represents isomorphism from subgraph $g_1' \subseteq g_1$ to another subgraph $g_2' \subseteq g_2$
		- clique corresponds to maximum common subgraph of $g_1$ and $g_2$
		- LATER subgraph is not necessarily connected, right?
		  :LOGBOOK:
		  CLOCK: [2025-04-02 Wed 10:57:59]--[2025-04-02 Wed 10:58:17] =>  00:00:18
		  :END:
- maximum clique can be found using [[bron-kerbosch algorithm for maximum clique]]