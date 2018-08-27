Sampling of Finite Population
@Author: ky liu

* a finite population is denoted as $\mathcal{P}=\{x_1,x_2,\cdots,x_N\}$.
* a sample of population $\mathcal{P}$ is $\mathcal{S}=\{X_1,X_2\,\cdots,X_n\}$.

The population mean of $\mathcal{P}$ is
$$
	\overline{X}=\frac{1}{N}\sum_{i=1}^{N}x_i.
$$

The population variance of $\mathcal{P}$ is
$$
	S_X = \frac{1}{N-1}\sum_{i=1}^{N}\left(x_i-\overline{X}\right)^2.
$$

For the sample $\mathcal{S}$, an estimator might be
$$
	\overline{x} = \frac{1}{n}\sum_{i=1}^{n}X_i.
$$

The expectation and variance of $\overline{x}$ are **non-trivial**!

-

***Expectation***: 

Since $\mathcal{S}$ is chosen from $\mathcal{P}$, there are totally $\binom{N}{n}$ possible samples with equal occurrence probability. Define indicator variable $Z_i$ as
$$
	Z_i = \begin{cases}
				1, &x_i\in\mathcal{P}\text{ is chosen in }\mathcal{S}\\
				0, &\text{otherwise}
			\end{cases}
$$

It is easy to see $\Pr\left[Z_i\right]=\frac{n}{	N}$. Thus, the expectation of estimator $\overline{x}$ is
$$
\begin{aligned}
	\mathbf{E}\left[\overline{x}\right] &= \mathbf{E}\left[\frac{1}{n}\sum_{i=1}^{n}X_i\right]\\
	&= \mathbf{E}\left[\frac{1}{n}\sum_{i=1}^{N}x_i\cdot Z_i\right]\\
	&= \frac{1}{n}\cdot\left[\sum_{i=1}^{N}x_i\cdot \mathbf{E}\left[Z_i\right]\right]\\
	&= \frac{1}{n}\cdot\left[\sum_{i=1}^{N}x_i\cdot \frac{n}{N}\right]\\
	&= \frac{1}{N}\sum_{i=1}^{N}x_i = \overline{X}.
\end{aligned}
$$

-
***Variance***:

We show the result first. The variance of estimator $\overline{x}$ is given by
$$
	\mathbf{Var}[\overline{x}] = \frac{N-n}{Nn}\cdot S_X,
$$
where $S_X$ is the population variance and the factor $\frac{N-n}{Nn}$ is called *finite population correction factor*.

The result is reasonable by observing that if $n=N$, $\mathbf{Var}[\overline{x}]=0$ (all elements in the finite population are used).

We begin to prove this. 
$$
\begin{aligned}
	\mathbf{Var}\left[\overline{x}\right] &= \mathbf{Var}\left[\frac{1}{n}\sum_{i=1}^{n}X_i\right]\\
	&= \mathbf{Var}\left[\frac{1}{n}\sum_{i=1}^{N}x_i\cdot Z_i\right]\\
	&= \frac{1}{n^2}\cdot\left(\sum_{i=1}^{N}x_i^2\cdot\mathbf{Var}\left[Z_i\right]+\sum_{i\neq j}x_ix_j\mathbf{Cov}[Z_i,Z_j]\right)
\end{aligned}
$$
where 
$$
	\mathbf{Var}[Z_i] = p\cdot(1-p) = \frac{n}{N}\cdot\left(1-\frac{n}{N}\right)
$$
and 
$$
\begin{aligned}
	\mathbf{Cov}[Z_i,Z_j] &= \mathbf{E}[Z_iZ_j]-\mathbf{E}[Z_i]\mathbf{E}[Z_j]\\
	&= \frac{n(n-1)}{N(N-1)}-\frac{n^2}{N^2}\\
	&= \frac{n(n-N)}{N^2(N-1)}.
\end{aligned}
$$

Note that, 
$$
\begin{aligned}
	\mathbf{E}[Z_iZ_j] &= \Pr[Z_i=1, Z_j=1]\\
	&= \Pr[Z_j=1|Z_i=1]\cdot\Pr[Z_i=1]\\
	&= \frac{n-1}{N-1}\frac{n}{N}.
\end{aligned}
$$

Thus, the variance can be simplified as
$$
\begin{aligned}
	\mathbf{Var}\left[\overline{x}\right] &= \frac{1}{n^2}\cdot\left(\sum_{i=1}^{N}x_i^2\cdot\mathbf{Var}\left[Z_i\right]+\sum_{i\neq j}x_ix_j\mathbf{Cov}[Z_i,Z_j]\right) \\
	&= \frac{1}{n^2}\cdot\left(\sum_{i=1}^{N}x_i^2\cdot\frac{n(N-n)}{N^2}+\sum_{i\neq j}x_ix_j\frac{n(n-N)}{N^2(N-1)}\right)\\
	&= \frac{1}{n^2}\cdot\frac{n(N-n)}{N^2}\cdot\left(\sum_{i=1}^{N}x_i^2-\frac{1}{N-1}\sum_{i\neq j}x_ix_j\right)
\end{aligned}
$$

Note that, 
$$
\begin{aligned}
	S_X &= \frac{1}{N-1}\sum_{i=1}^{N}\left(x_i-\overline{X}\right)^2 \\
	&= \frac{1}{N-1}\sum_{i=1}^{N}\left(x_i^2-2x_i\cdot\overline{X}+\overline{X}^2\right)\\
	&= \frac{1}{N-1}\left(\sum_{i=1}^{N}x_i^2-2\overline{X}\cdot\sum_{i=1}^{N}x_i+N\cdot\overline{X}^2\right)\\ 
	&= \frac{1}{N-1}\left(\sum_{i=1}^{N}x_i^2-N\cdot\overline{X}^2\right)\\
	&= \frac{1}{N-1}\left(\sum_{i=1}^{N}x_i^2-\frac{1}{N}\cdot\left(\sum_{i=1}^{N}x_i\right)^2\right)\\
	&= \frac{1}{N-1}\left(\sum_{i=1}^{N}x_i^2-\frac{1}{N}\cdot\left(\sum_{i=1}^{N}x_i^2+\sum_{i\neq j}x_ix_j\right)\right)\\
	&= \frac{1}{N}\cdot\left(\sum_{i=1}^{N}x_i^2-\frac{1}{N-1}\sum_{i\neq j}x_ix_j\right).
\end{aligned}
$$

Bring it back to $\mathbf{Var}[\overline{x}]$, we have
$$
\begin{aligned}
	\mathbf{Var}\left[\overline{x}\right] &= \frac{1}{n^2}\cdot\frac{n(N-n)}{N^2}\cdot\left(\sum_{i=1}^{N}x_i^2-\frac{1}{N-1}\sum_{i\neq j}x_ix_j\right)\\
	&= \frac{1}{n^2}\cdot\frac{n(N-n)}{N^2}\cdot N\cdot S_X\\
	&= \frac{N-n}{nN}\cdot S_X.
\end{aligned}
$$

Thus, we finish the proof.
