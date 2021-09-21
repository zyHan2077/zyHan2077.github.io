---
title: Symmetry and classification of Topological Orders
tags: Note\笔记
key: PHSTRSCS
layout: article
license: true
toc: true
pageview: true
aside:
    toc: true
sitemap: true
mathjax: true
---

The terminology of symmetries is often invoked, especially in the field of topological classification (of non-interacting system), with conflicting meanings. Here I intend to summarize a self-consistent explanation to some well-known conclusion, e.g. particle-hole symmetry of Hubbard model, Chiral symmetry of SSH model ...

<!--more-->

main reference:

[Chiu, C.-K., Teo, J. C. Y., Schnyder, A. P., & Ryu, S. (2016). Classification of topological quantum matter with symmetries. *Reviews of Modern Physics*, *88*(3), 035005.](https://doi.org/10.1103/RevModPhys.88.035005)

## preliminaries

Any symmetry can be represented as an operator, which is either linear and unitary, or anti-linear and anti-unitary. **Wigner's theorem**



### Time-reversal symmetry

antilinear operator $A$ is a map in Hilbert space $\{x, x \in \mathcal{H}\}$, with following definitions:

$$
\newcommand{\expect}[1]{\langle #1 \rangle}
\begin{aligned}
\text{antilinear: } & A (\alpha x + \beta y)= \bar{\alpha} \cdot Ax + \bar{\beta} \cdot Ay \\
\text{adjoint operator: }  & \expect{Ax, y} = \overline{\expect{x, A^* y}} \\
\text{antiunitary: } & \expect{Ax, Ay} = \overline{\expect{x, y}} \Leftrightarrow A A^* = A^*A = I
\end{aligned}
$$

Time reversal is an antiunitary operator defined by:

$$
\newcommand{\ti}{\mathscr{T}}
\ti \psi_I \ti^{-1} = (U_T)_I^J \psi_J
\label{eq:defTR}
$$

for an antiunitary, $\ti^{-1}$ is equivalent with the adjoint operator $\ti^*$

As a symmetry, $\ti$ preserves the commutation relation and leaves $\hat{H}$ invariant:

$$
\begin{aligned}
& \ti \{\psi_I, \psi^\dagger_J\} \ti^{-1} = \{\psi_I, \psi^\dagger_J\}, \, \dots \\
& \ti \hat{H} \ti^{-1} = \hat{H}
\end{aligned}
$$

with observations:

1. $\ti^2, \ti \psi_I \ti^{-1}, \dots$ are all linear operators, $(\ti \psi_I \ti^{-1})^\dagger = \ti \psi_I^\dagger \ti^{-1}$
2. Matrix $U_T$ is unitary (can be deduced from the preserving of commutator)
3. under Heisenberg representation, for a system with TRS, $\ti \hat{O}(t) \ti^{-1} = \hat{O}(-t)$

**Kramer's degeneracy** comes when $\ti^2 = -1$, proof:

$$
\braket{\phi |  \ti \phi} = \overline{\expect{\ti\phi, \ti^2\phi}} = - \overline{\expect{\ti \phi, \phi}} = -\braket{\phi | \ti \phi} \Leftrightarrow \braket{\phi | \ti \phi} = 0
$$



indicating $\ti\ket{\phi}$ and $\ket{\phi}$ are two distinct, degenerate state.



**how this relates to topology :**

when $\hat{H} = \psi^\dagger H \psi$ is single-particle Hamiltonian inside a **symmetry class** (defined such that matrix $H$ runs over an irreducible representation space), it can be shown that:

- $(U_T^* U_T)^\dagger H (U_T^* U_T) = H$
- Schur's lemma gives  $U_T^*U_T = \pm I \Rightarrow \ti^2 \psi_I \ti^{-2} = \pm \psi_I$
- for any $N$-particle state, $\ti^2 = (\pm 1)^{\hat{N}}$



**a common scenario with** $\ti^2 = -1$ :

one common example is the spin-$\frac{1}{2}$ single particle case, where the Time reversal is chosen as (ordinary textbook notation)

$$
i K \sigma_y = K \pmatrix{0 & 1 \\ -1 & 0}
$$

which is a rather confusing notation. It may be understood by saying that this $\ti$  does not affect spatial coordinate, only reverse each individual on-site spin by setting 

$$
U_T = \pmatrix{0 & 1 \\ -1 & 0}
$$

in the definition of TR, i.e.

$$
\ti \psi_{\vec{r}, s} \ti^{-1} = (U_T)_{s s'} \psi{_{\vec{r}, s'}}
$$

It is the only choice available if one requires $\ti^{2} = -1$ in a 2-dimensional Hilbert space.

<!-- **equation $\eqref{eq:defTR}$ can also be satisifed for a linear, unitary operator $\ti$** -->


###  particle-hole symmetry

particle-hole, or charge conjugation is a unitary transformation given by

$$
\newcommand{\cg}{\mathscr{C}}
\begin{aligned}
& \cg \psi_I \cg^{-1} = (U_C^*)^J_I \psi_J^\dagger \\
& \cg \psi^\dagger_I \cg^{-1} =  \psi_J (U_C)^J_I \\
\end{aligned}
$$

with observations:

- $\hat{N} = \sum \psi^\dagger_I \psi_I$, $\cg \hat{N} \cg^{-1} = N - \hat{N}$, with $N$ the total number of sites
- it is natural to define total charge as $Q \equiv \hat{N} - N/2$, $\cg Q \cg^{-1} = -Q$

#### e.g. Hubbard model at half-filling

if a many body Hamiltonian, combining with the chemical potential term, is invariant under particle-hole transformation:

$$
\cg (\hat{H} - \mu \hat{N}) \cg^{-1} = (\hat{H} - \mu \hat{N})
$$

note that this can only be true for specific $\mu$'s.

expectation of particle number:

$$
\newcommand{\Tr}{\text{Tr}}
\begin{aligned}
\expect{\hat{N}} &= \frac{\Tr(\hat{N} e^{-\beta (\hat{H} - \mu \hat{N})})}{\Tr(e^{-\beta (\hat{H} - \mu \hat{N})})} \\
&= \frac{\Tr(\cg \hat{N} \cg^{-1} \cg e^{-\beta (\hat{H} - \mu \hat{N})} \cg^{-1})}{\Tr(e^{-\beta (\hat{H} - \mu \hat{N})})} \\
&= N - \expect{\hat{N}} \\
&\Rightarrow  \expect{\hat{N}} = N / 2
\end{aligned}
$$

i.e. at this certain chemical potential level, half of the total orbitals are "filled", regardless of temperature $\beta$. While the exact particle number expectation corresponding to generic $\mu$ may not be able to calculate.

**Explicitly write down the PH transformation of Hubbard model:**

$$
\newcommand{\greenF}[2]{c^\dagger_{#1} c_{#2}}
\hat{H} = \sum_{i,j; \sigma} t_{ij} \greenF{i \sigma}{j\sigma} + U \sum n_{i\uparrow} n_{i\downarrow}
$$

one may expect a simple form of $\cg$:

$$
\cg c_{i\sigma} \cg^{-1} \propto c^\dagger_{i\sigma} = \alpha_{i\sigma} c^\dagger_{i\sigma}
$$

where $\alpha$ has absolute value 1.

$$
\begin{align}
\cg \hat{H} \cg^{-1} &= \sum t_{ij} \alpha^*_{i\sigma} \alpha_{j\sigma} (-c^\dagger_{j\sigma} c_{i\sigma}) + U \sum (1 - n_{i\uparrow}) (1-n_{i\downarrow}) \nonumber \\
&= \hat{H} + \frac{N}{2}U - U \hat{N} \\

\cg (- \mu \hat{N} ) \cg ^{-1} &= -\mu N + \mu \hat{N}
\end{align}
$$

PH is then satisfied when $\mu = U/2$, plus one additional constraint that

$$
t_{ji} = t^*_{ij} = - t_{ij} \alpha^*_{i\sigma} \alpha_{j\sigma}, \quad \forall \; \text{neighboring} \; ij
$$

under the special case of real $t$, bipartite lattice, $\alpha$ can be chosen as $\pm 1$ on each sub lattice to meet the requirements.

### Chiral symmetry

<!--Chiral symmetry is an antilinear operator which transform particles into holes.-->

CS often refers to the case when both TRS and PHS are broken, while their combination is satisfied.

$$
\newcommand{\cl}{\mathscr{I}}
\begin{aligned}
& \cl = \ti \cdot \cg \\
\end{aligned}
$$

A well-known example for chiral symmetry is the SSH model (on a bipartite lattice, orbits in each unit cell are labeled by $a, b$)

$$
\hat{H} = \sum (t a^\dagger_jb_j + t' b^\dagger_j a_{j+1} + H.C.)
$$

![img](https://phyx.readthedocs.io/en/latest/_images/2.jpg)

using the translational symmetry:

$$
\hat{H} = \sum_k \pmatrix{a^\dagger_k & b^\dagger_k} \pmatrix{0 & t + t'^* e^{ik}\\ t^* + t' e^{-ik} & 0} \pmatrix{a_k \\ b_k}
\label{eq:diagink}
$$

the property $h_k = \vec{h} \cdot \vec{\sigma}$, while $h_z = 0$ is often claimed to be Chiral symmetry.

Here for spinless fermion, TR:

$$
\ti \psi_I \ti^{-1} = \psi_I
$$

PH transformation is exactly the same as stated in above section:

$$
\begin{aligned}
\cg a_j \cg^{-1} &= + a^\dagger_j \\
\cg b_j \cg^{-1} &= - b^\dagger_j \\
\end{aligned}
$$

**In the general case of complex $t, t'$**, TRS and PHS are all broken, but their combination is satisfied.

Chiral symmetry then forbids the exists of terms like $\sum_{k} u(k) a^\dagger_k a_k$.



A more general argument may be given, for non-interacting system

$$
\cl \psi_I \cl^{-1} = (U^*_S)_I^J \psi^\dagger_J \Rightarrow U_S^\dagger H U_S = - H
$$

(without loss of generality, assuming $\Tr(H) = 0$ by adjusting the zero of energy)

Chiral symmetry then gives rise to a symmetric spectrum:

$$
H \ket{\phi} = E \ket{\phi} \Rightarrow H (U_S \ket{\phi}) = - E (U_S \ket{\phi})
$$

In a basis where $U_S$ is diagonal, i.e., let $U^2_S = 1$ from the schur's lemma:

$$
\text{basis} = \{\ket{\phi} \pm U_S \ket{\phi}\}
$$

corresponding to $\pm 1$ sector of operator $U_S$, Hamiltonian is thus block-off-diagonal

$$
H = \pmatrix{0 & D \\ D^\dagger & 0}
$$

to be continued ...