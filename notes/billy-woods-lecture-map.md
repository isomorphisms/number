# Billy Woods ANT lecture map

Source course:

- https://billywoods.net/ANT.html
- https://www.youtube.com/playlist?list=PLSibAQEfLnTwq2-zCB-t9v2WvnnVKd0wn

Billy Woods's teaching page says his channel currently contains 18 videos comprising most of the informal course. That does **not** by itself imply that the course has ANT01 through ANT18. At present, ANT01 and ANT15 are directly verified, while ANT15 itself explicitly refers back to videos 9, 10, and 11.

This file therefore separates **confirmed metadata** from **cross-referenced topic information**.

## Confirmed

### ANT01

**Algebraic number theory: an introduction, via Fermat's last theorem**

https://www.youtube.com/watch?v=1f0-pc9zYPQ

Verified topics from the transcript:

- Euclidean algorithm in \(\mathbb Z\);
- Bézout and Euclid's lemma;
- unique factorization;
- Gaussian integers \(\mathbb Z[i]\);
- Eisenstein integers \(\mathbb Z[\omega]\);
- Pythagorean triples via factorization in \(\mathbb Z[i]\);
- Fermat exponent \(3\) via \(\mathbb Z[\omega]\).

### ANT15

**p-adic integers: a primer, and an application (part 1)**

https://www.youtube.com/watch?v=SwbJmKbFo7o

Verified topics from the transcript:

- modular obstructions to Diophantine equations;
- Chinese remainder theorem;
- organization by prime powers;
- \(p\)-adic integers as compatible prime-power data;
- base-\(p\) expansions;
- negative and rational \(p\)-adic examples;
- \(p\)-adic valuation;
- Hensel's lemma;
- square roots in \(\mathbb Z_p\);
- local analysis of sums of three squares;
- the \(2\)-adic obstruction visible modulo \(8\).

## Confirmed by ANT15 cross-reference

These topic identifications come from ANT15's own references to earlier videos. Exact titles and URLs remain to be recovered.

### ANT09

ANT15 says that video 9 studied

\[
6y^2=x(x+1)(x+2),
\]

split possibilities according to where factors \(2\) and \(3\) occur, and eliminated cases by congruence arguments.

This makes ANT09 a useful source for the progression

\[
\text{integer equation}
\to
\text{factor bookkeeping}
\to
\text{local congruence obstruction}.
\]

### ANT10

ANT15 refers to video 10 for **division in modular arithmetic**.

The relevant conceptual boundary is:

- addition and multiplication always descend modulo \(m\);
- division requires the divisor to be a unit modulo \(m\);
- modulo a prime \(p\), every nonzero residue is invertible;
- modulo composite \(m\), zero divisors obstruct naive division.

This is likely the bridge into viewing \(\mathbb Z/p\mathbb Z\) as a field and into prime-power arithmetic.

### ANT11

ANT15 refers to video 11 for the **Legendre symbol**, used to determine whether a nonzero residue is a square modulo an odd prime.

For \(p\nmid a\),

\[
\left(\frac ap\right)
=
\begin{cases}
1,&a\text{ is a square mod }p,\\
-1,&a\text{ is a nonsquare mod }p.
\end{cases}
\]

ANT15 then combines this with Hensel lifting: for odd \(p\), a \(p\)-adic unit is a square in \(\mathbb Z_p\) precisely when its reduction modulo \(p\) is a square.

That is a clean example of information being promoted from a finite field to a local ring.

## Course-level structure visible already

Even without the exact titles of every middle lecture, the verified material shows a coherent arc:

\[
\begin{array}{c}
\text{factorization over }\mathbb Z\\
\downarrow\\
\text{enlarge rings to factor equations}\\
\downarrow\\
\text{study primes, units, ideals, and failure of UFD}\\
\downarrow\\
\text{finite residue rings and quadratic residues}\\
\downarrow\\
\text{prime-power towers}\\
\downarrow\\
\mathbb Z_p\text{ and local solvability}.
\end{array}
\]

Woods's official course page also explicitly displays ideal LCMs as lattice intersections, confirming that ideals/lattice geometry belongs to the middle of this conceptual arc even though the exact video metadata has not yet been recovered here.

## Notes connected to this map

- [Main Woods notes](billy-woods-ant.md)
- [Ideals as lattices](ideals-as-lattices.md)
- [p-adic towers](p-adic-towers.md)

## Retrieval status

- [x] ANT01 exact metadata and transcript
- [x] ANT15 exact metadata and transcript
- [x] ANT09 topic cross-reference
- [x] ANT10 topic cross-reference
- [x] ANT11 topic cross-reference
- [ ] recover exact ANT02–ANT14 titles and URLs
- [ ] determine whether ANT15 is currently the last numbered ANT lecture
- [ ] extract the middle-course ideal/class-group material directly from Woods
- [ ] attach exact video links to every lecture note

Do not fill the missing slots by guessing from a standard algebraic-number-theory syllabus.
