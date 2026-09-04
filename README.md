# Discrete Mathematics for Software Engineers

Discrete mathematics gives software engineers a **common language for describing logic, structures, relationships, and systems**.

Instead of focusing mainly on continuous quantities, as calculus often does, discrete mathematics studies distinct objects and states: true or false conditions, sets of values, nodes and edges in a graph, recursive structures, combinations, mappings, and finite or countable possibilities.

That makes it especially relevant to software. Programs are built from discrete states. Databases organize sets and relationships. Permissions rely on logic. Networks and dependencies can be modeled as graphs. Trees appear in file systems, user interfaces, compilers, and hierarchical data. Algorithms often depend on counting, recursion, and formal reasoning.

This course is designed to approach those ideas **through software engineering first**. The goal is not to memorize mathematical notation for its own sake. The goal is to learn a precise way to reason about software systems and the structures underneath them.

## Course Goals

By the end of the course, you should be able to:

- Translate ordinary programming conditions into formal logic.
- Use sets, relations, and functions to describe software data and behavior.
- Reason carefully about whether an algorithm or rule is correct.
- Analyze combinations and possible system states.
- Understand recursion mathematically as well as programmatically.
- Model systems using graphs and trees.
- Recognize when Boolean algebra, probability, or number theory applies to a software problem.
- Connect discrete mathematical ideas to data structures and algorithms.
- Use mathematical language to describe software systems more precisely.

## Course Philosophy

The course follows a simple progression:

**Programming intuition → mathematical language → formal reasoning → software application**

Each unit should include:

1. An intuitive explanation.
2. The mathematical vocabulary and notation.
3. Several software-engineering examples.
4. Worked examples.
5. Practice exercises.
6. A small application or programming exercise where appropriate.
7. A short review tying the unit back to the larger course.

The emphasis is on understanding *why* an idea is useful before becoming formal about it.

---

# Course Outline

## Unit 1 — Logic

**Core topics:** propositions, truth values, negation, AND, OR, implication, equivalence, truth tables, predicates, quantifiers.

**Software connections:**

- `if` statements
- validation rules
- authorization and permissions
- feature flags
- business rules
- specifications and invariants

Logic is the foundation of the course because software constantly makes decisions based on whether statements are true or false.

---

## Unit 2 — Sets

**Core topics:** sets, elements, subsets, union, intersection, difference, complement, Cartesian products, power sets.

**Software connections:**

- collections
- database queries
- filtering
- roles and permissions
- test-data domains
- grouping objects by properties

Sets provide a precise way to describe collections of objects and the relationships between collections.

---

## Unit 3 — Relations and Functions

**Core topics:** relations, functions, domains, codomains, mappings, equivalence relations, partial orders.

**Software connections:**

- database relationships
- object associations
- APIs and transformations
- identity and equality
- dependency ordering
- state transitions

Relations let us describe how things are connected. Functions describe how one value or object maps to another.

---

## Unit 4 — Proof and Mathematical Reasoning

**Core topics:** direct proof, counterexamples, proof by contradiction, proof by cases, mathematical induction, invariants.

**Software connections:**

- showing that an algorithm works
- proving that an edge case cannot occur
- reasoning about loops
- validating recursive algorithms
- expressing system guarantees

The goal is not to become a pure mathematician. It is to become more rigorous about claims such as, "This always works," or, "This state can never occur."

---

## Unit 5 — Counting and Combinatorics

**Core topics:** sum and product rules, permutations, combinations, binomial coefficients, pigeonhole principle.

**Software connections:**

- counting possible system states
- estimating test combinations
- password/search spaces
- configuration explosion
- brute-force algorithms

Counting helps explain why apparently small systems can produce enormous numbers of possible states.

---

## Unit 6 — Discrete Probability

**Core topics:** sample spaces, events, probability rules, conditional probability, independence, expected value.

**Software connections:**

- reliability
- randomized algorithms
- testing
- failure probabilities
- distributed systems
- interpreting uncertain outcomes

This unit builds on sets and counting to reason about uncertainty in discrete systems.

---

## Unit 7 — Recursion and Recurrence Relations

**Core topics:** recursive definitions, recursive sequences, recurrence relations, induction and recursion together.

**Software connections:**

- recursive functions
- divide-and-conquer algorithms
- nested data
- trees
- repeated state transformations
- algorithm runtime growth

Recursion in code and induction in mathematics have closely related structures. This unit makes that connection explicit.

---

## Unit 8 — Graph Theory

**Core topics:** vertices, edges, directed and undirected graphs, paths, cycles, connectivity, degree, reachability, DAGs, topological ordering.

**Software connections:**

- dependency graphs
- social networks
- routing
- build systems
- package dependencies
- workflow graphs
- system architecture

Graph theory provides one of the clearest examples of discrete mathematics as a language for describing systems and relationships.

---

## Unit 9 — Trees

**Core topics:** rooted trees, parent/child relationships, leaves, depth, traversal, binary trees, spanning trees.

**Software connections:**

- file systems
- DOM trees
- abstract syntax trees
- organizational hierarchies
- search trees
- hierarchical application data

Trees are a special kind of graph with structures that appear throughout software engineering.

---

## Unit 10 — Boolean Algebra

**Core topics:** Boolean variables, logical identities, simplification, De Morgan's laws, equivalent expressions.

**Software connections:**

- complex conditionals
- access-control logic
- search filters
- digital logic
- simplifying predicates

Boolean algebra gives us formal tools for simplifying and reasoning about logical expressions.

---

## Unit 11 — Number Theory

**Core topics:** divisibility, primes, greatest common divisors, modular arithmetic, congruence.

**Software connections:**

- hashing
- cryptography
- cyclic structures
- checksums
- identifiers
- modular indexing

Number theory shows how apparently abstract mathematics becomes foundational in areas such as cryptography and computer security.

---

## Unit 12 — Discrete Mathematics in Algorithms and Software Systems

**Core topics:** combining logic, sets, counting, recursion, graphs, trees, and formal reasoning.

**Software connections:**

- data structures and algorithms
- complexity reasoning
- dependency analysis
- state-space modeling
- system design
- correctness arguments

This final unit brings the earlier ideas together and uses them to analyze realistic software problems.

---

# Possible Final Project

The course can culminate in a software-system modeling project.

For example, a student could take a graph-based application or another real software system and formally describe:

- its important sets of objects,
- relationships between those objects,
- logical rules and constraints,
- possible states,
- recursive or hierarchical structures,
- graph properties,
- algorithms operating on the system,
- and selected correctness or complexity arguments.

The goal would be to demonstrate that discrete mathematics is not separate from software engineering. It is a toolkit for **describing software precisely, asking better questions about it, and reasoning about how it behaves**.

## Status

This repository is being developed as a complete, self-guided course. The plan is to build each unit in depth rather than generate every lesson superficially at once.

**Next:** Unit 1 — Logic.
