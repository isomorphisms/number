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


## ANT03 — Ideal factorisation: recovering uniqueness

Video: https://www.youtube.com/watch?v=jE7pxr1nzfc

The full transcript makes Woods's geometric program much more explicit than the course-page caption alone.

### Ideals begin as pictures of divisibility

Woods opens with ordinary integers:

\[
4\mathbb Z\cap 6\mathbb Z=12\mathbb Z.
\]

This says both \(\operatorname{lcm}(4,6)=12\) and, through containment,

\[
12\mathbb Z\subseteq4\mathbb Z
\quad\Longleftrightarrow\quad
4\mid12.
\]

So divisibility becomes containment of lattices/subgroups, with the direction reversed.

He then defines ideals and immediately draws the ideal generated by \(2+i\) inside \(\mathbb Z[i]\). The point is visual before it is categorical: multiplication by every ring element fills out a sublattice.

Ideals also **forget units**. For example,

\[
2\mathbb Z=(-2)\mathbb Z
\]

and in the Gaussian integers \((4)=(4i)\). Principal ideals therefore behave like elements modulo associates.

### Ideal arithmetic: LCM, product, GCD

Woods gives three distinct operations. Intersection behaves like least common multiple,

\[
(4)\cap(6)=(12),
\]

ideal multiplication extends ordinary multiplication,

\[
(4)(6)=(24),
\]

and the ideal sum is the smallest ideal containing both ideals. In \(\mathbb Z\),

\[
(4)+(6)=(2).
\]

Woods ties this directly to Bézout and the gcd. Thus

\[
I+J \leftrightarrow \gcd,
\qquad
I\cap J \leftrightarrow \operatorname{lcm}.
\]

His motivating interpretation of a nonprincipal ideal is essentially a **gcd that should exist but is not represented by any single element of the ring**.

### Repairing \(\mathbb Z[\sqrt{-5}]\)

The familiar failure

\[
6=2\cdot3=(1+\sqrt{-5})(1-\sqrt{-5})
\]

has two genuinely different factorizations into irreducible elements.

Woods passes to principal ideals and then forms ideal sums such as

\[
\mathfrak p_1=(2,1+\sqrt{-5}).
\]

The new prime ideals provide the missing finer factors. Apparently different generated ideals can coincide, and their products recover the original principal ideals.

The conceptual point is:

> ideal factorization does not deny the two element factorizations; it refines both into a deeper common factorization.

### Dedekind domains

Woods identifies the number rings under discussion as Dedekind domains and frames ideal theory as adjoining the missing gcds required to recover the familiar multiplicative laws.

At the ideal level one recovers analogues of gcd, prime factorization, Euclid's lemma, and unique factorization. If every ideal is principal, this collapses back to unique factorization of elements up to units. This explains retrospectively why \(\mathbb Z[i]\) and \(\mathbb Z[\omega]\) behaved so cleanly.

### Splitting of rational primes in \(\mathbb Z[\sqrt{-5}]\)

Woods gives a concrete table and summarizes the pattern:

- \(2\) and \(5\) ramify;
- primes congruent to \(1,3,7,9\pmod{20}\) split;
- primes congruent to \(11,13,17,19\pmod{20}\) remain inert.

He also records

\[
N(a+b\sqrt{-5})=a^2+5b^2
\]

and that the units are \(\pm1\).

This is immediately visualizable: one rational prime enters the quadratic lattice and either remains one prime ideal, splits into two, or becomes a repeated prime ideal.

### Diophantine example and the obstruction that remains

Woods studies

\[
y^3=x^2+5.
\]

Factoring gives

\[
y^3=(x+\sqrt{-5})(x-\sqrt{-5}).
\]

Element-level unique factorization is unavailable, so he passes to ideals. Coprimality plus unique ideal factorization gives an ideal \(\mathfrak a\) with

\[
\mathfrak a^3=(x+\sqrt{-5}).
\]

The right-hand side is principal. The new question is:

> if a power of an ideal is principal, must the ideal itself be principal?

No in general. That is precisely the phenomenon for which ideal classes are needed. ANT03 ends at this boundary and says the next video will address it.

So the narrative moves from

\[
\text{failure of element factorization}
\to
\text{unique ideal factorization}
\to
\text{principal versus nonprincipal ideal classes}.
\]

That is a much sharper route into the class group than introducing \(\operatorname{Cl}(R)\) as an unexplained quotient.

### Direct visualization targets from ANT03

1. Animate \(4\mathbb Z\), \(6\mathbb Z\), their intersection \(12\mathbb Z\), and their generated sum \(2\mathbb Z\).
2. Draw \((2+i)\subset\mathbb Z[i]\) and its intersection with \((2-i)\).
3. Show why multiplying a generator by a unit leaves the same ideal lattice.
4. Draw the hidden prime-ideal factors behind the two factorizations of \(6\) in \(\mathbb Z[\sqrt{-5}]\).
5. Animate rational-prime behavior as **split / inert / ramified**.
6. Represent ideal classes as equivalence classes of lattice shapes under multiplication by field elements.
7. Show \(\mathfrak a^3\) landing in the principal class even when \(\mathfrak a\) itself does not.


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
- [Class groups from ideal powers](class-groups-from-ideal-powers.md)
- [\(p\)-adic towers and compatible roots](p-adic-towers.md)
