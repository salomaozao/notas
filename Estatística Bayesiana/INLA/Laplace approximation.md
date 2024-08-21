Recall the basic Taylor series expansion, where a function about $a$ point can be expanded into a (sometimes infinite) sum of terms, and using a finite number of these terms can serve as an approximation (often the first three terms are used, up to the second derivative).
$$

\begin{equation*}
f(x) = f(a) + \frac{f’(a)}{1!}(x-a) + \frac{f’’(a)}{2!}(x-a)^2 + \frac{f’’’(a)}{3!}(x-a)^3 + …
\end{equation*}

$$
Say we have the basic parabola, $y=x^2$ . Expand around $a=2$ (here we could pick any value):
$$

\begin{align*}
f(x) = x^2 \hspace{7mm} f’(x) = 2x, \hspace{7mm} f’’(x) = 2, \hspace{7mm} f’’’(x) = 0
\end{align*}

$$
![taylor.png|735](https://www.precision-analytics.ca/articles/a-gentle-inla-tutorial/taylor.png)
A **Laplace approximation is used to estimate any distribution (PDF) with a normal distribution**. It uses the first three terms (quadratic function) Taylor series expansion around the mode $(\hat{x})$ of a function to approximate $\log g(x)$ (the log simplifies differentiation):
$$

\begin{align}
\log g(x) \approx \log g(\hat{x}) + \frac{\partial \log g(\hat{x})} {\partial x} (x-\hat{x}) + \frac{\partial^2 \log g(\hat{x})} {2 \partial x^2} (x-\hat{x})^2
\end{align}

$$
então, a variância estimada (baseada na curvatura), é:
$$

\begin{align}
\hat{s}^2=\log g(x) \approx \log g(\hat{x}) - \frac{1}{2\sigma^2} (x-\hat{x})^2
\end{align}

$$
Taking the exponent and integral of both sides and moving out the constants, we make a normal approximation
$$

\begin{align}
\int g(x)dx = \int exp[\log g(x) dx] \approx constant \int exp[ - \frac{(x-\hat{x})^2}{2\hat{\sigma^2}}]dx
\end{align}

$$Using a Laplace approximation the distribution $f(x)$ is approximately normal with mean $\hat{x}$ which can be found by solving $f’(x) = 0$, and variance $\hat{\sigma}^2 = -1/f’’(x)$ at the mode.
$$
f(x)\sim N\left(\hat{x}, \frac{-1}{f’’(x)}\right)
$$