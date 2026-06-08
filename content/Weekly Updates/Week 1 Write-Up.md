**Key points**:
- Weak derivatives
- Weak formulation of 1D Poisson equations
- Soblev spaces
---

We start with 1D Poisson equations. We use the following boundary value problem as in Silverster's Primer on finite elements:
$$
	\begin{cases}
		-u''(x) = f \\
		u(0) = 0 = u(1),
	\end{cases} \tag{1}
$$
where we seek solution $u:\Omega \to \mathbb{R}$, $\Omega = [0,1].$

Classically we need $u \in \cC^2$; however, such requirement is too restrictive as in practice, we often need $f$ to be much irregular, e.g., a step function, or Dirac function. The price we pay to allow these irregular $f$'s is that we will have to lose the property that $u$ agrees with the above BVP pointwisely. 

To see this, one note that if
$$
	f(x) = \begin{cases}
		1 \text{ if } x \geq \frac{1}{2}  \\
		0 \text{ otherwise,}
	\end{cases}
$$
a simple step function, then there is no **function** $u$ (not just the ones in $\cC^2$) s.t. $-u''\left( \frac{1}{2} \right) = f\left( \frac{1}{2} \right)$ because of [Darboux's theorem](https://en.wikipedia.org/wiki/Darboux%27s_theorem_(analysis)).

This means that we need to enlarge the definition of derivatives so that BVP like $(1)$ can have solutions for irregular $f$.

> **Weak derivative (1D)**: we say that $g \in L^2(\Omega)$ is a weak derivative of $u \in L^2(\Omega)$ if 
> 
> $$
>	\int_{\Omega} gv = -\int_{\Omega} u v', \forall v \in \cC^\infty_{c}(\Omega).
> $$

To motivate this definition, first note that if $u$ is smooth enough, and $v$ is perfectly smooth and vanishes at $\partial \Omega$, then by 1D integration by parts, 
$$
	\int_{\Omega} u'v = \underbrace{ [uv]_{\partial\Omega} }_{ 0 } - \int_{\Omega} uv' = - \int_{\Omega} uv'.
$$
The the definition of weak derivative just turned the above observation on its head: $g$ is a weak derivative of $u$ if they make the above integral formula true. 

One note that if $g$ is a classic derivative of $u$ then it is a weak derivative, so the definition of weak derivative is indeed a generalization, and we have enlarge the spaces where $u$ has any derivatives from the space of differentiable functions on $\Omega$ to $L^2(\Omega)$.

Also note that we need $u, g \in L^2$ so that the integrals are finite.

---

Therefore, the differential equation in $(1)$ can be read as that $u$'s double weak derivative is $-f$. This gives the **weak formula** of the 1D poisson: we seek $u \in L^2$ that
$$
	\int_{\Omega} -fv = -\int_{\Omega} u'v', \text{ or simply } \int_{\Omega} fv = \int_{\Omega} u'v', \forall v \in \cC^\infty_{c}(\Omega),
$$
that satisfy the boundary condition $u(0) = 0 = u(1)$ and that $u' \in L^2$.



The theory goes deeper. The solution $u$ before naturally sits inside **Sobolev space**.
> **Sobolev space**: $H^k(\Omega) = \left\{  u: \Omega \to \mathbb{R}: \int_{\Omega}u^2, \int_{\Omega} (u')^2, \dots, \int_{\Omega}(u^{(k)})^2 < \infty \right\},$ where $u', u'', \dots, u^{(k)}$ includes weak derivatives.

More precisely,
$$
	u \in H^1_{0}(\Omega) = \{ u \in H^1(\Omega) : u(0) = 0 = u(1) \}.
$$

It's an established result that $H^k$ is a complete normed space, i.e., a Banach space.

Therefore, we can rephrase the weak formulation of 1D Poisson as that we seek $u \in H^1_{0}$ s.t.
$$
	\int_{\Omega} fv = \int_{\Omega} u'v', \forall v \in \cC^\infty_{c}(\Omega). \tag{2}
$$

Also note that Silverster introduces the weak formulation as that we seek $u \in H^1_{0}$ s.t.
$$
	\int_{\Omega} fv = \int_{\Omega} u'v', \forall v \in H^1_{0}. \tag{3}
$$
One note that (2) and (3) are the same statement as $\cC^\infty_{c}(\Omega)$ is dense in $H^1_{0}(\Omega)$ with the Sobolev norm.