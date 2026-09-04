# Discrete Mathematics Symbol Reference

Discrete mathematics has its own notation; **LaTeX is a way to type and typeset that notation**. LaTeX does not give the symbols their mathematical meaning. It gives us text commands that render as those symbols.

For example, the mathematical statement:

`∀x ∈ A, P(x) → Q(x)`

can be entered in LaTeX as:

```latex
\forall x \in A, P(x) \rightarrow Q(x)
```

So there are three useful layers to recognize:

| Layer | Example |
|---|---|
| Meaning in English | For every x belonging to A, if P(x), then Q(x) |
| Mathematical notation | `∀x ∈ A, P(x) → Q(x)` |
| LaTeX source | `\forall x \in A, P(x) \rightarrow Q(x)` |

For most symbols in this course, the correspondence is direct: learn what the mathematical symbol means, and the LaTeX command is simply a convenient way to type it. Some notation is built from several LaTeX commands rather than one command, and some symbols have multiple accepted LaTeX forms.

## Symbol table

| Symbol | Read as | Meaning | LaTeX | Example | Main unit |
|---|---|---|---|---|---|
| `¬` | not | Negates a statement | `\neg` | `¬p` | Logic |
| `∧` | and | Both statements are true | `\land` | `p ∧ q` | Logic |
| `∨` | or | At least one statement is true | `\lor` | `p ∨ q` | Logic |
| `⊕` | exclusive or / XOR | Exactly one of two statements is true | `\oplus` | `p ⊕ q` | Logic / Boolean Algebra |
| `→` | implies / if...then | If the left side is true, the right side must be true | `\rightarrow` | `p → q` | Logic |
| `↔` | if and only if | Both statements imply each other | `\leftrightarrow` | `p ↔ q` | Logic |
| `≡` | equivalent / logically equivalent | Two expressions have the same logical meaning in context | `\equiv` | `¬(p ∧ q) ≡ ¬p ∨ ¬q` | Logic / Boolean Algebra |
| `∀` | for all / for every | A statement applies to every item under consideration | `\forall` | `∀u ∈ Users, hasId(u)` | Logic |
| `∃` | there exists | At least one item satisfies a statement | `\exists` | `∃u ∈ Users, admin(u)` | Logic |
| `∈` | is an element of / belongs to | An item belongs to a set | `\in` | `u ∈ Users` | Sets |
| `∉` | is not an element of | An item does not belong to a set | `\notin` | `u ∉ Admins` | Sets |
| `⊆` | is a subset of | Every element of one set is also in another | `\subseteq` | `Admins ⊆ Users` | Sets |
| `⊂` | is a proper subset of* | One set is contained in another and is not equal to it | `\subset` | `Admins ⊂ Users` | Sets |
| `∪` | union | Everything belonging to either set | `\cup` | `A ∪ B` | Sets |
| `∩` | intersection | Everything belonging to both sets | `\cap` | `A ∩ B` | Sets |
| `∅` | empty set | A set containing no elements | `\emptyset` | `A = ∅` | Sets |
| `\` | set difference | Elements in one set but not another | `\setminus` | `A \ B` | Sets |
| `×` | Cartesian product | All ordered pairs formed from two sets | `\times` | `Users × Roles` | Sets / Relations |
| `=` | equals | Two values or objects are equal in the stated sense | `=` | `x = 5` | Throughout |
| `≠` | not equal | Two values are not equal | `\neq` | `x ≠ 5` | Throughout |
| `≤` | less than or equal to | Comparison or ordering | `\leq` | `x ≤ 10` | Relations / Throughout |
| `≥` | greater than or equal to | Comparison or ordering | `\geq` | `x ≥ 10` | Relations / Throughout |
| `|A|` | cardinality of A | Number of elements in a finite set | `\lvert A \rvert` | `|Users| = 100` | Sets / Counting |
| `𝒫(A)` | power set of A | Set of all subsets of A | `\mathcal{P}(A)` | `𝒫({a,b})` | Sets |
| `Σ` | sum | Add a sequence or collection of values | `\sum` | `Σ xᵢ` | Counting / Algorithms |
| `Π` | product | Multiply a sequence or collection of values | `\prod` | `Π xᵢ` | Counting |
| `n!` | n factorial | Product `n × (n-1) × ... × 1` | `n!` | `5! = 120` | Counting |
| `C(n,k)` / binomial coefficient | n choose k | Number of ways to choose k items from n without order | `\binom{n}{k}` | `C(5,2) = 10` | Counting |
| `⌊x⌋` | floor of x | Greatest integer less than or equal to x | `\lfloor x \rfloor` | `⌊3.8⌋ = 3` | Algorithms / Number Theory |
| `⌈x⌉` | ceiling of x | Smallest integer greater than or equal to x | `\lceil x \rceil` | `⌈3.2⌉ = 4` | Algorithms / Number Theory |
| `a ∣ b` | a divides b | b is divisible by a with no remainder | `a \mid b` | `3 ∣ 12` | Number Theory |
| `a ≡ b (mod n)` | congruent modulo n | a and b have the same remainder modulo n | `a \equiv b \pmod{n}` | `17 ≡ 2 (mod 5)` | Number Theory |

\*Notation for proper subsets is not perfectly universal across textbooks. We will use `⊆` when equality is allowed and explicitly explain proper-subset notation when we reach sets.

## Reading LaTeX syntax

A few patterns make LaTeX much less mysterious:

- A backslash begins many commands: `\forall`, `\in`, `\rightarrow`.
- Curly braces group arguments: `\binom{n}{k}` says that `n` and `k` are the two arguments of the binomial-coefficient command.
- Subscripts use `_`: `x_i` represents x with subscript i.
- Superscripts use `^`: `2^n` represents 2 to the nth power.
- Commands can be combined: `\forall x \in A` becomes `∀x ∈ A` when rendered as mathematics.

This makes LaTeX somewhat analogous to source code: **you type a textual instruction, and a renderer produces the formatted mathematical expression.** The important thing for this course is still the mathematics. LaTeX is simply a practical way to write it.