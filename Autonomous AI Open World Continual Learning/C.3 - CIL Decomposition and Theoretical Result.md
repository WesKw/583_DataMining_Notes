- **Class Incremental Learning** can be decomposed into 2 subproblems *within-task prediction (WP)* and *task-id prediction (TP)*$$\begin{align}
P(x \in X_{k_0j_0}|D)\\ = \sum_{k=1,...,n}{P(x \in X_{k,j_0}|x \ in X_k,D)P(x \in X_k|D)}
\\
=
P(x \in X_{k_0j_0}|x \in X_{k_0},D)P(x \in X_{k_0}|D) \end{align}
$$
- $P(x \in X_{k_0j_0}|x \in X_{k_0},D) \rightarrow$ *WP* / TIL
- $P(x \in X_{k_0}|D) \rightarrow$ *TP*
- Theoretical result: Good *WP* and *TP* (or out-of-distribution (*OOD*)) are necessary and sufficient for a good **CIL**
- Only possible solution for CIL is closed world - each task is good at OOD detection within the $T$ tasks
- Theory can be extended to open world (CIL+) with unknowns
	- Each task is good at OOD detection
- Theory-based methods outperform baselines by large margins