---
title: triangulations & persistent homology
tags: Note\笔记
key: Barcode_Triangulations
layout: article
license: true
toc: true
pageview: true
aside:
    toc: true
sitemap: true
mathjax: true
mathjax_autoNumber: true
---

基本群可以用来区分一些拓扑空间，例如球面和环面，甚至可以证明基本群可以用来区分比较general case下的二维曲面，但有着更多的情况基本群无法做出区分。这里说明对于一大类拓扑空间 (i.e. triangulable space), Simplicial Homology Group可以作为一个更精细的拓扑不变量，其优点还有易于编程写成算法等。

<!--more-->

# Simplicial Homology


## triangulable space

首先限制研究的拓扑空间可以三角剖分，即，该空间同胚于某Euclidean space $E^n$ 中的单纯复形 (simplicial complex)，具体来说

- k-simplex 定义为某$E^n$中包含$k+1$个顶点$v_0, ... v_k \in E^n$的最小凸集（即集合
  
  $$
  \newcommand{\abs}[1]{| #1 |}
  \newcommand{\d}{\text{d}}
  \{x | x=\lambda_0 v_0 + \cdots + \lambda_k v_k,   \sum \lambda_i \equiv 1, \lambda_i \ge 0\}
  $$

  ，当然要求它们真的张出一个$k$维空间）

  ![ksimplex](/assets/images/ksimplex.svg)

- simplex的并集就是complex了，如果complex满足下面几条则称为simplicial complex

  - 有限个simplex
  - 如果有某个simplex $A$，则也包含这个$A$ 的所有surface (surface 也可以 intuitively 定义为$A$的顶点的子集张成的simplex )
  - 两个simplex交集只能为两者共同的surface

- 从$E^n$的拓扑诱导出complex $K$上拓扑空间，记为$\|K\|$

- $X$的triangulation即为某个$\abs{K}$到$X$的同胚

## fundamental group of simplicial complex

可以证明，complex $K$经过某顶点$v$的所有路径（要求是loop）的等价类构成edge group $E(K, v)$，该群同构于拓扑基本群$\pi_1(\abs{K}, v)$，其中：

- complex $K$中路径定义为一个序列$v_0 v_1 \cdots v_k$，其中$v_i, v_{i+1}$张出一个$K$中1-simplex

- 路径间的等价定义为下图

  ![equivalent](/assets/images/equivalent.png)

- loop的群乘法仍然类似基本群定义：

  $$\{v v_1 \cdots v_{k-1} v\} \cdot \{v w_1 \cdots w_{k-1} v\} = \{v v_1 \cdots v_{k-1} v w_1 \cdots w_{k-1} v\}$$

上述edge group 定义中不涉及任何高于2维的simplex，所以可称$K$的所有2维及以下的simplex构成的subcomplex为$K$的2-skeleton，$K$的基本群同构于其2-skeleton的基本群，即基本群不可能包含高于2维的信息，同时基本群也适合于研究2维的问题。

由2-skeleton可以证明球面$S^n, n \ge 2$的基本群是平凡的：

- $S^n$同胚于$(n+1)$-simplex的边界
- $n\ge2$时，$(n+1)$-simplex的2-skeleton 同胚于它的边界的2-skeleton

故$S^n$基本群同构于$(n+1)$-simplex 的基本群，即是平凡群。

## simplicial homology

下面先定义Chain Group，让我们可以在bulk和surface之间建立联系；之后，通过一个例子说明这个代数如何帮助我们区分两个不同的拓扑空间，并自然地对基本群进行推广。

- 将一个q-simplex按照顶点标记为：

	$$(v_0, v_1, \cdots, v_q)$$

- 每个q-simplex有正负两种**定向**，且定义
  
	$$ (v_0, v_1, \cdots, v_q)  = (-1)^{\theta} (v_{\theta(0)}, \cdots, v_{\theta(q)})$$

- 某个complex $K$的chain group $C_q(K)$定义为形如：
  
	$$\lambda_1 \sigma_1 + \lambda_2 \sigma_2 + \cdots + \lambda_s \sigma_s$$

	的元素集合，其中$\lambda$均为整数，$\sigma$为$K$中包含的$s$个q-simplex （有任意的定向）. 群上的加法定义为对应项系数相加. 这样定义的chain group为一个阿贝尔群.
- q-simplex的边界由如下映射$\partial$得到：
  
	$$\partial (v_0, v_1, \cdots, v_q) \equiv \sum_{i=0}^q (-1)^{i} (v_0, \cdots v_{i-1}, v_{i+1}, \cdots v_q)$$

- $\partial$映射视为线性算符，则成为$C_{q+1}(K) \to C_q(K)$的映射，方便起见令0-simplex，即单个点的边界为0

上面的定义自然保证了，对一个形如

$$z = (v_0, v_1) + (v_1, v_2) + \cdots + (v_n, v_0)$$

的loop，因为首尾相连，故$\partial z = 0$

且对任意元素，容易证明$\partial^2 \equiv \partial \circ \partial = 0$

（微分流形中一个积分可以定义为一个r维“区域”和一个微分 r-形式的配合$(D, \omega)$, Stokes' theorem说$(D, \d \omega) = (\partial D, \omega)$，这个结论形式上和Poincare Lemma $\d^2 \omega = 0$是相容的，*更深刻的内容我还没有看qwq*）

### motivation & homology

<img src="/assets/images/1280px-A_triangulation_of_the_torus,_with_bounding_box_fixed.svg.png" alt="1280px-A_triangulation_of_the_torus,_with_bounding_box_fixed.svg" style="zoom: 30%;" />

考察一个torus，其表面上的loop $z$有两种，一种是某个曲面$\omega$的边界（上图红色），即$\partial \omega = z$，可以称之为一个trivial的loop；另一种不是，表明这个loop“绕着曲面上某个洞”（蓝色）。我们尝试把两个差是trivial的loop置于同一个等价类中，预计可以回到基本群：

定义：
- $C_{q+1}(K)$在$\partial$作用下的像为$B_q(K)$，包含了所有”bounding q-cycle”
- $C_q(K)$中所有被$\partial$映射到0的群元构成$Z_q(K)$，由于$\partial^2 = 0$，$B_q$是$Z_q$的子群
- q阶同调群定义为
	$$H_q(K) = Z_q(K) / B_q(K)$$

我们期待$H_1(K)$是$\abs{K}$的基本群，其余$q$的同调群也应当可以用来反映拓扑空间的某些差别。

如上定义的同调群中的某个元素$[z] = z + B_q(K)$（即代表元$z \in Z_q(K)$的等价类），要么满足$[z] + [z] + \cdots$任意多次不会回到自身，要么在几次加自身后得到0（数学上将Abelian group所有有限阶的群元组成的子群称为torsion group $T$）。则

$$ H_q(K) \cong \mathbb{Z} \oplus \mathbb{Z} \cdots \mathbb{Z} \oplus T $$

上式中$\mathbb{Z}$的个数定义为第$q$个Betti number $\beta_q$

### examples

（待续）

- $\beta_0$为拓扑空间连通分量个数
- 基本群进行abelianization后得到$H_1(K)$
- 利用2阶同调群区分Klein Bottle 与 torus

## applications

### in data analysis

这样一个听起来非常适合于编程的方法必然有着一大堆数据分析上的应用，例如computational neuroscience研究神经网络拓扑结构，时间序列数据的分析（待续），以及和非常成熟的软件包可以调用

### 分析 Ising model 相变

物理上应用还算是刚起步，例如想用它分析Ising model量子相变，目前有这样的操作，（引自[Persistent homology of quantum entanglement
](https://arxiv.org/abs/2110.10214)）

- 首先在Ising模型格点之间建立某个和量子态有关的度量，然后根据这个度量构建一个拓扑空间
  - 利用不等式
  
    $$0 \leq M_{ij} = S_i+ S_j - S_{ij} \leq 2 \ln 2$$

    其中$S_i$代表将除$i$外其它所有格点自旋自由度trace掉后剩下密度矩阵对应的熵，一个简单观察是如果两个格点自旋形成singlet，且与其它自旋完全不纠缠，则$M_{ij}$取最大值；两个格点为直积态则取最小值

  - 定义$D_{ij} = 2 \ln 2 - M_{ij}$， $D$将满足三角不等式，且直观上$D$作为度量可以让纠缠越强的两个自旋距离越小；任何两个自旋间$D$距离有上限；
  - 有了度量后就总可以建起一个simplicial complex来，例如，确定一个阈值$\epsilon$，如果$k$个点间两两距离小于这个阈值，则令他们构成一个$k$ - simplex

- 计算各阶Betti数，分析这个拓扑空间的结构，data analysis中常用barcode，图示如下：
  ![barcode](/assets/images/barcode_TFIsing.png)

  其中横轴$\epsilon$的意义如前所述，这里对格点数不大、周期性边界条件的横场Ising模型基态，在每个固定$\epsilon$处计算了前两个Betti number，红线数量等于$\beta_0$，蓝线为$\beta_1$。
  
  - 量子相变点之前，任意两点间纠缠强度差不多，在$\epsilon$提高到某个阈值后，所有点连进一个连通分量，且拓扑平庸，并没有loop出现，$\beta_1 = 0$
  - 相变点之后，强场的情况下几乎都是直积态，互相不连通。
  - 相变点附近，各点连通后可能出现loop，表现为一根蓝色bar。看起来蓝线长度随$h$的变化……似乎也许可以用来反映相变点( (d)图)……但显然这个工作还比较初步

