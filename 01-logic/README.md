# Unit 1 — Logic

Logic is the smallest building block in this course, and much of it should feel familiar if you already program.

Every time a program asks whether a user is logged in, whether a value is valid, whether two conditions are both true, or whether one of several conditions is enough to continue, it is using logic.

The purpose of this unit is therefore not to teach programmers how `if` statements work. It is to take something you already use intuitively and give it a precise mathematical language. That language will become useful later when we describe sets, proofs, algorithms, graphs, and entire systems.

## Learning goals

By the end of this unit, you should be able to:

- identify propositions and their truth values;
- use negation, conjunction, disjunction, implication, and equivalence;
- translate between ordinary language, mathematical notation, and program conditions;
- construct and read truth tables;
- recognize logically equivalent expressions;
- understand predicates and quantifiers;
- use logic to describe software rules precisely.

---

## 1. Propositions

A **proposition** is a statement that can be classified as either true or false.

Examples:

- `5 > 3`
- "The user is authenticated."
- "The request contains a valid token."
- "Node A has an edge to Node B."

Each of these makes a claim that has a truth value.

We commonly give propositions short names such as `p`, `q`, and `r`.

For example:

- `p`: The user is authenticated.
- `q`: The user is an administrator.

This lets us reason about the structure of the rule without repeatedly writing the full sentences.

Not every sentence is a proposition. "Log in to the application" is a command, not a statement that is true or false. Likewise, `x > 5` is not yet a proposition unless we know what `x` is. Later we will call an expression like that a **predicate**.

### Software connection

A Boolean expression in a program often represents a proposition:

```java
boolean authenticated = user.isAuthenticated();
boolean admin = user.isAdmin();
```

At a particular moment in the program, each variable is either `true` or `false`.

---

## 2. Negation — NOT

The **negation** of a proposition reverses its truth value.

If:

`p`: The user is authenticated.

then:

`¬p`: The user is not authenticated.

The symbol `¬` means **not**.

| p | ¬p |
|---|---|
| T | F |
| F | T |

In programming this is familiar as:

```java
if (!authenticated) {
    redirectToLogin();
}
```

Mathematical notation and programming syntax differ, but the idea is identical.

---

## 3. Conjunction — AND

A **conjunction** says that two propositions must both be true.

Notation:

`p ∧ q`

Read it as:

> p AND q

Suppose:

- `p`: The user is authenticated.
- `q`: The user has edit permission.

Then:

`p ∧ q`

means:

> The user is authenticated AND has edit permission.

| p | q | p ∧ q |
|---|---|---|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | F |

The programming equivalent is straightforward:

```java
if (authenticated && hasEditPermission) {
    allowEdit();
}
```

AND is restrictive: every required condition must hold.

---

## 4. Disjunction — OR

A **disjunction** says that at least one proposition must be true.

Notation:

`p ∨ q`

Read it as:

> p OR q

Suppose a user may delete a post if they own the post or they are a moderator.

- `p`: The user owns the post.
- `q`: The user is a moderator.

The rule is:

`p ∨ q`

| p | q | p ∨ q |
|---|---|---|
| T | T | T |
| T | F | T |
| F | T | T |
| F | F | F |

In code:

```java
if (ownsPost || isModerator) {
    allowDelete();
}
```

In mathematical logic, OR normally means **inclusive OR**: it is also true when both propositions are true.

That distinction matters because ordinary conversation sometimes uses "or" to mean exactly one choice. If exactly one of two conditions may be true, that is **exclusive OR (XOR)**.

---

## 5. Combining logical expressions

Real rules often contain several operators.

Suppose a user can edit a post when they are authenticated and either own the post or are a moderator.

Let:

- `a`: authenticated
- `o`: owns the post
- `m`: moderator

Then the rule is:

`a ∧ (o ∨ m)`

In code:

```java
if (authenticated && (ownsPost || isModerator)) {
    allowEdit();
}
```

Parentheses matter. Compare:

`a ∧ (o ∨ m)`

with:

`(a ∧ o) ∨ m`

The second expression allows a moderator through even if the moderator is not authenticated. The expressions look similar, but they describe different rules.

This is one reason formal logic is useful in software engineering: it makes the exact structure of a rule visible.

---

## 6. Implication — IF ... THEN

One operator is less obvious from ordinary programming syntax: **implication**.

Notation:

`p → q`

Read it as:

> If p, then q.

For example:

- `p`: The request is authorized.
- `q`: The request has an authenticated user.

`p → q` says:

> If the request is authorized, then the request has an authenticated user.

This is useful for describing **guarantees, requirements, and invariants**.

The truth table is:

| p | q | p → q |
|---|---|---|
| T | T | T |
| T | F | F |
| F | T | T |
| F | F | T |

The surprising rows are the last two. Why is the implication true when `p` is false?

Because the statement only promises what must happen **if p occurs**.

Consider:

> If an account is an administrator account, it has elevated permissions.

A normal user account does not violate that rule. The rule made no claim about what happens when the account is not an administrator.

The only way to violate `p → q` is for `p` to be true while `q` is false.

This idea appears constantly in specifications:

> If an order is marked shipped, it must have a shipment record.

> If a session is expired, it cannot authorize a protected request.

> If a node is a child, it must have a parent.

These are logical claims about valid system states.

### A common mistake: reversing implication

From:

`p → q`

we cannot automatically conclude:

`q → p`

For example:

> If a user is an administrator, the user is authenticated.

does **not** mean:

> If a user is authenticated, the user is an administrator.

The reversed statement is called the **converse**, and it is a different claim.

---

## 7. Equivalence — IF AND ONLY IF

Sometimes two statements imply one another.

Notation:

`p ↔ q`

Read it as:

> p if and only if q

or simply:

> p exactly when q

It is true when `p` and `q` have the same truth value.

| p | q | p ↔ q |
|---|---|---|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | T |

Equivalence is stronger than implication.

`p → q` gives one direction.

`p ↔ q` gives both:

`p → q` and `q → p`

For software, equivalence is useful when a state is defined exactly by a condition rather than merely constrained by it.

---

## 8. Truth tables as exhaustive testing

A truth table lists every possible assignment of truth values to an expression.

For two Boolean variables there are four combinations:

| p | q |
|---|---|
| T | T |
| T | F |
| F | T |
| F | F |

For three variables there are eight. For four there are sixteen.

In general, `n` independent Boolean variables have:

`2^n`

possible truth-value combinations.

This makes a truth table a tiny form of **exhaustive state-space analysis**.

Consider:

`authenticated ∧ (owner ∨ moderator)`

A truth table can enumerate all eight possible combinations and tell us exactly when access is granted.

That is closely related to testing. If a permission rule depends on three independent Boolean inputs, its complete Boolean state space contains eight cases.

Later, when we study combinatorics, we will see why exhaustive testing becomes difficult as the number of independent conditions grows.

---

## 9. Logical equivalence

Two expressions are **logically equivalent** if they have the same truth value for every possible input.

For example:

`¬(p ∧ q)`

is equivalent to:

`¬p ∨ ¬q`

This is one of **De Morgan's laws**.

In ordinary language:

> It is not true that both conditions hold

means the same thing as:

> At least one of the conditions does not hold.

Likewise:

`¬(p ∨ q) ≡ ¬p ∧ ¬q`

These transformations are useful when simplifying or checking complex conditions.

We will return to them in greater depth in the Boolean Algebra unit.

---

## 10. Predicates

Consider:

`x > 5`

We cannot call this simply true or false until we know `x`.

This is a **predicate**: a statement whose truth depends on one or more variables.

We can write it as:

`P(x): x > 5`

Now:

`P(10)` is true.

`P(3)` is false.

Programming is full of predicates:

```java
user.isActive()
order.total() > 100
post.authorId() == user.id()
```

A predicate can be thought of as a rule that takes an object or value and produces a truth value.

This idea will become especially important when we study sets. A set can often be described by the predicate its members satisfy.

---

## 11. Quantifiers

Predicates let us make statements about collections of values.

Two important symbols are:

### Universal quantifier — ∀

`∀` means **for all** or **for every**.

For example:

`∀ user ∈ Admins, authenticated(user)`

means:

> Every administrator is authenticated.

### A symbol from the next unit — ∈

The symbol `∈` means **is an element of** or **belongs to**. It is set notation, which we will study properly in Unit 2, but it appears naturally alongside quantifiers.

For example:

`user ∈ Admins`

means:

> user belongs to the set of administrators.

So in:

`∀ user ∈ Admins, authenticated(user)`

we can read each piece as:

- `∀ user` — for every user
- `∈ Admins` — belonging to the set of administrators
- `authenticated(user)` — that user is authenticated

Altogether: **Every administrator is authenticated.**

This resembles assertions developers make about an entire class of objects.

### Existential quantifier — ∃

`∃` means **there exists at least one**.

For example:

`∃ user ∈ Users, moderator(user)`

means:

> There exists at least one user who is a moderator.

Here again, `∈ Users` means **belongs to the set of Users**. The symbols `∀`, `∃`, and `∈` may look somewhat similar at first, but they have different jobs: `∀` says **every**, `∃` says **at least one exists**, and `∈` says **belongs to a set**.

These are much more than unusual symbols. They distinguish two fundamentally different kinds of claims:

> Every request passed validation.

versus:

> At least one request passed validation.

Confusing those statements can produce very different conclusions.

### Negating quantified statements

There is an important relationship:

`¬∀x P(x) ≡ ∃x ¬P(x)`

In words:

> It is not true that every x satisfies P

means:

> There is at least one x that does not satisfy P.

Similarly:

`¬∃x P(x) ≡ ∀x ¬P(x)`

In words:

> There does not exist an x satisfying P

means:

> Every x fails to satisfy P.

This is useful when reasoning about tests and counterexamples. To disprove a claim that something works for **every** input, you only need one input for which it fails.

That observation leads directly toward the later unit on proofs.

---

# Putting it together: describing a system rule

Suppose a system has this requirement:

> Every published post must have an author, and its author must be an active user.

Let:

- `Post` be the collection of posts;
- `published(p)` mean post `p` is published;
- `hasAuthor(p)` mean post `p` has an author;
- `active(author(p))` mean its author is active.

We can express the requirement as:

`∀p ∈ Post, published(p) → (hasAuthor(p) ∧ active(author(p)))`

You do not need mathematical notation to implement the system. But the notation gives us a compact, unambiguous way to state what the system guarantees.

That is the larger purpose of discrete mathematics in this course: **a common language for describing logic and systems precisely.**

---

# Worked example

A document may be edited when:

1. the user is authenticated; and
2. the user owns the document or has the editor role.

Define:

- `a`: authenticated
- `o`: owner
- `e`: editor

The rule is:

`a ∧ (o ∨ e)`

Now examine a few states:

| a | o | e | Can edit? |
|---|---|---|---|
| T | T | F | T |
| T | F | T | T |
| T | F | F | F |
| F | T | T | F |

The last row is important. Even though both authorization-related conditions are true, authentication is required separately.

This same rule can be represented in code:

```java
boolean canEdit = authenticated && (owner || editor);
```

or in mathematical logic:

`a ∧ (o ∨ e)`

or in English:

> The user must be authenticated and must either own the document or have the editor role.

Those are three languages describing the same structure.

---

# Practice

Try these before looking anything up.

### 1. Translation

Let:

- `p`: the user is authenticated
- `q`: the user has a paid account

Write each statement symbolically:

1. The user is authenticated and has a paid account.
2. The user is authenticated or has a paid account.
3. The user is not authenticated.
4. If the user has a paid account, then the user is authenticated.

### 2. Permission rule

A user may view an internal dashboard if the user is an employee **and** is either a manager or an administrator.

Define three proposition letters and write the logical expression.

Then write the equivalent Boolean expression in a programming language of your choice.

### 3. Find the bug

A requirement says:

> Only authenticated administrators may delete users.

A developer writes:

```java
if (authenticated || administrator) {
    deleteUser();
}
```

Explain precisely what is wrong with the condition.

### 4. Implication

Suppose:

`p`: An order has shipped.

`q`: The order has a tracking record.

Explain what `p → q` requires and identify the one combination of truth values that violates the requirement.

### 5. Quantifiers

Translate these into ordinary English:

`∀u ∈ Users, hasId(u)`

`∃u ∈ Users, administrator(u)`

Then explain how you could disprove the first statement.

### 6. Design your own rule

Choose a real software rule involving at least three Boolean conditions. Write it:

1. in ordinary English;
2. as a logical expression;
3. as a Boolean expression in code.

Check whether all three versions actually say the same thing.

---

# Review

The central ideas of this unit are small:

- A **proposition** is true or false.
- `¬p` means NOT p.
- `p ∧ q` means p AND q.
- `p ∨ q` means p OR q.
- `p → q` means if p, then q.
- `p ↔ q` means p if and only if q.
- A **truth table** enumerates possible truth-value combinations.
- A **predicate** becomes true or false depending on its input.
- `∀` means every.
- `∃` means at least one exists.
- `∈` means **is an element of** or **belongs to** a set.

A useful way to keep the three similar-looking symbols straight is: `∀` = **every**, `∃` = **exists**, `∈` = **belongs to**.

None of these ideas is individually very large. Their importance comes from what we can build with them.

Logic gives us a precise vocabulary for describing rules. Sets will give us a vocabulary for describing collections. Relations will let us describe connections. Proofs will let us justify claims. Graph theory will let us model whole networks of relationships.

So this unit is intentionally a small foundation. The interesting part of discrete mathematics comes as these pieces begin to connect.

## Next

**Unit 2 — Sets:** moving from statements about individual conditions to precise descriptions of collections of objects.