---
title: Mean Field Variational approach
tags: Note\笔记
key: MFVariational
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

An interesting variational principle, first promoted by Bogoliubov. Might be helpful in understanding the origin of Mean Field Theory.

<!--more-->

## generic MF Hamiltonian

$$
H_0 = -\sum \tau_{i,j} c^\dagger_i c_j + \sum (\Delta_{i,j}c^\dagger_ic^\dagger_j + H.C.)
$$

in the case $\tau, \Delta$ obeys translational invariance, the model could be easily solved.

The problem now is to represent the ground state (zero temperature) of a generic many body Hamiltonian by G.S. of $H_0$​, say $\Psi_0$

## Zero temperature case

for fermion case, let

$$
H = -\sum t_{ij} c^\dagger_i c_j + \sum V_{ijkl}c^\dagger_ic^\dagger_j c_kc_l
$$

variational principle:

$$
\newcommand{\expect}[1]{\langle #1 \rangle}
\newcommand{\greenF}[2]{c^\dagger_{#1} c_{#2}}
E = \bra{\Psi_0} H \ket{\Psi_0} \equiv \expect{H}_0 \geq E_{GS}
$$

minimizing E requires

$$
\frac{\partial E}{\partial \tau_{i, j}} = 0, \quad\frac{\partial E}{\partial \Delta_{i, j}} = 0,
$$

since the ground state is unchanged when shifting the parameters, additional constraint should be considered. Note that

$$
\begin{aligned}
\frac{\partial {\expect{H_0}_0}}{\partial \tau_{ij}} &= -\expect{c^\dagger_i c_j}_0 \quad (\text{Feynman-Hellman})\\
&= -\expect{c^\dagger_i c_j}_0 -\sum_{kl} \tau_{k,l} \frac{\expect{c^\dagger_k c_l}_0}{\partial \tau_{i,j}} - \sum \Delta_{k,l} \dots \quad (\text{Direct calculation}) \\

\Rightarrow 0& \equiv \sum_{kl} \tau_{k,l} \frac{\expect{c^\dagger_k c_l}_0}{\partial \tau_{i,j}} + \sum \Delta_{k,l} \dots
\end{aligned}
$$

Using Wick's contraction, $\expect{\dagger\dagger..} = \expect{\dagger\dagger}\expect{..} - \expect{}\expect{} + \expect{}\expect{}$ (?)

$$
\begin{aligned}
\frac{\partial {\expect{H}_0}}{\partial \tau_{ij}} &= -\sum_{k l}\left[t_{k l}+\sum_{p q}(V(p k l q)-V(p k q l))\left\langle c_{p}^{\dagger} c_{q}\right\rangle_{0}\right] \frac{\partial\left\langle c_{k}^{\dagger} c_{l}\right\rangle_{0}}{\partial \tau_{i j}} \\
&+\sum_{k l}\left[\left(\sum_{p q} V(k l p q)\left\langle c_{p} c_{q}\right\rangle_{0}\right) \frac{\partial\left\langle c_{k}^{\dagger} c_{l}^{\dagger}\right\rangle_{0}}{\partial \tau_{i j}}+H . C .\right]
\end{aligned}
$$

Comparing above two equations,

$$
\label{eq:1}
\begin{aligned}
\tau_{k,l} &= t_{k,l} + \sum_{p q}(V(p k l q)-V(p k q l))\left\langle c_{p}^{\dagger} c_{q}\right\rangle_{0} \\
\Delta_{k,l} &= \dots
\end{aligned}
$$

### e.g. Hubbard Model

$$
H = -\sum_{\expect{ij}, \sigma} t_{ij} \greenF{i\sigma}{j\sigma} + U \sum n_{i\uparrow} n_{i\downarrow}
$$


$$
H_0 = - \sum \tau_{\alpha, \beta} \greenF{\alpha}{\beta} + \sum(\Delta_{\alpha, \beta}
c^\dagger_\alpha c^\dagger_\beta + H.C.)
$$

hereafter, Greek letter indicates both the coordinate and the spin, $\kappa \equiv (k, \sigma)$​

$\Rightarrow$

$$
\begin{aligned}
\tau_{\kappa,\iota} &= t_{k,l} - U \delta_{\kappa, \iota} \expect{n_\bar{\kappa}}_0 + U \delta_{\kappa, \bar{\iota}} \expect{ c^\dagger_{\bar{\kappa}} c_\bar{\iota}}_0 \\
\end{aligned}
$$

where $\overline{(k, \uparrow)} = (k, \downarrow)$ , denotes the spin flip for simplicity.

Additional terms given by this result can be seen from ...

$$
\newcommand{\Tr}{\text{Tr}}
\begin{aligned}
H_{MF} = & -t \sum \greenF{k,\sigma}{l,\sigma} + U\sum \left(n_{k\uparrow} \expect{n_{k\downarrow}}_0 + \dots (\text{down spin part})\right) \\
&- \color{red}{U \cdot \sum\left(  \expect{\greenF{k\uparrow}{k\downarrow}} \greenF{k\downarrow}{k\uparrow} + \dots \right) -U \cdot \left( c^\dagger_{k\uparrow} c^\dagger_{k\downarrow} \expect{c_{k\uparrow} c_{k\downarrow}}_0 + \dots \right)}
\end{aligned}
$$

If one restricts himself, by using the symmetry of Hubbard Hamiltonian (total $\hat{N}$ and $\hat{S}_z$), to the case that the number of up/down spins are separately conserved, he may drop the $\color{red}{\text{red}}$ terms and restore the familiar result (Landau's symmetry breaking and order parameter approach, in this case, **order parameter** is taken as the density $\expect{n}$ 

$$
n_{i\uparrow} n_{i\downarrow} = n_{i\uparrow} \expect{n_{i\downarrow}}_0 + \expect{n_{i\uparrow}}_0 n_{i\downarrow} - \expect{n_{i\uparrow}}_0 \expect{n_{i\downarrow}}_0 + \color{blue}{(n_{i\uparrow} - \expect{n_{i\uparrow}}_0)(n_{i\downarrow} - \expect{n_{i\downarrow}}_0)}
$$

One then states that the mean field Hamiltonian is obtained by dropping the $\color{blue}{\text{blue}}$ second order correlation term.)



## Finite Temperature case

see [**Bogoliubov variational principle**](https://arxiv.org/abs/1507.00563)

$$
F(H) = -\frac{1}{\beta} \log \left(\Tr(e^{-\beta H})\right)
$$

$$
\expect{\hat{O}}_0 = \frac{\Tr( \hat{O} e^{-\beta H_0})}{\Tr( e^{-\beta H_0})}
$$

Bogoliubov principle:

$$
\label{eq:FH}
F(H) \leq F(H_0) + \expect{H-H_0}_0, \quad \forall H_0
$$

Feynman-Hellman:

$$
\frac{\partial F(H_0)}{\partial \tau_{i,j}} = - \expect{\greenF{i}{j}}_0
$$

remaining calculations (minimizing R.H.S of eq $\eqref{eq:FH}$​ are exactly the same as in Zero-T case, and resolves the ambiguity in eq.$\eqref{eq:1}$​​​
