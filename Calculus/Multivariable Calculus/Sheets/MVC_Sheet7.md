# MVC7
#ProblemSheet #MVC 
>Stokes’ theorem. Examples. Consequences.
1. Let $0<a<b$. Verify [[Stokes' Theorem]] when $\mathbf{F}=(y, z, x)$ and $\Sigma$ is the upper half of the torus generated by rotating the circle $(x-b)^{2}+z^{2}=a^{2}$ about the $z$ -axis.
2. The vector field $\mathbf{F}(\mathbf{R})$ is defined by
$$
\mathbf{F}(\mathbf{R})=\int_{C}|\mathbf{r}-\mathbf{R}|^{2} \mathrm{~d} \mathbf{r}
$$
where $\mathbf{r}$ lies on the simple closed curve $C .$ Show that there are constant vectors $\mathbf{A}$ and $\mathbf{B}$ such that $\mathbf{F}(\mathbf{R})=\mathbf{R} \wedge \mathbf{A}+\mathbf{B} .$ Deduce that
$$
\nabla \wedge \mathbf{F}=-4 \iint_{S} \mathrm{~d} \mathbf{S}
$$
where $S$ is any smooth surface spanning $C$.
3. Let $\Sigma$ denote that part of the cone $x^{2}+y^{2}=z^{2}, z>0$ which lies beneath the plane $x+2 z=1$. Let $\mathbf{F}(x, y, z)=x\mathbf{j}$.
Show that the projection of $\partial \Sigma$ vertically to the $x y$ -plane is an ellipse. Parametrise $\partial \Sigma$ and determine $\int_{\partial \Sigma} \mathbf{F} \cdot \mathrm{d} \mathbf{r} .$
Show that $\mathrm{d} \mathbf{S} \cdot \mathbf{k}=\mathrm{d} x \mathrm{~d} y$ on $\Sigma$ and verify [[Stokes' Theorem]] for $\mathbf{F}$ on $\Sigma$.
4. Let $\mathbf{F}(x, y)=(u(x, y), v(x, y))$ be defined on $\mathbb{R}^{2}$ where $u, v$ have continuous partial derivatives of all orders.
(i) Under what condition on $u$ and $v$ is $\operatorname{curl} \mathbf{F}=\mathbf{0} ?$ Under what condition is $\operatorname{div} \mathbf{F}=0 ?$ Show that if both these conditions hold then $u$ and $v$ are harmonic $-$ that is, they satisfy [[Laplace's equation]].
(ii) Conversely say $U$ is a harmonic function. Use [[Green's Theorem]] to explain why
$$
\mathbf{G}(X, Y)=\left(U(X, Y), \int_{C} U_{y} \mathrm{~d} x-U_{x} \mathrm{~d} y\right)
$$
is a well-defined function, independent of the choice of curve $C$ from $(0,0)$ to $(X, Y)$. Show that $\operatorname{div} \mathbf{G}=0$ and $\operatorname{curl} \mathbf{G}=\mathbf{0}$
(iii) What is $\mathbf{G}(x, y)$ if (a) $U(x, y)=x^{2}-y^{2}$ ?
(b) $U(x, y)=e^{x} \cos y ?$
5. (Optional) Let $\mathbf{F}=\mathbf{r} / r^{3}=\mathbf{e}_{r} / r^{2}$, in terms of [[Spherical Polar Coordinates]], and let
$$
R_{1}=\mathbb{R}^{3} \backslash\{\mathbf{0}\} \quad \text { and } \quad R_{2}=\left\{(x, y, z) \in \mathbb{R}^{3}: x^{2}+y^{2} \neq 0\right\}
$$
(i) Show that $\operatorname{div} \mathbf{F}=0$.
(ii) Show that
$$
\mathbf{f}=\frac{\cot \theta}{r} e_{\phi}
$$
is a [[vector potential]] for $\mathbf{F}$ on $R_{2}-$ that is, show that $\mathbf{F}=\nabla \wedge \mathbf{f}$.
(iii) Why is $\mathbf{f}$ not a vector potential for $\mathbf{F}$ on $R_{1}$ ?