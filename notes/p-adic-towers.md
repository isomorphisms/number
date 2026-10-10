# \(p\)-adic towers and compatible roots

This note develops the computational picture from Billy Woods's ANT15:

- Billy Woods, **[ANT15] p-adic integers: a primer, and an application (part 1)**
- https://www.youtube.com/watch?v=SwbJmKbFo7o

Thank you to Billy Woods.

Woods's presentation is especially useful because he motivates \(\mathbb Z_p\) from the tower of congruences before asking the viewer to think of \(p\)-adic integers as exotic numbers.

## 1. One prime, all powers

Fix a prime \(p\).

The data

\[
x_1\in\mathbb Z/p\mathbb Z,
\quad
x_2\in\mathbb Z/p^2\mathbb Z,
\quad
x_3\in\mathbb Z/p^3\mathbb Z,
\quad\ldots
\]

form a compatible tower when

\[
x_{n+1}\equiv x_n\pmod{p^n}.
\]

A \(p\)-adic integer is exactly such a compatible system:

\[
\mathbb Z_p
=
\varprojlim_n \mathbb Z/p^n\mathbb Z.
\]

For implementation, this definition is preferable to beginning with an infinite digit string.

A finite computation can store the truncation

\[
(x_1,\ldots,x_N)
\]

together with proofs/tests of compatibility.

## 2. Base-\(p\) digits are coordinates on the tower

A compatible residue modulo \(p^n\) determines the first \(n\) base-\(p\) digits.

Write

\[
x=a_0+a_1p+a_2p^2+\cdots
\]

with

\[
0\le a_k<p.
\]

Unlike ordinary decimal expansion, the sequence may continue indefinitely toward higher powers.

The visual model should show the equivalence between

    digits:    ... a3 a2 a1 a0

and

    mod p       x1
      ↑
    mod p²      x2
      ↑
    mod p³      x3
      ↑
      ...

The digits and inverse-limit tower are two views of the same object.

## 3. Negative integers are not exceptional

For example,

\[
-1
\]

has all digits \(p-1\):

\[
-1=(p-1)+(p-1)p+(p-1)p^2+\cdots
\]

in \(\mathbb Z_p\).

This is a useful first animation because it breaks the false intuition that infinitely many leftward digits imply "infinite size."

## 4. Valuation measures divisibility

For nonzero \(x\in\mathbb Z_p\),

\[
v_p(x)
\]

is the exponent of the first nonzero base-\(p\) digit, equivalently the largest \(k\) such that

\[
p^k\mid x.
\]

The associated absolute value is

\[
|x|_p=p^{-v_p(x)}.
\]

So divisibility by a large power of \(p\) means \(p\)-adic smallness.

Numbers are close when their difference is divisible by a large power of \(p\).

A renderer should therefore avoid a Euclidean number line. A rooted tree is more faithful.

## 5. The residue tree

At level \(n\), create one node for each class modulo \(p^n\).

A node \(a\bmod p^{n+1}\) connects to

\[
a\bmod p^n.
\]

Every node has \(p\) children.

An element of \(\mathbb Z_p\) is an infinite path from the root.

At finite depth \(N\), a computation sees a cylinder set: all \(p\)-adic integers sharing the first \(N\) digits.

This representation makes the topology visible.

## 6. Hensel lifting as branch selection

Suppose

\[
f(a_1)\equiv0\pmod p
\]

and the root is simple:

\[
f'(a_1)\not\equiv0\pmod p.
\]

Hensel's lemma gives a unique compatible lift

\[
a_1
\leftarrow
a_2
\leftarrow
a_3
\leftarrow\cdots
\]

with

\[
f(a_n)\equiv0\pmod{p^n}.
\]

Graphically:

1. draw the full residue tree;
2. mark roots of \(f\) at each level;
3. connect compatible roots;
4. highlight the unique branch selected by the simple root.

That picture directly explains what "a root in \(\mathbb Z_p\)" means.

## 7. Newton/Hensel computation

When division by \(f'(a)\) is valid \(p\)-adically, Newton iteration

\[
a_{\text{new}}
=
a-\frac{f(a)}{f'(a)}
\]

is the local computational mechanism behind rapid lifting.

For a deliberately elementary implementation, it is also possible to lift by trying the \(p\) candidates

\[
a+k p^n,\qquad k=0,\ldots,p-1
\]

and selecting the one satisfying

\[
f(a+kp^n)\equiv0\pmod{p^{n+1}}.
\]

That brute-force form is excellent for visualization because every child is visible.

## 8. Example: a square root of \(-1\) in \(\mathbb Z_5\)

Take

\[
f(x)=x^2+1.
\]

Modulo \(5\),

\[
2^2+1=5\equiv0\pmod5.
\]

Also

\[
f'(2)=4\not\equiv0\pmod5.
\]

So \(2\bmod5\) lifts uniquely to a root in \(\mathbb Z_5\).

At the next level test

\[
2+5k,\qquad k=0,1,2,3,4.
\]

The correct child modulo \(25\) is

\[
7,
\]

because

\[
7^2+1=50\equiv0\pmod{25}.
\]

Then continue modulo \(125\), \(625\), and so on.

This should be the first executable Hensel example.

## 9. Chinese remainder decomposition

Woods motivates concentrating on prime powers using the Chinese remainder theorem.

For coprime \(m,n\),

\[
\mathbb Z/(mn)\mathbb Z
\cong
\mathbb Z/m\mathbb Z
\times
\mathbb Z/n\mathbb Z.
\]

So a modulus

\[
N=\prod_i p_i^{e_i}
\]

splits into independent prime-power components.

Computationally this suggests two layers:

    global modulus N
        ↓ factor N
    prime-power components
        ↓
    p-adic towers

This is the bridge from elementary modular arithmetic to local arithmetic.

## 10. Local solvability versus global solvability

A global integer or rational solution gives compatible local solutions.

The converse is the interesting question.

The repository should distinguish:

- solution over \(\mathbb Z\);
- solution over \(\mathbb Q\);
- solution modulo \(p^n\);
- solution over \(\mathbb Z_p\);
- solution over \(\mathbb Q_p\);
- solution over \(\mathbb R\).

A local-global visualization can display one equation with a column for each completion.

This avoids treating "has a solution modulo every prime" as if it were automatically equivalent to "has an integer solution."

## 11. Three-square direction from ANT15

Woods uses \(p\)-adic solvability to analyze representations

\[
x^2+y^2+z^2=n.
\]

The striking structural point is that almost all odd primes cease to be the obstruction; the decisive restriction comes from the \(2\)-adic side, visible already modulo \(8\).

This is a good example of why local methods are not just an infinite pile of congruence checks. They *compress* the checks by prime and often isolate the one place where an obstruction lives.

## 12. Suggested data types

A first implementation could use conceptual types like

    Prime
    PrimePower
    ResidueClass(p, exponent)
    CompatibleTower(p, depth)
    PadicApproximation(p, precision)
    Polynomial
    LiftStep
    LocalSolution

with invariants:

\[
x_{n+1}\bmod p^n=x_n
\]

and, for root towers,

\[
f(x_n)\equiv0\pmod{p^n}.
\]

The finite-precision type should not claim to be an exact \(p\)-adic integer unless it carries a symbolic rule or a proof object for the infinite continuation.

That distinction matters.
