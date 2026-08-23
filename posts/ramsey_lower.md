# Lower bounds of Ramsey numbers

## A probabilistic method

**Definition.** Let $k,l\in\mathbb{N}$. Then $R(k,l)$ is the smallest $n\in\mathbb{N}$ for which the following holds (if no such $n$ exists, $R(k,l)=\infty$):
whenever $E(K_n)$, the edge set of a complete graph on $n$ vertices, is coloured red and blue, there is a $K_k$ subgraph coloured red or a $K_l$ subgraph coloured blue.

Colour every edge of $K_n$ red with probability $p$, else blue, independently. 
For any of the $\binom nk$ possible choices of $k$ vertices,
the probability that every edge they induce is red equals $p^{\binom k2}$.
Since the event that a red $K_k$ occurs is the union of the events that some $k$ vertices form a red $K_k$,
its probability is at most 

$$\binom nk p^{\binom k2}\le \frac{n^k}{(k/e)^k}p^{\frac{k(k-1)}{2}}=\left(enk^{-1}p^{\frac{k-1}{2}}\right)^k.$$

For the same reason, the probability that a blue $K_l$ occurs is at most $\left(enl^{-1}(1-p)^{\frac{l-1}{2}}\right)^l$.

If both of these probabilities are less than $\frac12$, there is no red $K_k$ and no blue $K_l$ with positive probability, so $n<R(k,l)$.
The conditions for $n$ are $n<2^{-1/k}e^{-1} kp^{-\frac{k-1}{2}}$ and $n<2^{-1/l}e^{-1} l(1-p)^{-\frac{l-1}{2}}$,
so $p_c$, a near-optimal value of $p$, satisfies 

$$p_c^{k}=(1-p_c)^{l}.$$

We deduce that 

$$R(k,l)\ge 0.1  \min\left( k\sqrt {p_c},l\sqrt{1-p_c} \right)\cdot (p_c^{-1/2})^k,$$

which, up to a constant factor, is the best known lower bound when $k=l$ and $p_c=\frac12$.

## A recent improvement

In 2025, [Jie Ma, Wujie Shen, and Shengjie Xie](https://arxiv.org/abs/2507.12926) improved this bound exponentially: 

$$R(k,\alpha k)=\Omega((p_c^{-1/2}+\varepsilon)^k),$$

for the "off-diagonal" case, where $\varepsilon>0$, $p_c$ only depends on $\alpha=\frac lk$, and $k\to \infty$. 
They considered a random geometric graph, consisting of $n$ independent uniformly random points on the $d$-dimensional sphere $S^{d}\subseteq \mathbb{R}^{d+1}$.
An edge between two points is coloured red or blue depending on whether the angle subtended by the corresponding unit vectors is larger than a certain value.
Estimating the probability of a red $K_k$ or a blue $K_l$ is technically challenging, and this may be the reason why the bound on $R(k,\alpha k)$ was not obtained previously.

## An excursion into finite geometry

A year later, [Domagoj Bradač](https://arxiv.org/abs/2605.28793) proved a different lower bound on Ramsey numbers 
by considering the $d$-dimensional sphere in the finite geometry over a field $\mathbb{F}$ with $q$ elements (which exists if and only if $q$ is a prime power).
The analogue of a sphere is the set of nonzero vectors in $\mathbb{F}^{d+1}$, where two vectors are seen as identical if they differ by a nonzero scalar.

A key feature of these vectors is that if $\mathbf{x}(1),\ldots,\mathbf{x}(d+2)$ and $\mathbf{z}(1),\ldots,\mathbf{z}(d+2)$ are such vectors,
it is impossible that 
* $\langle \mathbf{x}(i),\mathbf{z}(j)\rangle = 0$ for all $i<j$
* but $\langle \mathbf{x}(i),\mathbf{z}(i)\rangle \neq 0$ for all $i$.

Why? From this condition, it would clearly follow that $\mathbf{z}(1),\ldots,\mathbf{z}(d+2)$ are linearly independent, a contradiction!

Next, consider the *directed graph* $D$ where:
* vertices are pairs $(\mathbf{x},\mathbf{z})$ with $\langle \mathbf{x},\mathbf{z}\rangle \neq 0$, 
* directed edges $(\mathbf{x},\mathbf{z})\to (\mathbf{x}',\mathbf{z}')$ are those for which $\langle \mathbf{x},\mathbf{z}'\rangle =0$.

In this context, our previous observation is equivalent to there being no transitive tournament of size $d+2$ in $D$.

*Note.* Using energy-intensive computational technology, 
an OpenAI team found that if the directed edges of $D$ are defined with a further constraint of $\langle \mathbf{x}',\mathbf{z}\rangle \neq 0$,
then there is no transitive tournament of size $d+1$ in $D$. Using this version of $D$, they found the optimal base in the lower bound.

## A detour into spectral graph theory

There are $n=\frac{q^{d+1}-1}{q-1}$ points on the $d$-dimensional sphere over $\mathbb{F}$.

If we draw a graph connecting two (not necessarily different) points, $\mathbf{x}$ and $\mathbf{y}$, if $\langle \mathbf{x},\mathbf{y}\rangle =0$, 
then 
* every point is adjacent with $\Delta=\frac{q^d-1}{q-1}$ points 
(if $\mathbf{u}\neq 0$, then there are equally many $\mathbf{v}\in \mathbb{F}^{d+1}$ with $\langle \mathbf{u},\mathbf{v}\rangle =a$ for all $a\in \mathbb{F}$),
* every two distinct points are both adjacent with $\frac{q^{d-1}-1}{q-1}$ points (by a similar bijective argument).

Let $A$ be the adjacency matrix of this graph, $J$ be the matrix of ones, and $I$ be the identity matrix.
Then the square of $A$ satisfies

$$A^2=\frac{q^{d-1}-1}{q-1}J+q^{d-1}I.$$

One eigenvector of $A$ is the vector of ones, with eigenvalue $\Delta$. 
Any other eigenvector is perpendicular to the vector of ones, and so its eigenvalue $\lambda$ satisfies $\lambda^2=q^{d-1}<\Delta$.

Since $A'=A-\Delta n^{-1} J$ has eigenvalues $0$ and $\pm q^{\frac{d-1}{2}}$,
multiplying by it increases the norm of a vector by at most a factor of $q^{\frac{d-1}{2}}\le \sqrt{\Delta}$.

Let $U$ and $V$ be sets of points. Then $1_U^TA1_V$ is the number of edges from $U$ to $V$ with multiplicity. By Cauchy-Schwarz,

$$\left|1_U^T\left(A-\Delta n^{-1} J\right)1_V\right|\le |1_U|_2\cdot |A'1_V|_2\le \sqrt{\Delta|U||V|}.$$

Hence, the proportion of edges appearing between $U$ and $V$ is approximately $\frac{\Delta}{n}$.

## Counting forward independent $t$-tuples in $D$

Returning to the directed graph $D$, let $(\mathbf{x}_1,\mathbf{z}_1),\ldots,(\mathbf{x}_t,\mathbf{z}_t)$ be vertices of $D$
for which there is no directed edge from an earlier vertex to a later vertex.
Call index $i$ special if $\mathbf{x}_i$ is orthogonal to at most $\frac{\Delta}{2n}$ proportion 
of the points not orthogonal to $\mathbf{x}_j$ ($j=1,\ldots,i-1$).

It is for a non-special index that the number of these non-orthogonal points decreases by a factor of $<\left(1-\frac{\Delta}{2n}\right)$. 
Thus, if there are $s$ indices that are non-special, then by the last non-special index, at most $n\left(1-\Delta/(2n)\right)^{s-1}$ points are non-orthogonal.
However, by definition of $D$, $\mathbf{z}_i$ is not orthogonal to $\mathbf{x}_j$ for all $j<i$, so this amount is at least one.
By convexity $1+x\le e^x$, yielding $ne^{-(s-1)\Delta/(2n)}\ge 1$, so that

$$s-1\le \frac{2n\log n}{\Delta}.$$

Let $U$ be the set of non-orthogonal points and $V$ be the set of points orthogonal to at most $\frac{\Delta}{2n}$ proportion of them.
Since the number of edges from $U$ to $V$ is at least $\Delta n^{-1} |U||V|-\sqrt{\Delta |U||V|}$, yet less than $\frac{\Delta}{2n}|U||V|$,
we deduce $\frac{4n^2}{\Delta}\ge |U||V|$. The number of edges from $U$ to $V$ is at most $\Delta n^{-1}|U||V|+\sqrt{\Delta |U||V|}\le 4n+2n=6n$.

Now suppose we are told in advance which indices are special.
For non-special indices $i$, there are at most $\Delta n$ possible $(\mathbf{x}_i,\mathbf{z}_i)$ for any preceding vertices of $D$.
For special indices $i$, however, there are at most $6n$ possible $(\mathbf{x}_i,\mathbf{z}_i)$, given the preceding vertices,
because $\mathbf{z}_i$ is not orthogonal to $\mathbf{x}_j$ ($j=1,\ldots,i-1$) and $\mathbf{x}_i$ must be orthogonal to $\mathbf{z}_i$.
Therefore, the number of such $t$-tuples is at most $6^{t-s}\Delta^s n^t\le (\Delta/6)^{2n\log n/\Delta+1} (6n)^t$.
Since there are at most $2^t$ ways for the $t$ indices to be special or not, 
the number of "forwards independent $t$-tuples" is at most

$$(\Delta/6)^{2n\log n/\Delta+1} (12n)^t.$$

## The resulting lower bound

In a uniformly random permutation of $D$'s vertices, join two vertices if their edge is from earlier to later vertex.
There will be no $K_{d+2}$, and the chance there will be an independent $K_t$ is at most $\frac{(\Delta/6)^{2n\log n/\Delta+1} (12n)^t}{t!}\le (\Delta/6)^{2n\log n/\Delta+1}(12en/t)^t$.

Retaining a vertex with probability $p$ and then deleting a vertex from every independent $K_t$, an expected number of

$$\ge p\cdot (\Delta n)-(\Delta/6)^{2n\log n/\Delta+1}(12epn/t)^t$$

vertices remain with no $K_{d+2}$ or independent $K_t$. We specify $p$ so as to make the latter term $1$, guaranteeing 

$$R(d+2,t)\ge p\Delta n=\frac{t\Delta}{12e(\Delta/6)^{(2n\log n/\Delta+1)/t}}.$$

For $q\ge 8$, one can check that $2n\log n/\Delta+1\le 2(d+1)q\log q$. 
Upon writing $q^{d-1}$ in the place of $\Delta$ and $\Delta/6$, the optimal value of $q$ as a real parameter satisfies $q(\log q)^2+2q\log q=\frac{t}{2(d+1)}$.
Thus, let $k=d+2$, $\alpha k=t$ (where $\alpha\ge 35$), so that $q$ can be a power of $2$ such that $\frac14\alpha\le q(\log q)^2 \le \alpha$:

$$R(k,\alpha k)\ge \frac{\alpha k q^{d-1}}{12e(q^{d-1}/4)^{2\frac{d+1}{t}q\log q}}\ge q^{(d-1)(1-2\alpha^{-1}q\log q)}\ge (e^{\log q-2})^{k-3}$$

where $q\ge \frac{\alpha}{4(\log \alpha)^2}$. Thus, we improved the probabilistic lower bound of roughly $(\sqrt \alpha)^k$ to roughly $\alpha^k$.



