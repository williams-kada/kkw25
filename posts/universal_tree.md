At BCC 30, Zach Hunter [asked](https://arxiv.org/abs/2409.07216) the following question.
We say that a tree $T$ is an $n$-supertree if every $n$-vertex tree $T′$ can be obtained from $T$ by edge contractions (so that $T′$ is a minor of $T$). 
Let $F(n)$ be the smallest number of vertices of an $n$-supertree. It is known that $cn \log n \le F(n) \le n^2$. Is it true that $F(n)\le n^{1+o(1)}$?

This is precisely the question that had already been asked by [Olivier Bodini in 2002](https://arxiv.org/abs/0911.2807).
In fact, a quick AI search found that it was answered by [Paweł Gawrychowski, Fabian Kuhn, Jakub Łopuszański, Konstantinos Panagiotou, and Pascal Su in 2018](https://epubs.siam.org/doi/10.1137/1.9781611975031.166).
This much is not evident from the abstract of the paper. Hence, we reproduce the proof here. We show the answer is no.

**Observation 1.** Let $H$ be a contraction of the tree $U$ with maximum degree at most $3$. Then $H$ is a subdivision of $U$.

*Proof* The contracted edges of $U$ form connected components, corresponding to vertices of $H$, that are joined by at least an edge if they are adjacent in $H$.
If $H$ has maximum degree $3$, there are at most three edge endpoints in each such component.
Hence, it is easy to see that in every component, a vertex of $U$ can be selected with edge-disjoint paths to each endpoint in the component.
Now these paths and the joining edges form a subdivision of $H$ in $U$. $\square$

By designating a vertex of a tree as the root, its edges can given a direction, away from the root. 
We say that a rooted tree is a downward subtree of another rooted tree if the directions of their edges agree.

**Observation 2.** Suppose $B$ is a rooted binary tree with $k$ leaves and $BB$ is the tree formed by two disjoint copies of $B$ and an edge between the roots.
If the rooted tree $U$ contains a subdivision of $BB$, it has a downward subtree that is a subdivision (dss) of $B$.

*Proof sketch.* Consider the path from the root of $U$ to the root of either tree. 
It cannot be the case that both paths have an edge in common with the respective subdivision of $B$. $\square$

**Lemma 3.** If a rooted tree $U$ contains a subdivision of every $k$-leaf rooted binary tree as a downward subtree, then it has at least $b(k)$ leaves, where $b(1)=1$ and

$$b(k)=1+\sum_{j=2}^k b(\lfloor k/j\rfloor).$$

*Proof.* Let $C_i$ be the caterpillar tree: $C_0$ is a vertex, $C_1$ is an edge, $C_{i+1}$ is a root joined with a vertex and with the root of $C_i$.

For each vertex $v$ of $U$, let $f(v)$ be the maximal $i$ for which the subtree rooted at $v$ has a dss of $C_i$. 
This can be computed by recursion on the least distance from a leaf of $U$.

Let $U_{\ge j}$ consist of the vertices $v$ of $U$ with $f(v)\ge j$. Then $U_{\ge j}$ contains every rooted binary tree with $\lfloor k/j\rfloor$ leaves.
Indeed, by appending $C_j$ to every leaf of the binary tree, we obtain a rooted binary tree with $\le k$ leaves.

Thus, $U_{\ge j}$ has at least $b(\lfloor k/j\rfloor)$ leaves, each of which have $f$-value precisely $j$ ($2\le j\le k$). 
Since the $f$-value of their descendants is smaller, there are multiple branches at each such leaf.
Therefore, starting from the root of $U$, there are at least $\sum b(\lfloor k/j\rfloor)$ many branches. The result follows. $\square$

Let $\alpha$ be maximal such that $k^\alpha\ge \sum_{j=2}^k (k/j)^\alpha$ for all $k$, or [equivalently](https://mathworld.wolfram.com/RiemannZetaFunction.html), $2=\zeta(-\alpha)$.
Then $\alpha>1.7286=\beta$, and it is a standard exercise to show that $b(k)=\Omega(k^\beta)$.
