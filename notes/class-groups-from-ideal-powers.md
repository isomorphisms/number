# Class groups from powers of ideals

This note starts exactly where Billy Woods leaves ANT03.

Primary source:

- Billy Woods, **[ANT03] Ideal factorisation: recovering uniqueness**  
  https://www.youtube.com/watch?v=jE7pxr1nzfc

Standard background checked against:

- Keith Conrad, notes on ideal class groups and \(\mathbb Q(\sqrt{-5})\):  
  https://kconrad.math.uconn.edu/blurbs/gradnumthy/classgroupKronecker.pdf
- William Stein, *Algebraic Number Theory, a Computational Approach*:  
  https://www.williamstein.org/books/ant/

Thank you to Billy Woods, Keith Conrad, and William Stein for making these expositions available.

## 1. The exact problem ANT03 leaves behind

Woods factors the Diophantine equation

\[
y^3=x^2+5
\]

inside

\[
R=\mathbb Z[\sqrt{-5}].
\]

After passing from elements to ideals, unique ideal factorization gives an ideal \(\mathfrak a\) such that

\[
\mathfrak a^3=(x+\sqrt{-5}).
\]

The right side is principal.

The question at the end of ANT03 is therefore:

\[
\mathfrak a^3\text{ principal}
\quad\Longrightarrow\quad
\mathfrak a\text{ principal?}
\]

Not in general.

This is the precise point at which unique factorization of ideals stops being enough. We need to remember **which ideals differ from principal ideals, and by how much**.

## 2. Fractional ideals form a group

In a Dedekind domain \(R\), nonzero fractional ideals form an abelian group under ideal multiplication.

Write this group as

\[
I(R).
\]

Principal fractional ideals form a subgroup

\[
P(R)
=
\{(\alpha):\alpha\in K^\times\},
\]

where \(K\) is the fraction field of \(R\).

The ideal class group is

\[
\operatorname{Cl}(R)
=
I(R)/P(R).
\]

So two fractional ideals \(I,J\) represent the same class exactly when

\[
I=\alpha J
\]

for some nonzero \(\alpha\in K\).

This is the algebraic version of the lattice picture:

> ideal lattices are identified when one is obtained from the other by multiplication by a field element.

The identity element is the class of principal ideals.

## 3. ANT03 becomes one line in the class group

If

\[
\mathfrak a^3
\]

is principal, then in the class group

\[
[\mathfrak a]^3=1.
\]

So Woods's obstruction is not vague. The class

\[
[\mathfrak a]
\]

must be a torsion element whose order divides \(3\).

If the class group has no nontrivial \(3\)-torsion, then

\[
[\mathfrak a]^3=1
\quad\Longrightarrow\quad
[\mathfrak a]=1,
\]

hence \(\mathfrak a\) is principal.

This is the missing logical step that lets an ideal-theoretic solution descend back to an element-theoretic one.

For a general exponent \(n\),

\[
\mathfrak a^n\text{ principal}
\quad\Longleftrightarrow\quad
[\mathfrak a]^n=1.
\]

Thus a Diophantine proof can reduce to a statement about the \(n\)-torsion of a finite abelian group.

## 4. Why the class group measures failure of unique factorization

For rings of integers of number fields,

\[
\operatorname{Cl}(R)=1
\]

if and only if every nonzero ideal is principal.

In a Dedekind domain this is equivalent to \(R\) being a PID, hence a UFD.

So

\[
\operatorname{Cl}(R)=1
\]

means element factorization behaves as well as ideal factorization.

A nontrivial class group records the obstruction to choosing an element generator for every ideal.

This gives a better hierarchy than the loose phrase "how badly factorization fails":

\[
\text{unique ideal factorization}
\]

always survives in the Dedekind setting, while

\[
\text{class group}
\]

measures the obstruction to collapsing those ideal factors back to element factors.

## 5. The Woods example \(\mathbb Z[\sqrt{-5}]\)

Let

\[
R=\mathbb Z[\sqrt{-5}].
\]

ANT03 introduces the ideal

\[
\mathfrak p=(2,1+\sqrt{-5}).
\]

Woods shows in the hidden factorization of \(6\) that the relevant two ideals above \(2\) coincide, so

\[
(2)=\mathfrak p^2.
\]

Therefore

\[
[\mathfrak p]^2=1
\]

in the class group.

But \(\mathfrak p\) is not principal. One quick norm argument is that if

\[
\mathfrak p=(a+b\sqrt{-5}),
\]

then its norm would force

\[
a^2+5b^2=2,
\]

which has no integer solution.

Thus \([\mathfrak p]\neq1\) but

\[
[\mathfrak p]^2=1.
\]

In fact,

\[
\operatorname{Cl}(\mathbb Z[\sqrt{-5}])
\cong
\mathbb Z/2\mathbb Z.
\]

Geometrically, there are two ideal-lattice classes up to multiplication by nonzero field elements:

1. the principal class;
2. one nonprincipal class.

This is exactly the kind of picture Woods's lattice presentation makes unusually concrete.

## 6. A multiplication table worth rendering

For class number \(2\), the entire group law is

| \(\cdot\) | \(1\) | \(c\) |
|---|---|---|
| \(1\) | \(1\) | \(c\) |
| \(c\) | \(c\) | \(1\) |

where

\[
c=[\mathfrak p].
\]

The visual version should not just draw this table.

Draw representative lattices and animate:

\[
\mathfrak p\cdot\mathfrak p=(2).
\]

The product of two nonprincipal representatives lands back in the principal class.

That is the class-group law made visible.

## 7. Principalization as a dynamical picture

Given an ideal class \(c\), display the sequence

\[
1,c,c^2,c^3,\ldots.
\]

The first return to \(1\) is the order of the class.

For an ideal \(\mathfrak a\),

\[
\operatorname{ord}([\mathfrak a])
=
\min\{n>0:\mathfrak a^n\text{ is principal}\}.
\]

This is exactly the invariant ANT03 is asking for at the end.

For the \(\mathbb Z[\sqrt{-5}]\) nonprincipal class,

\[
c^0=1,\quad
c^1=c,\quad
c^2=1,\quad
c^3=c,\ldots
\]

For a Diophantine argument involving cubes, this immediately tells us that the only class satisfying

\[
c^3=1
\]

is \(c=1\), since the class group has order \(2\).

Therefore any ideal \(\mathfrak a\) with \(\mathfrak a^3\) principal must itself be principal.

That is exactly the condition Woods needs for the equation in ANT03.

## 8. The general computational boundary

A useful API should distinguish at least:

    Ideal
    FractionalIdeal
    PrincipalIdeal
    IdealClass
    ClassGroup

with maps

\[
\operatorname{class}:I(R)\to\operatorname{Cl}(R)
\]

and

\[
\operatorname{principal}:\ K^\times\to I(R).
\]

Important executable laws:

\[
[IJ]=[I][J],
\]

\[
[(\alpha)]=1,
\]

\[
[I]=1
\Longleftrightarrow
I\text{ is principal},
\]

and

\[
[I]^n=1
\Longleftrightarrow
I^n\text{ is principal}.
\]

Do not represent an ideal class by a single preferred ideal unless a reduction algorithm has actually chosen one. The quotient is the object; a representative is data attached to it.

## 9. Connection to lattices and Minkowski geometry

An ideal in a number field becomes a lattice under the Minkowski embedding.

Passing to an ideal class identifies lattices that differ by multiplication by a nonzero field element.

This suggests a useful visual hierarchy:

\[
\text{ideal}
\longrightarrow
\text{embedded lattice}
\longrightarrow
\text{lattice orbit under }K^\times
\longrightarrow
\text{ideal class}.
\]

For imaginary quadratic fields, this has a classical geometric refinement: ideal classes are closely tied to equivalence classes of binary quadratic forms and to lattices in the complex plane up to the appropriate scaling/equivalence.

That connection deserves its own later note rather than being folded prematurely into ANT03.

## 10. Next source questions

The immediate source-spider targets are:

- recover the exact ANT04 title and transcript;
- check how Woods introduces the class group after the ANT03 question;
- see whether he develops class number through explicit quadratic examples;
- preserve any diagrams he uses for multiplication of ideal classes;
- compare his route with Conrad's \(\mathbb Q(\sqrt{-5})\) examples and Stein's computational presentation;
- then connect the finite class group to Minkowski's theorem and geometry of numbers.

The key conceptual chain is now explicit:

\[
\text{non-UFD}
\to
\text{ideals}
\to
\text{unique ideal factorization}
\to
\text{nonprincipal ideals}
\to
\text{ideal classes}
\to
\text{torsion}
\to
\text{Diophantine descent}.
\]
