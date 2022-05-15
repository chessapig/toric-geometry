---
{"dg-publish":true,"permalink":"/toric-geometry/duistermaat-heckman-theorem/","dgHomeLink":true,"dgPassFrontmatter":false}
---
p

#theorem 


Let $(\calP,\omega)$ be a 2m-dimensional symplectic manifold, with $U(1)^n$ action defined by [[Toric geometry/Moment map|Moment map]]$\mu:\calP \to \mathfrak{t}^*\equiv {\mathfrak{u}(1)^{n}}^*$.  [[Toric geometry/Symplectic reduction|Symplectic reduction]] yields a family of symplectic manifolds parametrized by the level of the moment map $t\in \mathfrak{t}^*$:

$$(\calP_{t},\omega_{t} ) = \mu\inv(t)/U(1)^n$$


>[!theorem] Theorem: Duistermaat-Heckman, version 1
>The cohomology class  $[\omega_t]$ depends piecewise linearly on $t$. More precisely, for $t$ in a neighborhood of a regular value $t_0$, The manifolds $\calP_{t}$ and $\calP_{t_0}$ are diffeomorphic, and there is a fixed element $c\in H_2(\calP_{t_0},\mathfrak{t})$ such that
>$$[\omega_{t}] = [\omega_0] + \langle t-t_{0},c\rangle $$
^thm--DH-v1

>[!proof]+ 
>Follows from normal form of $U(1)^n$ actions. Since $t_0$ is regular, $\mu\inv(t_0)$ is a $U(1)^{n}$ principal bundle $P \to \calP$. For a neighborhood of regular values $U$, $\mu\inv(U)$ is a subset of $P \times \mathfrak{t}^*$. This carries a natural symplectic form 
>$$\omega' =  \pi^{*}\omega_{0}+\langle t,F_t \rangle$$
>where $F$ is the curvature of $P$ as a $\mathfrak{t}$-valued 2-form. This implies
>$$\frac{\de}{\mathrm{d} t}\omega_t =  F_t $$
>The cohomology of $F$ is constant, constrained topologically to equal the first Chern class $c$.  So, the derivative of $\omega_t$ is constant, meaning $\omega_t$ is linear in $t$.



>[!theorem]+ Thoemrem: Duistermaat-Heckmann, version 2
>The pushforward of the symplectic volume of $\calP$ under the moment map is a piecewise polynomial measure on $\mathfrak{t}$. 
^thm--DH-v2

>[!proof]+
>The pushforward of the symplectic volume is $f \prod \mathrm{d}t_i$ for a function $f(t) = \mathrm{Vol}(\calP_t)$. The dimension of $\calP_t$ is $2(n-m)$, so its volume is measured cohomologically by the class $[\omega_t]^{(m-n)}$. Since $[\omega_t]$ is piecewise linear, $\mathrm{Vol}(\calP_t)$ is a piecewise degree $(m-n)$ polynomial


>[!theorem]+ Theorem: Duistermaat-Heckman, version 3
>For a Hamiltonian $H$ generating a $U(1)$ action, the stationary phase approximation is *exact* for the Integral
 > $$\int_M e^{i t H}$$
 >That is, the integral localizes to the sum of gaussian integrals at the fixed points. This yields the Duistermaat-Heckman formula
 >$$\int_{M}e^{i t H} = \sum_{p \in F} \frac{e^{it H(p)}}{\sqrt{\mathrm{Det}(D^{2}H(p))}}$$

>[!proof]+ Proof 1
>Quickly follows from [[Toric geometry/Duistermaat-Heckman theorem#^thm--DH-v2|Duistermaat-Heckman theorem#^thm--DH-v2]]. Need to verify this equality holds for integrals over the moment map part, and the complement. The complement is locally exactly quadratic by [[Toric geometry/Equivariant Darboux's theorem|Equivariant Darboux's theorem]], so stationary phase is exact.  the moment map part is exact because Fourier transforms of polynomials is a sum of Dirac deltas and their derivatives, whose contribution must vanish by smoothness. 

 >[!proof]+ Proof 2
 >Follows from the localization formula in equivariant cohomology. The $U(1)$-equivariant extension of the symplectic form is 
 >$\omega^{\sharp}= \omega + itH$
 >Using this,
 >$$\int_{M}\omega^{n}e^{i t H}=\int_{M}e^{\omega^\sharp} $$
 >$e^{\omega^\sharp}$ is an equivariant cohomology class, so its integral localizes to $U(1)$ fixed points, and the formula retrieves the leading order stationary phase approximation.