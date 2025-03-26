# A Measure-Theoretic Look at LOTUS

The Law of the Unconscious Statistician is one of the most useful and "nicest feeling" results in probability.  In an introductory probability class, the law is stated separately for discrete and continuous random variables: 

$$
E[g(X)] = \sum_{x \in supp(X)} g(x) f_X(x)
$$

$$
E[g(X)] = \int_{x \in supp(X)} g(x) f_X(x) dx
$$

However, LOTUS is in fact more general, and is really just a specific case of the general measure-theoretic change of variables formula.

## Proof of the General LOTUS

For setup, assume:

- $X$ is a random variable mapping from a probability space $(\Omega, F, P)$ into a measurable space $(R, B)$

- $g:(R, B) \rightarrow (X, S)$ 

Then:

$$ E[g(X)] = \int_{\Omega} g(X(\omega)) dP $$

Now assume $g$ to be a positive simple function, such that there exist a collection of disjoint $A_i \in B$ where:

$$g(x) = \sum_i c_i I_{x \in A_i}$$

Then:

$$\int_{\Omega} g(X(\omega)) dP  = \int_{\{\omega \in F | X(\omega) \in \cup_i A_i\}} g(X(\omega))dP + \int_{\{\omega \in F | X(\omega) \notin \cup_i A_i\}} g(X(\omega))dP$$

$$= \int_{\{\omega \in F | X(\omega) \in \cup_i A_i\}} g(X(\omega))dP$$

$$= \sum_i \int_{\{\omega \in F | X(\omega) \in A_i\}} g(X(\omega))dP$$

$$ = \sum_i \int_{\{\omega \in F | X(\omega) \in A_i\}} c_i dP$$
 
$$ = \sum_i c_i P(\{\omega \in F | X(\omega) \in A_i\})$$
 
We can re-express  $P(\{\omega \in F \| X(\omega) \in A_i\})$ using the pushforward measure $X^{-1} \circ P$ on $B$:

$$ = \sum_i c_i (X^{-1} \circ P)(A_i)$$

$$ = \int_{R} g d(X^{-1} \circ P)$$

We have thus far been assuming that $g$ is a simple function, but by the simple function approximation lemma any measurable function $g$ can be approximated arbitrarily well by simple functions.  Therefore there exists a sequence of simple functions $g_n$ such that $lim_{n \rightarrow \infty} g_n = g$.  Thus by the monotone convergence theorem we have that:

$$
lim_{n \rightarrow \infty} \int_{\Omega} g_n(X(\omega)) dP = \int_{\Omega} lim_{n \rightarrow \infty}  g_n(X(\omega)) dP
$$

$$
= \int_{\Omega} g(X(\omega)) dP
$$

$$
= lim_{n \rightarrow \infty} \int_{R} g_n d(X^{-1} \circ P) = \int_{R} lim_{n \rightarrow \infty} g_n d(X^{-1} \circ P)
$$

$$
= \int_{R} g d(X^{-1} \circ P)
$$

And therefore the result holds for all positive measurable $g$ in $L^1 (X^{-1} \circ P)$.  We can extend the result to all measurable functions in $L^1 (X^{-1} \circ P)$ by taking an arbitrary positive and/or negative function, decomposing it into it's positive and negative parts, and following the same process.

## Recovering the Continuous Case

The general LOTUS looks quite dissimilar to the continuous random variable LOTUS stated above, but we can recover the latter without too much work.

We assume that $X$ was a real valued continuous random variable, so we can say that: $X:(\Omega, F, P) \rightarrow (R, B, \lambda)$ where we now fix $R$ as the reals, $B$ as the Borel sigma algebra of $\mathbb{R}$, and $\lambda$ as the Lebesque measure.  We are also assuming via the "continuous" designation that the distribution of $X$ - a.k.a. the pushforward measure $X^{-1} \circ P$ on $R$ - is absolutely continuous with respect to the ("reference measure") $\lambda$.  

These assumptions allow us to do a little bit more with the pushforward measure $X^{-1} \circ P$ of $X$.  In particular, the Radon-Nikodym theorem gives us by the absolute continuity of $X^{-1} \circ P$ with respect to $\lambda$ that there exists a measurable function $f: R \rightarrow \mathbb{R}$ such that:

$$
(X^{-1} \circ P)(A_i) = \int_{A_i} f d\lambda
$$

This function is indeed the density function $f_X$.  Above, when we assumed $g$ to be a simple function we got to:

$$E[g(X)] = \sum_i c_i (X^{-1} \circ P)(A_i)$$

Using our new assumptions yields:

$$= \sum_i c_i \int_{A_i} f d\lambda $$

$$ = \sum_i \int_{A_i} c_i f d\lambda = \int_{R} g f d\lambda = \int_{R} g(x) f_X(x) dx $$

That formula looks familiar!

## Recovering the Discrete Case

Now suppose that $X$ is a discrete random variable.  Then we assume $R$ to be countable.  Set $B$ to be the power set of $R$ (which is indeed a sigma algebra), and $\mu$ the counting measure defined on $B$ (i.e. $\mu(A_i) = \|A_i\|$).  Then we have that the induced measure $X^{-1} \circ P$ is absolutely continuous with respect to $\mu$, and therefore by Radon-Nikodym we have that $(X^{-1} \circ P)(A_i) = \int_{A_i} f d \mu$.  The function $f$ is the probability mass function of $X$.  Therefore, $\int_{A_i} f d \mu = \sum_{x \in A_i} f(x)$.  Then, as above:

$$
E[g(X)] = \sum_i c_i (X^{-1} \circ P)(A_i)
$$

$$
= \sum_i c_i \int_{A_i} f d \mu
$$

$$
= \sum_i c_i \sum_{x \in A_i} f(x)
$$

$$
= \sum_i \sum_{x \in A_i} c f(x)
$$

$$
= \sum_{x \in R} g(x)f_X(x)
$$

## Conclusion

The general LOTUS is much stronger than the specific cases that we recovered as it doesn't require the random variable $X$ to be absolutely continuous (we don't need $f_X$ to exist), and it holds for all $L^1$ measurable functions $g$.  Of course, actually computing $E[g(X)]$ for an "exotic" $X$ might be quite difficult.

## References

Rinaldo, A. (2018). Limit Theorems and the Standard Machinery https://www.stat.cmu.edu/~arinaldo/Teaching/36752/S18/Notes/lec_notes_3.pdf


