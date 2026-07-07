---
layout: default
title: Embedding Lemma
---

*Lemma.* Let $H$ be an $r$-partite graph with vertex classes $V_1,\ldots,V_r$ of size $an$. Suppose that if $U,U'$ include $\ge \alpha an$ vertices from two different vertex classes, then $\ge \varepsilon$ of the edges between $U$ and $U'$ occur in $E(H)$. 

Provided $G$ is an $n$-vertex graph with $\varepsilon^l-(\Delta-l)\alpha\ge \frac1a$ for all $0\le l\le \Delta=\Delta(G)$ and $\chi(G)=r$, there is a subgraph of $H$ isomorphic to $G$.

*Proof.* Let $c:V(G)\to\{1,\ldots,r\}$ be an $r$-colouring of $G$. Let $v_1,\ldots,v_m$ be the vertices of $G$ in some order.

Suppose $f:\{v_1,\ldots,v_{i-1}\}\to V(G)$ is a partial embedding of $G$ into $H$ with $f(v_j)\in V_{c(v_j)}$ for $1\le j<i$. Is there a vertex $f(v_i)$ in $V_{c(v_i)}$ joined to $f(v_j)$ by an edge in $H$ whenever $\{v_i,v_j\}\in E(G)$?

Thinking ahead, we can guarantee that for all $k>i$, the set of possible $f(v_k)$ includes at least $\varepsilon^l an$ vertices, where $v_k$ neighbours $l$ of $v_1,\ldots,v_i$.

Indeed, if $\{v_i,v_k\}\in E(G)$, then among $\ge \varepsilon^{l-1} an$ vertices in $V_{c(v_k)}$ neighbouring $f(v_j)$ for all $j<i$ with $\{v_j,v_k\}\in E(G)$, fewer than $\alpha an$ vertices in $V_{c(v_i)}$ neighbour less than $\varepsilon$ as many of them ($\varepsilon^{l-1}\ge \alpha$).

This excludes $<(d_i-l_i)\alpha an$ of the $\ge \varepsilon^{l_i}an$ possible $f(v_i)$, where $v_i$ has $l_i$ neighbours among $v_1,\ldots,v_{i-1}$ and $d_i$ neighbours in total. 

Since $v_i$ must differ from $v_1,\ldots,v_{i-1}$, we can successfully specify $f(v_i)$ if $(\varepsilon^{l_i}-(d_i-l_i)\alpha)an\ge n$ holds. $\square$
