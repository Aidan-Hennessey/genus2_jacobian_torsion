# Torsion of Jacobians of genus 2 curves over number fields

This repo contains a file featuring a function TorsionSubgroup, which takes in a Jacobian
J of a genus 2 curve over a number field K, and returns an abstract abelian group A isomorphic
to J(K)_tors, together with an embedding of A into J(K).

The function assumes that the ground field of your Jacobian has monic defining polynomial,
and that your the genus 2 curve is in the form y^2 = f(x) for f a polynomial of degree 5 or 6
with (algebraically) *integral* coefficients. The function **does not check to ensure these 
conditions are met.**

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
