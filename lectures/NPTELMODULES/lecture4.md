# Summary — Lecture 4
## First-Order Logic: Uniqueness, Equality, Substitution, Incidence Geometry & Logical Consequence

## 1. Unique existence (notation & meaning)

**Formula** ∃!x α(x) means there exists exactly one x with α(x).

**Equivalent expansion:**
```
∃x α(x) ∧ ∀x∀y((α(x) ∧ α(y)) → x = y)
```

(There is an x satisfying α, and if α holds for x and y then x = y.)

---

## 2. Negation of unique existence

**Negation** ¬(∃!x α(x)) is the disjunction of:

- **∀x ¬α(x)** — no x satisfies α; or
- **∃x∃y (α(x) ∧ α(y) ∧ x ≠ y)** — at least two distinct x, y satisfy α.

---

## 3. Equality predicate (special role)

Equality is a predicate with standard properties:

- **Reflexivity:** ∀x (x = x)
- **Substitutivity:** If x = y then any formula α(x) with free x implies α(y), provided substitution of y for x does not cause the new y to be captured by a quantifier.

---

## 4. Caution about substitution (variable capture)

Substitution must avoid capture by existing quantifiers.

**Example:**

- **Original:** ∀y (P(x) → Q(y)) with x free.
- **Substituting y for x naively gives:** ∀y (P(y) → Q(y)) — meaning changes (capture happened).

**Rule:** Always ensure the substituted variable remains free (not bound) unless intended.

---

## 5. Example vocabulary (geometry)

**Predicates:**
- P(x) = "x is a point" (unary)
- L(x) = "x is a line" (unary)
- O(x, y) = "x lies on y" (binary)

**Define three axioms** (set Γ = {P₁, P₂, P₃}):

- **P₁:** For all distinct points x, y there exists a unique line z with O(x, z) and O(y, z).
  - (Every pair of distinct points determines a unique line.)

- **P₂:** For every line z there exist distinct points x, y with O(x, z) and O(y, z).
  - (Every line has at least two distinct points.)

- **P₃:** There exist three distinct points w, x, y that are not all on the same line.
  - (There exist three non-collinear points.)

**Γ + logical consequences ≡ Incidence Geometry.**

---

## 6. Euclidean parallel property (statement)

**Informal:** Given line x and point y ∉ x, there exists a unique line z through y parallel to x (i.e., no point w lies on both x and z).

**First-order formulation:**
```
∀x∀y ((L(x) ∧ P(y) ∧ ¬∃w(O(y,x))) → 
      ∃!z (L(z) ∧ ¬∃w(O(w,x) ∧ O(w,z))))
```

(Negation expanded in lecture via De Morgan.)

---

## 7. Independence of Euclidean parallel property from Γ

The negation of Euclidean parallel property splits into two possibilities:

- **Elliptic parallel property:** No parallel exists through the point (no line through y that avoids intersection with x).
- **Hyperbolic parallel property:** More than one parallel exists through the point.

**Showing independence:** present models (interpretations) where Γ holds but Euclidean parallel property fails.

---

## 8. Models (interpretations) used in the lecture

### Model 1 (3 points A, B, C; 3 lines = pairs AB, BC, CA)

- **Points:** A, B, C
- **Lines:** {A, B}, {B, C}, {C, A}
- P₁, P₂, P₃ are true.
- **Euclidean parallel property:** false (elliptic behavior — no parallels)
- **Conclusion:** Euclidean parallel property is not a logical consequence of Γ.

### Model 2 (4 points A, B, C, D; lines = all 2-element subsets)

- **Points:** A, B, C, D
- **Lines:** (4 choose 2) = 6 two-element sets
- P₁, P₂, P₃ true.
- **Euclidean parallel property:** true (there exists a unique parallel in this model)
- Elliptic & hyperbolic properties false here.

### Model 3 (5 points; lines = all 2-element subsets)

- **Points:** A, B, C, D, E
- **Lines:** (5 choose 2) = 10 two-element sets
- P₁, P₂, P₃ true.
- **Euclidean parallel property:** false (hyperbolic behavior — multiple parallels exist)
- Shows hyperbolic case is possible while Γ holds.

### Model 4 (points = all points on sphere; lines = great circles)

- Here P₁ fails (antipodal points have infinitely many great circles through them).
- So this is **not a model of Γ** (used to illustrate violation of P₁).

---

## 9. Conclusion about logical consequence

**Definition:** Γ ⊨ α means every interpretation that makes all formulas in Γ true also makes α true.

**Because** there exist interpretations/models where Γ holds but Euclidean parallel property does not, **Euclidean parallel property is not a logical consequence of Γ.**

Similarly, elliptic and hyperbolic parallel properties are not logical consequences of Γ (each can be true in some model and false in others).
