---
title: Note | Clique seperator
date: 2023-06-01 23:54:22
mathjax: true
tags:
- Sparse-Matrix
- Graph-Theory
- Minimum-Degree
- Clique-Decomposition
categories:
- Reading-Note
- Notes
ShowToc: true

---

# Clique seperator

## Decomposition by clique seperator ([Tarjan, 1985](https://scholar.google.com/citations?user=lazJixIAAAAJ&hl=zh-CN&oi=sra))
### Main Idea: 

Based on the idea of 'divide and conquer', this paper proposed an graph decomposition algorithm by finding the clique seperator recursively. The decomposition results in a binary decomposition tree. The author suggested some general ideas to tackle 4 NP-hard problems by ultlizing the binary decomposition tree.

### Preliminaries

*Perfect elimination ordering*, *Clique*, *Minimal and Minimum ordering*, *Seperator*

### Algorithms

<img src="https://p.ipic.vip/c3fqaa.png" alt="Decompistion by clique separator" style="zoom:40%;" />

[Text description](https://scholar.google.com/citations?user=lazJixIAAAAJ&hl=zh-CN&oi=sra)

### Corollary: 

### If we can find the perfect ordering on atoms,

### then we can find the perfect ordering on the entire graph

Proof: 

Let Atoms be $G_i=(V_i, E_i)\ \forall i=1,\cdots,k$. 

We first compute the fill-in $F_i$ on $G_i$ produced by $\sigma_i$. Since $G_i'=(V_i, E_i\cup F_i)$ is chordal, so is $G'=(V, E\cup \cup_{i=1}^kF_i)$.

Next, We compute the perfect ordering $\sigma$ on $G'$, the resulted fill-in is the subset of $\cup_{i=1}^kF_i$. Thus, $\sigma$ is minimum if $\sigma_i$ is minimum for all $i$



### Algorithms to generate graph with the perfect ordering

<img src="https://p.ipic.vip/zat33a.png" alt="Algorithms to generate graph with the perfect ordering" style="zoom:50%;" />















