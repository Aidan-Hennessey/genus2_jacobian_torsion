# Torsion of Jacobians of genus 2 curves over number fields

This repo contains a file featuring a function TorsionSubgroup, which takes in a Jacobian
$J$ of a genus 2 curve over a number field $K$, and returns an abstract abelian group $A$ isomorphic
to $J(K)_{\rm tors}$, together with an embedding of $A$ into $J(K)$.

The function assumes that the ground field of your Jacobian has monic defining polynomial,
and that your the genus 2 curve is given by a model of the form $y^2 = f(x)$ for $f$ a polynomial 
of degree 5 or 6 with (algebraically) *integral* coefficients. The function **does not check to 
ensure these conditions are met.**

To compute the torsion subgroup over an extension of the field of definition, run something like this:
```
_<x> := PolynomialRing(Rationals());
f := x^6 + 2x + 2;
C := HyperellipticCurve(f);
J := Jacobian(C);
K := NumberField(x^2-5);

JK := BaseChange(J, K);
TorsionSubgroup(JK);
```

Based on (limited) speed testing, the function seems to take a few tenths of a second for reasonable examples.
There are some optimizations left to make; these are highlighted in inline comments. The function is based on 
the existing algorithm to compute the torsion subgroup over $\mathbb{Q}$. An outline of that algorithm can be found in 
[this paper](http://matwbn.icm.edu.pl/ksiazki/aa/aa90/aa9026.pdf) of Stoll.

Code to compute the same thing can also be found in [this repo](https://github.com/MaxPosthumus/MasterProject/tree/main). 
That implementation corresponds to [Max Posthumus's masters thesis](https://fse.studenttheses.ub.rug.nl/31630/1/mMATH_2023_PosthumusM.pdf). My implementation was developed without knowledge of Posthumus's work.

Various small snippets of this code were written with the help of AI. Such snippets are identified
in inline comments.
