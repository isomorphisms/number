# Masanori Morishita — *Knots and Primes: An Introduction to Arithmetic Topology*

## Source

Masanori Morishita, *Knots and Primes: An Introduction to Arithmetic Topology*, Universitext, Springer.

- Second edition (2024): https://doi.org/10.1007/978-981-99-9255-3
- First English edition (2012): https://doi.org/10.1007/978-1-4471-2158-9

Thank you to Masanori Morishita for developing arithmetic topology into a systematic subject and for writing a book that makes the analogy usable rather than merely suggestive.

The **2024 second edition** should be the primary reference here. It corrects and updates the first edition and adds two substantial topics: idelic class field theory for 3-manifolds and number fields, and topological/arithmetic Dijkgraaf–Witten theory.

These notes are a guide to ideas and connections, not a reproduction of the book.

## Central dictionary

The organizing principle is that arithmetic of number fields behaves in strikingly parallel ways to topology of knots and 3-manifolds.

| Topology | Arithmetic |
| --- | --- |
| oriented closed 3-manifold | ring of integers of a number field |
| knot | prime ideal |
| link | finite set of primes |
| knot/link complement | arithmetic object with selected primes removed |
| fundamental group | Galois group |
| covering space | field extension |
| branched covering along knots | extension ramified at primes |
| linking number | quadratic / power residue symbol |
| homology | ideal class group |
| Alexander module | Iwasawa module |
| Milnor invariants | higher residue symbols |
| Reidemeister torsion / Alexander-type data | Iwasawa-theoretic torsion and p-adic arithmetic data |

The point is not that every entry is a literal equality. The analogy becomes precise only after choosing the correct topological and arithmetic categories, completions, and ramification conditions. Morishita's book is valuable because it develops those qualifications rather than stopping at a slogan.

## Why this belongs in `number`

This repository already approaches algebraic number theory geometrically through ideals as lattices. Morishita pushes the same instinct much further:

```text
integer arithmetic
    -> ideals and primes
    -> decomposition / ramification
    -> Galois groups
    -> topology of complements and covers
    -> knot and 3-manifold invariants
```

This gives a second geometric spine for the repository:

1. **lattice geometry** for ideals and embeddings;
2. **3-dimensional topology** for primes, ramification, and Galois theory.

The two viewpoints should eventually meet rather than live in separate note files.

## Route through the book

A useful first pass is not necessarily linear.

### 1. Establish the dictionary

Start with the chapters comparing knots with primes and 3-manifolds with number rings. The basic question is:

> What arithmetic construction plays the role of deleting a knot, taking a cover, or allowing ramification along it?

That question organizes much of the later material.

### 2. Linking numbers and residue symbols

This is probably the cleanest first nontrivial example.

For distinct knots (K_1,K_2), the linking number records how one winds around the other. On the arithmetic side, quadratic and higher power residue symbols record reciprocal information between primes.

Gauss reciprocity is therefore not just an isolated congruence theorem in this viewpoint; it has the flavor of a symmetry law for linking.

### 3. Homology and ideal class groups

The class group should be read topologically rather than merely as a bookkeeping device for failure of unique factorization.

The rough analogy pairs the first homology group of a 3-manifold with the ideal class group of a number field, with suitable choices of the topological object and arithmetic setting.

This is particularly relevant to the earlier Billy Woods notes: the class group first appears there through ideal arithmetic; Morishita gives a second interpretation through 3-manifold topology.

### 4. Link groups and restricted ramification

A link complement has a fundamental group whose peripheral structure remembers the removed components.

Arithmetic analogues use Galois groups of extensions with ramification restricted to a chosen finite set of primes.

This is one of the places where the analogy stops being pictorial and becomes structural.

### 5. Milnor invariants and higher residue symbols

Pairwise linking is not enough to distinguish links. Milnor invariants detect higher-order linking.

Arithmetic topology seeks corresponding higher residue symbols. This suggests an important programming principle: do not design the arithmetic-topology layer around pairwise relations only. Higher-arity invariants belong in the model from the beginning.

### 6. Alexander modules and Iwasawa modules

This is one of the strongest bridges in the book.

Infinite cyclic covers and Alexander theory on the knot side correspond to towers of number fields and Iwasawa modules on the arithmetic side.

In this dictionary, Alexander theory on the topological side plays the role of Iwasawa theory on the arithmetic side.

This is likely the point where the repository should eventually connect arithmetic topology to any existing work on (p)-adic numbers, towers, and completed group rings.

### 7. Torsion and the Iwasawa main conjecture

Topological torsion invariants and arithmetic characteristic ideals / (p)-adic (L)-data become parallel objects.

This is conceptually important because it shows that the analogy is not limited to elementary knot pictures. It reaches major structural theorems in modern number theory.

### 8. Representation spaces and deformations

The book compares representation spaces of knot and prime groups and then places deformations of hyperbolic structures beside (p)-adic deformations of modular forms.

That is especially relevant to this repository's broader geometric bias: arithmetic moduli should be treated as spaces with deformation theory, not only as sets of symbolic solutions.

### 9. New material in the second edition

The second edition adds:

- **idelic class field theory for 3-manifolds and number fields**;
- **Dijkgraaf–Witten theory for 3-manifolds and number rings**.

The latter is especially interesting because it extends the bridge toward mathematical physics and topological field theory.

## Questions to keep alive

- Can the knot/prime dictionary be expressed as actual typed interfaces rather than prose analogies?
- Which constructions are genuinely functorial on both sides?
- Can ramification data be represented like peripheral structure on a link complement?
- Can higher residue symbols and Milnor invariants share one abstract higher-linking interface?
- Can Alexander and Iwasawa modules be exposed through one common module-over-a-completed-group-ring abstraction?
- Where does the analogy fail, and can those failures themselves be useful invariants?
- How should arithmetic Dijkgraaf–Witten theory connect to gauge-theoretic code elsewhere?

## Immediate cross-links

When this repository grows, this note should be cross-linked with material on

- class field theory;
- (p)-adic numbers and Iwasawa theory;
- Galois groups;
- knot groups and 3-manifold topology;
- gauge theory and representation varieties;
- Dijkgraaf–Witten theory.

