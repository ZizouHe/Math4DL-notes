## Lecture 2: Symmetries and Geometric Stability

**Definition.** A symmetry of $$\mathcal{F}$$ is an invertible transformation $$T: \mathcal{X} \rightarrow \mathcal{X}$$ s.t.

$$
f(x) = f(T(x)), \forall f \in \mathcal{F}, \forall x \in \mathcal{X},
$$

where $$\mathcal{F} = \{f: \mathcal{X} \rightarrow \mathbb{R}\}$$.

Q: how symmetries in $$\mathcal{X}$$ related to symmetries in $$\Omega$$.

The set of symmetries forms a group.

Invariant and equivariant signal representations, $$\Phi: \mathcal{X} \rightarrow \mathcal{Z}$$ (feature space).

**Definition.** A representation $$\Phi: \mathcal{X} \rightarrow \mathcal{Z}$$ is invariant w.r.t. a group $$\mathcal{G}$$ of transformations if

$$
\Phi(Tx) = \Phi(x), \; \forall x \in \mathcal{X}, \forall T \in \mathcal{G}.
$$

**Definition.** A representation $$\Phi: \mathcal{X} \rightarrow \mathcal{Z}$$ is equivariant w.r.t. a group $$\mathcal{G}$$ of transformations if

$$
\Phi(T x) = \tilde{T} \Phi(x), \; \tilde{T} \in \tilde{\mathcal{G}} \simeq \mathcal{G}.
$$


Once we find a good representation,

$$
\begin{aligned}
\hat{f}(x) &= \langle \theta, \phi(x) \rangle, \; \; \text{regression} \\
&= \Gamma \left(\langle \theta, \phi(x) \rangle \right), \; \; \text{classification}
\end{aligned}.
$$

**Example.** $$x(u) \in L_1(\mathbb{R})$$,

$$
\Phi(x) = \int_{-\infty}^\infty x(u) \mathrm{d} \, u.
$$

Q: is $$\Phi(\cdot)$$ invariant to translation $$T_\tau = x(u-\tau)$$. Yes.

**Example.** $$x(u) \in L_1(\mathbb{R})$$, $$x(\cdot)$$ is bounded,

$$
\Phi(x) = \lim_{N\rightarrow \infty} \frac{1}{2N} \int_{-N}^N x(u) \mathrm{d} \, u.
$$

Q: is $$\Phi(\cdot)$$ invariant to translation.

$$
\begin{aligned}
\int_{-N}^N T_\tau x(u) \mathrm{d} \, u &= \int_{-N}^N x(u) \mathrm{d} \, u + \int_{N}^{N+\tau} x(u) \mathrm{d} \, u - \int^{-N}_{-N+\tau} x(u) \mathrm{d} \, u.
\end{aligned}
$$

$$
\begin{aligned}
\Phi_N(x_\tau) &= \frac{1}{2N} \int_{-N}^N T_\tau x(u) \mathrm{d} \, u \\
&= \Phi_N(x) + \frac{1}{2N} \left[\int_{N}^{N+\tau} x(u) \mathrm{d} \, u - \int^{-N}_{-N+\tau} x(u) \mathrm{d} \, u\right].
\end{aligned}
$$

Therefore,

$$
\left|\Phi_N(x_\tau) - \Phi_N(x) \right| \leq \frac{\tau}{N} \| x \|_\infty \rightarrow 0.
$$

**Example.** $$x(u) \in L_1(\mathbb{R})$$, $$x(\cdot)$$ has compact support,

$$
\Phi(x) = \frac{\int u |x(u)| \mathrm{d}\, u}{\int |x(u)| \mathrm{d}\, u}.
$$

Q: is $$\Phi(\cdot)$$ invariant to translation.

$$
\begin{aligned}
\Phi(T_\tau x) = \frac{\int u |x(u - \tau)| \mathrm{d}\, u}{\int |x(u -\tau)| \mathrm{d}\, u} = \frac{\int (u+\tau) |x(u)| \mathrm{d}\, u}{\int |x(u)| \mathrm{d}\, u}.
\end{aligned}
$$

Q: Is there a more systematic way to build Group invariant?

For Abelien group, yes. Assume $$\mathcal{X}$$ is a Hilbert space,

**Definition.** A one-parameter unitary group is a family of operators $$\varphi_t \in \mathrm{Ant}(\mathcal{X})$$ of $$\mathcal{X}$$, $$\{\varphi_t: \mathcal{X} \rightarrow \mathcal{X}\}_{t \in \mathbb{R}}$$ such that

(i) $$\forall t, s \in \mathbb{R}, \; \varphi_{s+t} = \varphi_s \cdot \varphi_t$$.
(ii) $$\lim_{s \rightarrow t} \|\varphi_s - \varphi_t\| = 0$$.
(iii) $$\|\varphi_t x\| = \|x\|, \; \forall x \in \mathcal{X}, \forall t \in \mathbb{R}$$.

**Theorem [Stone '30].** The set of self-adjoint operator of $$\mathcal{X}$$ is one-on-one to the set of one-parameter unitary group of $$\mathcal{X}$$.

(def. $$A$$ is self-adjoint if $$\langle Au, w\rangle = \langle u, Aw \rangle$$).

Given $$\{\varphi_t\}_{t\in \mathbb{R}} \rightarrow A$$ self-adjoint, ($$A$$ is the infinitesimal generator of $$\{\varphi_t\}$$).

$$
\varphi_s(t) = e^{itA}
$$

Therefore, if $$A$$ is self-adjoint, $$\rightarrow$$, there exists an orthogonal basis $$\{v_k\}$$ of $$\mathcal{X}$$ such that

$$
A v_k = \lambda_k v_k; \Longrightarrow \; \varphi_t v_k = e^{it \lambda_k} v_k.
$$

$$x \in \mathcal{X}$$, $$x = \sum_k \alpha_k v_k$$. Then,

$$
\varphi_t x = \sum_k \alpha_k \varphi_t v_k = \sum_k \alpha_k e^{it \lambda_k} v_k
$$

**Ex.** $$\varphi_t x(u) = x(u-t)$$, translation. Recall for $$x \in L_2(\mathbb{R}^s)$$,

$$
\begin{aligned}
\hat{x}(\xi) &= \int x(u) e^{-i 2\pi \langle u, \xi\rangle} \, \mathrm{d} \, u \\
\widehat{\varphi_t x}(\xi) &= \int x(u-t) e^{-i 2\pi \langle u, \xi\rangle} \, \mathrm{d} \, u = e^{2\pi i \langle t, \xi \rangle} \hat{x}(\xi)
\end{aligned}
$$

Consider $$\text{dim} \mathcal{X} = d$$, $$V \in \mathbb{C}^{d \times d}$$.

Q: how to build $$\Phi(\cdot)$$ that is $$\mathcal{G} = \{\varphi_t\}_{t \mathbb{R}}$$ invariant.

$$
\Phi(x) = \left| V^* x \right|.
$$

Claim: $$\Phi(\cdot)$$ is $$\mathcal{G}$$-invariant.

**Remarks.**

- For invariance to Abelien strcuture, a single hidden layer is OK.

- (Shortcomings) $$\Phi(x) = \boldsymbol{0}$$ is also invariant.

- (Shortcomings) We need representational power besides invariance. In previous example, we killed degree of freedom. Wasteful!

$$
\text{if} \; f^*(x) \neq f(x^\prime), \; \text{we need } \Phi(x) \neq \Phi(x^\prime),
$$

- what to do in the non-commutative case?

- Preserve information.

- Global v.s. local invariance.
