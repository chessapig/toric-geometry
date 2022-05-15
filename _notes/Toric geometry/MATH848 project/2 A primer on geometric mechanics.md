---
{"dg-publish":true,"permalink":"/toric-geometry/math-848-project/2-a-primer-on-geometric-mechanics/","dgHomeLink":true,"dgPassFrontmatter":false}
---

#writing 
```toc
```
^toc--section-2

# The shape of motion: A primer on geometric mechanics

The Hamiltonian formulation of classical mechanics studies motion of objects, like a ball on a spring, as a flow through some phase space. Like most physics, phase space was originally implicitly assumed to be Euclidean, but the complexities of celestial mechanics outgrew this local version. Phase space was reinterpreted as a *manifold*, endowed with a "symplectic form" which controlled the dynamics. Thus, symplectic geometry was born. Eventually, symplectic geometry separated from its physical origin to become its own field of mathematics. 

Start with the canonical example...

## The harmonic oscillator and Hamiltonian mechanics

Physically represented by the dynamics of a spring, which applies a restoring force proportional to the displacement. The force is proportional to the acceleration, meaning the motion is described by the following differential equation:

$$\ddot{x} = -x$$ ^eq--newtons-equations

Where all dimensional constants are set to one. The dynamics of this diffeq are easier to grasp in its equivlent system of first order of coupled differential equations:
$$ \dot p = - x$$
$$\dot x = p$$
a physical state is a pair of position $x$ and "momentum" $p$, defining a point in "phase space" $\calP =\RR^2$ ==include image==. The equations are encoded in a vector field over phase space. Solving the system, a state evolves by rotating at a constant rate in $\RR^2$. Focusing on the position, we see the particle oscillates sinusoidally with time. 

We can cast theses equations in the more suggestive form

$$  
\begin{gather}
	\dot p = -\frac{\del H}{\del x} \qquad \dot x = \frac{\del H}{\del p}\\
	H(x,p) = p^{2} + x^{2}
\end{gather}
$$
^eq--Hamiltons

==say why these come from: Rotate 90 degrees==

The evolution of position and momentum are controlled by the derivatives of a single function on phase space, which we call the Hamiltonian. 

The harmonic oscillator is characterized by the quadratic Hamiltonian. Their physical ubiquity stems from the mathematical role of quadratics, appearing as low order terms in Taylor series. But this Hamiltonian has a distinguished property that we've already seen: It generates rotation! If you start with a set of points set at different distances from zero, they will rotate at lock step, never falling out of phase. Formally, we can represent the evolution of a point of phase space $\calP$ after time $t$ by a map $\psi_t : \calP \to \calP$. The harmonic oscillator is periodic with period $T = 2\pi$, meaning everything returns after time $T$, $\psi_T = id$. This periodicity, along with the identity $\psi_t \circ \psi_s = \psi_{t+s}$, means the evolution $\psi_t$ is an $U(1)$ action on $\calP$. This is the fundamental connection between harmonic oscillators and the circle group, mentioned in the introduction. We will see many consequences of this connection below.

>[!remark]+ 
> The harmonic oscillator is uniquely characterized by this periodicity. There are many other Hamiltonians on $\RR^2$ where every point is periodic, with the same period. However, these all come from composing the harmonic oscillator Hamiltonian with an area-preserving diffeomorphisms, meaning they are harmonic oscillators in a different set of coordinates. 
^rmk--harmonic-osscilator-periodic



We can make the $U(1)$ action explicit by identifying phase space $\RR^2$ with the complex plane $\CC$, where $x$ is the real part and $p$ is the imaginary part. Realizing $t \in U(1)$ as a unit norm element in the complex plane, the evolution $\psi_t$ is multiplication by $t$.

These equations naturally generalize to higher dimensions. in $n$ dimensions, there are n position variables $x_1, \dots, x_n$ with associated momenta $p_1, \dots, p_n$, defining a point in phase space  $\calP = \CC^n$. The Hamilton equations on this phase space are 
$$

\begin{align}
\dot p_{i}&= -x_i\\
\dot{x_{i}} &= p_i
\end{align}
$$


The standard harmonic oscillator in $n$-dimensions is defined by a Hamiltonian 
$$H = \sum_i x_i^2 + p_i^2 $$
But we notice this essentially describes $n$ different, noninteracting harmonic osscilators. Leaning into this, we split $H$ into consitituent parts: ^0da6d9

$$H= \sum_i H_i ,\qquad H_i = x_i^2 + p_1^2$$

Each Hamiltonian $H_i$ rotates its own factor of $\CC$ in phase space.

This procedure is ethos of Hamiltonian mechanics. Mechanics lives on phase space, whose structure converts a Hamiltonian function to a vector field, describing evolution under that Hamiltonian.

## symplectic mechanics

%%==Cotangent bundle of spaces, inspired by pendulum==%%

Now we turn to geometry. We want to eventually replace the phase space $\CC^n$ with an arbitrary manifold $\calP$, and somehow define mechanics on $\calP$ that reduces to the hamiltons equations above in some coordinate chart. This is tricky with the coordinate-dependent formula [[Toric geometry/MATH848 project/2 A primer on geometric mechanics#^eq--Hamiltons|2 A primer on geometric mechanics#^eq--Hamiltons]], so we need a coordinate invariant formulation. We achieve this using differential forms. 


This finally motivates the phase space structure of a manifold $\calP$ is encoded in a 2-form $\omega$, called the *Symplectic form*, Such that:

- $\omega$ is nondegerenate, as a linear transform sending $T^*\calP$ to $T\calP$.
- $\de \omega = 0$. 

The first condition ensures that there always exists a unique Hamiltonian vector field $X_H$ such that $\omega(X_H,-) = \de H$. The second ensures that the sympletic form is locally modeled on the standard phase space. Closedness is necessary because the syandard symplecitc form $\CC^n$ is certainly closed, but remarkeably closeness is also sufficient. This is called [[Toric geometry/Darboux's theorem|Darboux's theorem]]:



>[!theorem]+ Theorem: (Darboux)
>Let $(\calP,\omega)$ be a symplectic manifold. Each point $p\in \calP$, has a neighborhood $U$ with coordinate chart $\phi:U\to \CC^n$ such that $\omega$ is the pullback of the standard symplectic form on $\CC^n$. That is, $U$ has coordinates $q_i , p_i$ such that $\omega = \de q_1 \wedge \de p_1 + \dots + \de q_n \wedge \de p_n$
^thm--Darboux

This fact makes symplectic geometry feel significantly different from other sorts of geometry. Compare this with the analagous statement in Riemannian geometry: A metric can be put in the standard, euclidean form *pointwise*, but on an open neighborhood it can diverge from the standard due to its curvature. However, Darboux's theorem says the standard form holds on the whole open est. There are no local invariants of a symplectic form akin to curvature. Said another way, all symplectic forms are locally isomorphic. This gives symplectic geometry a fundamentally globally character, to the point that the names "symplectic geometry" and "symplectic topology" are used interchangably. 

>[!remark] Remark: Proof of Darboux's theorem
>You can find a proof of Darboux's theorem in any book on symplectic geometry (see for instance ==Mcduff==), but to not leave you high and dry, let me give you the gist. We want to show any two symplectic forms on a small open set are equivalent by constructing a symplectomorphism: A diffeomorphisms pulling back one form to the other. (In particular, this can relate the given symplectic form to the standard one). We will instead look for an explicit path of diffeomorphisms, which is infinitesimally encoded in a time-varying vector field. A little manipulation shows this vector field satisfies a differential equation, which in fact is a version of Hamilton's equations. By non-degeneracy, we know a solution to Hamiltons equations exists, and we are done! Though constructing a whole path of diffeomorphisms seems like it would be harder, it lets us exploit the infinitesimal geometry that we know how to manipulate. This bit of slight-of-hand is called *Moser's trick*.  Symplectic geometry has many similar results turning structures into a standard form, all proven with a suitably generalized version of Moser's trick. 
^rmk--mosers-trick

Note that $\omega$ as a matrix is skew-symmetric, since it comes from a 2-from. In particular, if $n$ is odd, $\omega$ must have an unpaired zero eigenvalue, and be degenreate. So, nondegenracy means that symplectic manifolds are always even dimsnional.

>[!Example]+ Example: Symplectic structure on $S^2$
>The two dimensional sphere can be given a symplectic structure. Construct $S^2$ as the set of vectors of unit length in $\RR^3$. For a vector $p$ with unit length, the tangent space to the sphere is naturally the set of vectors normal to $p$. A symplectic form takes two tangent vectors $v,w$ and bilinearly returns a number. We define the standard symplectic form $\omega_s$ using the cross product of vectors in $\RR^3$:
>$$\omega_s(v,w) = ||v \times w ||$$
>This defines a two form because the cross product is bilinear and antisymmetric. As a two-form on a two dimensional manifold, it is necessarily closed. It is nondegenerate because any $v$ has a $w$ such that $v \times w \neq zero$, for instance $w = p\times v$. Hence, it is indeed symplectic.
^ex--S2-symplectic

## symmetries of classical mechanics
A symmetry of classical mechanics is a symmetry of phase space, which is a manifold with a symplectic structure. For a general manifolds, symmetries are *Diffeomorphisms*, differentiable bijective maps with differentiable inverses. These form a group where multiplication is composition of diffeomorphisms, which in particular has an infinitesimal structure. A path of diffeomorphisms can be described infinitesimally by a differentiable vector field, which points in the direction which points are pushed. Accordingly, pushing points along a fixed vector field $X$ defines a family of diffeomorphisms, the flow $\phi_X^t$ (This structure makes the group of diffeomorphisms an infinite dimensional *Lie group*).

The interesting group structure comes from the failure of commutativity, measured for diffeomorphisms $a,b$ by their commutator $a \circ b \circ a\inv \circ b\inv$. The infinitesimal structure of the group is encoded by the infinitesimal version of the commutator, called the *Lie bracket*
$$ [X,Y] := \frac{\de}{\de s}\frac{\de}{\de t} \phi_X^t \circ \phi_Y^s \circ \phi_X^{-t} \circ \phi_Y^{-s} |_{s,t=0}$$
This measures how one vector field changes along the flow of another. Taking the inverse of the RHS shows that the Lie bracket is antisymmetric, $[X,Y] = -[Y,X]$.The associativity of the group, encoded infinitesimally, enforces a condition on the Lie brackets called the Jacobi identity
$$[ [X,Y] , Z] + [ [Y,Z] , X] + [ [Z,X] , Y]=0$$
The structure of a manifold are encoded in the Lie bracket on the space of vector fields, making this space into what's called a *Lie algebra*.

Symmetries of a symplectic manifold are symmetries of a manifold that preserve the symplectic structure. These are diffeomorphisms $\phi$ such that $\phi^*\omega = \omega$, which are called *Symplectomorphisms*. Infinitesimally, these are vector fields $V$ preserving the symplectic form, $\calL_V \omega = 0$. Using Cartan's magic formula $\calL_ V = \de \iota_V + \iota_V \de$ and the fact that $\de \omega = 0$, $V$ preserves $\omega$ when $\iota_V\omega$ is closed. Locally, these forms are equal to $\de H$ for some function $H$, which by definition makes $V$ a Hamiltonian vector field. That is, infinitesimal symmetries of a symplectic manifold are locally defined by smooth functions.

We can now pull back the Lie algebra structure from vector fields to their defining Hamiltonian functions. This is called the *Poisson bracket*, denoted by $\{H,H'\}$. Just as the Lie bracket measures the change in one vector field under the flow of another, the Poisson bracket measures the change in one Hamiltonian under the flow of the other
$$\{H,H'\} \equiv \frac{\de}{\de t}\phi_{X_{H}}^t H' = X_{H}(H') = \de H' (X_{H}) = \omega(X_{H},X_{H'})$$
Note that the Poisson bracket is bilinear, by the linearity of the hamiltonian vector field. The antisymmetry of $\omega$ means the Poisson bracket is antisymmetric, and a computation in coordinates verifies the Jacobi identity. So, the Poisson bracket makes the algebra of smooth functions on phase space into a Lie algebra. And indeed, the Poisson bracket on Hamiltonians is equivalent to the lie bracket on their vector fields:
$$[X_{H},X_{H'}] = X_{\{H,H'\}}$$

>[!remark]+
>We can think of the fundamental structure of classical mechanics as the algebra of smooth functions $C^\infty(M)$ with Poisson bracket ('classical observables'). This alternate point of view to symplectic geometry gives a clear philosophical correspondence with quantum mechanics. There, the fundamental structure is the algebra of operators on a Hilbert space with commutator ('quantum observables'). To 'quantize' a classical system, you associate a Hilbert space to a symplectic manifold, and construct a Lie algebra homomorphism from smooth functions with Poisson bracket to operators with commutator. In practice, this procedure can be rather difficult and is almost never possible in full generality, but that's a story for another time.

