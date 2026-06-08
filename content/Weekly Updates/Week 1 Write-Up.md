**Key points**:
- Weak derivatives
- Soblev spaces
- Weak formulation of 1D Poisson equations
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

> **Weak derivative**: we say that g is a weak derivative of $u$ if 
> 
> $$
>	\int_{\Omega} g v' = -\int_{\Omega} fv, \forall v \in \cC^\infty_{c}(\Omega).
> $$

To motivate this definition, first note that if $u$ is smooth