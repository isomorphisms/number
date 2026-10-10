# Billy Woods — *An unorthodox introduction to algebraic number theory*

## Source

William (Billy) Woods, University of Essex.

- Official course page: https://billywoods.net/ANT.html
- Teaching page: https://billywoods.net/teaching.html
- YouTube playlist: https://www.youtube.com/playlist?list=PLSibAQEfLnTwq2-zCB-t9v2WvnnVKd0wn

Thank you to Billy Woods for making this material freely available.

Woods describes the series as deliberately nonstandard: advanced material presented for intuition and motivation, leaning on examples, diagrams, and discussion rather than a complete rigorous development. He lists modular arithmetic and complex numbers as the main mathematical prerequisites. His teaching page currently describes the course as comprising most of an 18-video channel.

That makes the series especially valuable here as a **source of pictures and organizing ideas**, not as a substitute for a conventional reference.

## Central geometric idea

One of Woods's own illustrations is least common multiples of ideals as intersections of lattices.

That should be treated as a central design clue.

For quadratic integer rings, an ideal is simultaneously

1. an algebraic object;
2. an additive subgroup;
3. after choosing an embedding/basis, a lattice in the plane.

Then ideal arithmetic acquires geometry:

- inclusion becomes containment of lattices;
- intersection becomes a visibly computable lattice operation;
- index becomes area/covolume;
- multiplication changes scale and orientation according to the ring multiplication;
- principal ideals can be seen as multiplication images of the ambient lattice.

This is the kind of algebra-to-geometry bridge worth preserving in code.

---

## ANT01 — Algebraic number theory: an introduction, via Fermat's last theorem

Video: https://www.youtube.com/watch?v=1f0-pc9zYPQ

### Route through the lecture

Woods starts from the Euclidean algorithm in \(\mathbb Z\) and uses it to motivate the whole subject.

The basic chain is

\[
\text{division algorithm}
\Rightarrow
\text{Euclidean algorithm}
\Rightarrow
\gcd
\Rightarrow
\text{Bézout}
\Rightarrow
\text{Euclid's lemma}
\Rightarrow
\text{unique factorization}.
\]

The point is not merely that integers factor uniquely. The point is that the *mechanism* producing the multiplicative theory can survive in other rings.

### Gaussian and Eisenstein integers

Two first extensions are

\[
\mathbb Z[i]
\]

and

\[
\mathbb Z[\omega], \qquad \omega=e^{2\pi i/3}.
\]

Woods presents both geometrically.

- \(\mathbb Z[i]\) is the square lattice in the complex plane.
- \(\mathbb Z[\omega]\) is the triangular/hexagonal lattice.

Both admit Euclidean algorithms and hence unique factorization.

This is already a useful implementation boundary:

    Euclidean structure
        -> gcd
        -> coprimality
        -> factorization
        -> Diophantine argument

Do not encode the examples merely as abstract ring elements if a lattice realization is available.

### Pythagorean triples

Factor

\[
x^2+y^2=z^2
\]

inside \(\mathbb Z[i]\):

\[
(x+iy)(x-iy)=z^2.
\]

After the usual primitive/parity reductions, the two factors are coprime in the Gaussian integers. Unique factorization then forces one factor to be a square up to a unit, giving the classical parameterization

\[
x = \pm(d^2-e^2),\qquad
y = \pm 2de,\qquad
z = \pm(d^2+e^2).
\]

The important methodological point is that a Diophantine problem over \(\mathbb Z\) becomes easier after moving to a larger ring where the polynomial factors.

### Fermat exponent 3

The same idea is pushed into the Eisenstein integers for

\[
x^3+y^3=z^3.
\]

The prime above \(3\) and factorization in \(\mathbb Z[\omega]\) become the relevant arithmetic geometry.

So already in the first lecture the recurring pattern is:

    integer equation
        -> enlarge the ring
        -> factor geometrically/algebraically
        -> understand gcd / units / primes there
        -> pull the conclusion back to integers

That is a useful architecture for this repository.

### Visual experiments suggested by ANT01

1. Draw \(\mathbb Z[i]\) and \(\mathbb Z[\omega]\) side by side.
2. Animate multiplication by a Gaussian or Eisenstein integer as a lattice endomorphism.
3. Show norm as squared Euclidean length / area scaling.
4. Animate \(x^2+y^2=(x+iy)(x-iy)\) as the passage from an integer equation to conjugate lattice points.
5. Display prime behavior geometrically: inert, split, ramified.
6. Later replace principal-element pictures by ideal lattices so the picture continues after unique factorization of elements fails.

---

## Later arc: ANT15 — p-adic integers

Video: https://www.youtube.com/watch?v=SwbJmKbFo7o

By ANT15 the course has reached local arithmetic.

The motivating observation is familiar: if an integer equation has a solution, then it has a solution modulo every \(m\).

Woods then reorganizes the infinitely many congruence tests prime-by-prime.

### Chinese remainder theorem

For coprime \(m,n\),

\[
\mathbb Z/(mn)
\cong
\mathbb Z/m\times \mathbb Z/n.
\]

This lets composite moduli be assembled from prime-power information.

### Towers of prime powers

Fix a prime \(p\). Instead of treating

\[
\bmod p,\quad \bmod p^2,\quad \bmod p^3,\ldots
\]

as unrelated calculations, consider compatible solutions through the entire tower.

This leads naturally to

\[
\mathbb Z_p
=
\varprojlim_n \mathbb Z/p^n\mathbb Z.
\]

Woods motivates \(p\)-adic integers operationally: they package all compatible prime-power congruence information into a single number system.

### Hensel lifting

A simple root modulo \(p\) can often be lifted successively through higher powers of \(p\), yielding a root in \(\mathbb Z_p\).

This is another excellent computational picture:

    root mod p
       ↓
    root mod p²
       ↓
    root mod p³
       ↓
    ...
       ↓
    p-adic root

A visualization should show both the inverse-limit tree and the selected compatible branch.

### Local-versus-global question

The natural next question is one of the central questions of arithmetic:

> if an equation has solutions in every relevant local system, must it have a global rational/integer solution?

Sometimes yes; sometimes no.

That is the doorway from elementary congruence arguments into local-global principles, quadratic forms, Hasse principles, and their failures.

---

## Repository directions suggested by Woods

### 1. Arithmetic objects with geometric realizations

Avoid making every number-theoretic object a purely symbolic structure.

Useful realizations include:

- quadratic integer rings as planar lattices;
- ideals as sublattices;
- Minkowski embeddings as lattices in \(\mathbb R^r\times\mathbb C^s\);
- quotient rings as finite grids;
- \(p\)-adic approximation as trees/inverse systems.

### 2. Separate element factorization from ideal factorization

The failure of unique factorization of elements is not a dead end. Ideals restore a good factorization theory in rings of integers of number fields.

This distinction should be visible in both notes and code:

    Element
    Ideal
    PrincipalIdeal
    PrimeElement
    PrimeIdeal

with no accidental identification between the last two pairs.

### 3. Norms should connect algebra and geometry

For the Gaussian integers,

\[
N(a+bi)=a^2+b^2.
\]

More generally field/ideal norms, determinants, indices, and covolumes are related views of the same arithmetic data.

Those identifications are excellent candidates for executable invariants.

### 4. Local data should be first-class

Rather than treating modular calculations as disposable tricks, retain the system

\[
\mathbb Z/p^n\mathbb Z
\]

and the transition maps explicitly. Then \(\mathbb Z_p\) is not a mysterious new scalar type; it is the compatible limit of information already present.

---

## Source-spider ledger

Confirmed directly so far:

- [x] official ANT course page
- [x] official teaching page
- [x] playlist
- [x] ANT01 transcript/content
- [x] ANT15 transcript/content
- [x] add a verified lecture map without guessing missing titles
- [x] extract ideal/lattice geometry into a reusable note
- [x] extract the ANT15 \(p\)-adic tower/Hensel picture into a reusable note
- [x] record ANT09–ANT11 topic cross-references from ANT15
- [ ] recover exact ANT02–ANT14 titles and URLs
- [ ] take lecture-by-lecture notes for the middle lectures
- [ ] extract further diagrams worth reproducing
- [ ] cross-reference standard texts for proofs omitted in the informal course
- [ ] identify additional code-sized experiments from each lecture

The eventual lecture notes should distinguish three things clearly:

1. what Woods actually says;
2. standard mathematical background added here;
3. new visualization or implementation ideas inspired by the lecture.


## Split-out notes

- [Verified lecture map](billy-woods-lecture-map.md)
- [Ideals as lattices](ideals-as-lattices.md)
- [\(p\)-adic towers and compatible roots](p-adic-towers.md)
