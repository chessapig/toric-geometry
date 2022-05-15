---
{"dg-publish":true,"permalink":"/toric-geometry/math-848-project/6-semiclassical-properties-of-moment-maps/","dgHomeLink":true,"dgPassFrontmatter":false}
---


```toc
```
# Semiclassical properties of moment maps: The Duistermaat-Heckman theorem

So far we have seen some of the superpowers of torus actions, framing their moment maps as a global versions of a harmonic oscillators. Moment maps inherit some special properties from harmonic oscillators, which are seemingly independent of their associated $U(1)$ action. As usual this comes from physics, and specifically the border between classical and quantum mechanics. Suppose that we're interested in stationary states of a system. In classical mechanics, a state is a point on a symplectic manifold $M$ evolving under a Hamiltonian flow, and it is stationary when it sits at one of the Hamiltonian's critical points. Quantum mechanics promotes states from points to complex valued functions, meaning the quantum properties include contributions from all points, not just the classically fixed ones. In the so-called path integral formulation, this data is all encoded in a single *partition function*
$$Z(t) = \int_M \exp{i t H}$$

The parameter $t$ controls the strength of quantum mechanical effects, so is often denoted by $1/\hbar$. As $t$ becomes very large the integrand oscillates extremely quickly away from fixed points of $H$. The rapid oscillations cancel each other out, so integrals' value is primarily controlled by the fixed points. This is formally encoded in the \textit{Stationary phase approximation}, which aymptotically expands the integral in orders of $1/t$ using fixed points of $H$. (We will more carefully describe this momentarily). Physically this represents a sort of semiclassical limit, and the integral depends only on fixed points because quantum states concentrate towards classical states as $\hbar$ goes to zero. For harmonic oscillators, semiclassical expansions stop after first order. That is, the semiclassical limit is *exact*. Now, given my repeated insistence that $U(1)$ moment maps are global versions of harmonic osscilators, you might have guessed:
==Include picture==

>[!Theorem]+ [[Toric geometry/Duistermaat-Heckman theorem|Duistermaat-Heckman theorem]]
> The stationary phase approximation is exact for $U(1)$ moment maps


In physics you run into a potpourri of examples when the semiclassical approximation is no approximation: The harmonic osscilator, the free particle, a particle in a constant field, etc. It seems like these are just simple examples where we happen to get lucky, but Duistermaat-Heckman (DH) shows the underlying reason: A shared $U(1)$ symmetry. In fact, DH is a just a small manifestation of a rich underlying structure called *equivariant cohomology*, which naturally extends cohomology to spaces with group actions. 

There are two routes to prove the Duistermaat-Heckman theorem. The first, used by the namesake \addCite{DH}, provides a simple form for symplectic form on a symplectic reduction as the offset of the moment map varies. The stationary phase approximation falls out as a corollary. The second approach uses equivariant cohomology. The DH theorem is a specific case of a very general localization formulae, which describes equivariant cohomology classes through the fixed points of a group action. Both proofs involve structures which are interesting in their own right, and their methods illuminate one another. We will follow Duistermaat and Heckman's original proof in this section, and see a taste of equivariant cohomology in the next.

## Variation of symplectic stuctures

Say a symplectic manifold $M$ carries a $G$-action with moment map $\mu: M \to \frak{g}^*$. Recall the definition of the symplectic reduction:

$$M_0 = M // G = \mu\inv(0)/G$$

Which is a manifold when $0$ is a regular value of the moment map, so that $G$ acts freely on $\mu\inv(0)$. The choice of 0 here is ultimatley arbitrary: We could have chosen any regular value $t \in \frak{g}^*$, obtaining the symplectic manifold
$$M_t  \equiv \mu\inv(t)/G$$
But how does $M_t$ depend on $t$? For inspiration, let's look to our new friends, the toric manifolds. 


>[!example]+ 
> Consider $\PP^2$, described in example ==link example==, whose moment polytope shown in figure ==add figure==. This has a $U(1)^2$ action generated by the Hamiltonians which are projection $\pi_x$ onto the $x$ axis and $\pi_y$ onto $y$. Consider the $U(1)$ action generated by $\pi_x$, and its symplectic reduction $\PP^2_t = \pi_x\inv(t)/U(1)$ for $t\in (0,1)$. This manifold is still toric, from the residual action of $\pi_y$. Indeed, $\pi_y$ is a function on $\pi_x\inv(t)$, which is invariant on the orbits generated by $\pi_x$ since the two Hamiltonians commute. So, $\pi_y$ descends to $\PP^2_t$. The associated moment map is the slice of the polytope for $\PP^2$ defined by $\pi_x = t$, which is a line segment of length $\ell(t)$. By the delzant correspondence, we know the symplectic reduction: The line becomes a sphere, with form proportial to the line's length
>$$\PP^2_t = (S,\ell(t) \omega_{FS}) $$
>From the diagram, we can see $\ell(t) = 1-t$. In particular, this is \textit{linear} with the value of the moment map. We get something similar for any Hamiltonian coming from $\pi_x$ and $\pi_y$. Figure ==add figure== depicts projecting onto some generic 1-dimensional subspace of ${\frak{u}(1)^2}^*$, and we see that the length of slices first grows linearly, then shrinks linearly.


At least intuitivly, this generalizes to any toric manifold. For a Hamiltonian projecting the moment polytope onto a dimension one subspace, the slices are all polytopes whose sides vary linearly with the Hamiltonian. The symplectic form is piecewise linear, with discontinuities at critical points of the Hamiltonian (when the slice hits a vertex of the polytope).

This intuition almost carries us to the general case. In fact, an arbitrary $U(1)$ action has a symplectic form which is linear *in cohomology*


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">



</div>

#theorem 


Let $(\calP,\omega)$ be a 2m-dimensional symplectic manifold, with $U(1)^n$ action defined by [[Toric geometry/Moment map|Moment map]]$\mu:\calP \to \mathfrak{t}^*\equiv {\mathfrak{u}(1)^{n}}^*$.  [[Toric geometry/Symplectic reduction|Symplectic reduction]] yields a family of symplectic manifolds parametrized by the level of the moment map $t\in \mathfrak{t}^*$:

$(\calP_{t},\omega_{t} ) = \mu\inv(t)/U(1)^n$


>[!theorem] Theorem: Duistermaat-Heckman, version 1
>The cohomology class  $[\omega_t]$ depends piecewise linearly on $t$. More precisely, for $t$ in a neighborhood of a regular value $t_0$, The manifolds $\calP_{t}$ and $\calP_{t_0}$ are diffeomorphic, and there is a fixed element $c\in H_2(\calP_{t_0},\mathfrak{t})$ such that
>$[\omega_{t}] = [\omega_0] + \langle t-t_{0},c\rangle $
^thm--DH-v1

>[!proof]+ 
>Follows from normal form of $U(1)^n$ actions. Since $t_0$ is regular, $\mu\inv(t_0)$ is a $U(1)^{n}$ principal bundle $P \to \calP$. For a neighborhood of regular values $U$, $\mu\inv(U)$ is a subset of $P \times \mathfrak{t}^*$. This carries a natural symplectic form 
>$\omega' =  \pi^{*}\omega_{0}+\langle t,F_t \rangle$
>where $F$ is the curvature of $P$ as a $\mathfrak{t}$-valued 2-form. This implies
>$\frac{\de}{\mathrm{d} t}\omega_t =  F_t $
>The cohomology of $F$ is constant, constrained topologically to equal the first Chern class $c$.  So, the derivative of $\omega_t$ is constant, meaning $\omega_t$ is linear in $t$.



>[!theorem]+ Thoemrem: Duistermaat-Heckmann, version 2
>The pushforward of the symplectic volume of $\calP$ under the moment map is a piecewise polynomial measure on $\mathfrak{t}$. 
^thm--DH-v2

>[!proof]+
>The pushforward of the symplectic volume is $f \prod \mathrm{d}t_i$ for a function $f(t) = \mathrm{Vol}(\calP_t)$. The dimension of $\calP_t$ is $2(n-m)$, so its volume is measured cohomologically by the class $[\omega_t]^{(m-n)}$. Since $[\omega_t]$ is piecewise linear, $\mathrm{Vol}(\calP_t)$ is a piecewise degree $(m-n)$ polynomial


>[!theorem]+ Theorem: Duistermaat-Heckman, version 3
>For a Hamiltonian $H$ generating a $U(1)$ action, the stationary phase approximation is *exact* for the Integral
 > $\int_M e^{i t H}$
 >That is, the integral localizes to the sum of gaussian integrals at the fixed points. This yields the Duistermaat-Heckman formula
 >$\int_{M}e^{i t H} = \sum_{p \in F} \frac{e^{it H(p)}}{\sqrt{\mathrm{Det}(D^{2}H(p))}}$

>[!proof]+ Proof 1
>Quickly follows from [[Toric geometry/Duistermaat-Heckman theorem#^thm--DH-v2|Duistermaat-Heckman theorem#^thm--DH-v2]]. Need to verify this equality holds for integrals over the moment map part, and the complement. The complement is locally exactly quadratic by [[Toric geometry/Equivariant Darboux's theorem|Equivariant Darboux's theorem]], so stationary phase is exact.  the moment map part is exact because Fourier transforms of polynomials is a sum of Dirac deltas and their derivatives, whose contribution must vanish by smoothness. 

 >[!proof]+ Proof 2
 >Follows from the localization formula in equivariant cohomology. The $U(1)$-equivariant extension of the symplectic form is 
 >$\omega^{\sharp}= \omega + itH$
 >Using this,
 >$\int_{M}\omega^{n}e^{i t H}=\int_{M}e^{\omega^\sharp} $
 >$e^{\omega^\sharp}$ is an equivariant cohomology class, so its integral localizes to $U(1)$ fixed points, and the formula retrieves the leading order stationary phase approximation.

</div></div>



Note that we're identifying the manifold underlying $M_t$ with $M_0$. This comes from Morse theory, as $M_0$ and $M_t$ are quotients of level sets of the same function, and there are no critical points between $0$ and $t$ to change their topology.

Like many other symplectic geometry constructions, theorem [[Toric geometry/Duistermaat-Heckman theorem|Duistermaat-Heckman theorem]] comes from a normal form construction. We will eventually identify a part of $M$ with no critical points with a complex line bundle over $M_t$. But to inform the math approach, let's instead start thinking physically. 


## Intermission: Symmetries of Electromagnetism

This section is somewhat of a digression from the primary plotline, but I can't resist mentioning. 


\subsection{Symplectic structures on space of orbits}
Normal form: Describe using line bundles, electromagentism



 