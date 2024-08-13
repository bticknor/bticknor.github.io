# A Proof That Sigma Fields Cannot be Countably Infinite

This is a classic result from measure theory, but the proofs that I have been able to find online up to this point are a little terse and hard to follow (in my opinion).  Therefore, here is a meticulous (read: too long and wordy) proof of the result.


**Theorem**: A sigma field cannot be countably infinite, it must be either finite or have an uncountably large cardinality.

**Proof**: Let $X$ be a set and $S$ be a sigma field over $X$.  If $X$ is finite, then the cardinality of the power set of $X$ is $2^{\|X\|}$, and it must be that $\|S\| < 2^{\|X\|}$ and is therefore finite.  Assume therefore that $X$ is not finite, and suppose for the sake of contradiction that $S$ is countably infinite.  Then we can write $S = {A_i}_{i \in \mathbb{N}}$.  Define the following function:

$$
    f(x) = \cap_{A_i: x \in A_i} A_i
$$

We see that this function maps each element of $X$ to a countable intersection of elements of $S$, and so $f:X \rightarrow S$.  We proceed with a lemma.


**Lemma**: If $f(x) \cap f(y) \neq \emptyset$, then $f(x) = f(y)$.


**Proof**: Suppose that $x, y \in X$ with $x \neq y$, and that $f(x) \cap f(y) \neq \emptyset$.  Let $C = f(x) \cap f(y)^c$, and notice that $C \in S$.  If we assume that $x \notin f(y)$, then $C \subset f(x)$ is a smaller set than $f(x)$ in $S$ that contains $x$.  This contradicts the definition of $f$, and therefore it must be that $x \in f(y)$.  It follows that $f(x) \subseteq f(y)$ - if there were some $z$ such that $z \in f(x)$ and $z \notin f(y)$, this would imply that there is a set $A_i \in S$ containing $x$ but not $z$, which contradicts the definition of $f(x)$.  A symmetric argument yields that $f(y) \subseteq f(x)$, and so $f(x) = f(y)$.  Therefore $f(x) \cap f(y) \neq \emptyset \implies f(x) = f(y)$.


Let $B = f(X)$, the image of $X$ under $f$.  Notice that we can express $S$ using $B$: $A_i = \cup_{x \in A_i} f(x) = \cup_{\theta_i} B_{\theta_i}$.  Therefore, if we assume that $B$ is finite, then there are at most $2^{\|B\|}$ possibilities for any given $A_i$ and so $S$ is finite.  If we instead assume that $B$ is uncountably infinite, then since $B \subset S$ we have that $S$ is uncountably infinite.  Therefore it must be that $B$ is countably infinite.

The lemma above gives us that the unique elements of $B$ are disjoint, and so $B_i \cup B_j \notin B$ for $i \neq j$.  Furthermore, for any subsets $I,J \subset \mathbb{N}^+$ with $I \neq J$, $\cup_{i \in I} B_i \neq \cup_{j \in J} B_j$.  In other words, if we take unique (with respect to index) unions of sets in $B$, we end up with unique sets.  Therefore, the set of all countable unions of $B_i$ has the same cardinality as the power set of $B$, which by Cantor's theorem is uncountably large.  However, $\cup_{i \in I} B_i \in S$ for any $I \subset \mathbb{N}^+$, and so $S$ has an uncountably large cardinality.

Therefore $S$ must be either finite or uncountably large.




