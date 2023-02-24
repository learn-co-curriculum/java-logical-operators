# Logical Operators

## Learning Goals

- Explain logical operators.
- Discuss Truth Tables.
- Discuss De Morgan's Laws.
- Learn about compound conditionals.

## What is a Logical Operator?

**Logical operators** allow us to compare boolean values against each other.
Just like we can compare numerical values with relational operators, logical
operators do the same except with true/false values. The result of logical
operators will always be a boolean, just like relational operators! Let's
look at two boolean expressions:

```java
int firstNumber = 20;
int secondNumber = 10;

boolean expression1 = firstNumber > secondNumber;
boolean expression2 = firstNumber != 20;
```

Now that we have two boolean expressions we can compare, we still have to ask
"How do we compare these two expressions?" Consider the following table of
logical operators:

| Operator                  | Description |
|---------------------------|-------------|
| `&&`                      | AND         |
| <code>&vert;&vert;</code> | OR          |
| `!`                       | NOT         |
| `^`                       | XOR         |

Let's break this down and explain what each operator means in this table:

- `&&` (**AND**) returns true if and only if both sides of the binary operator
  are true, so:
  - `expression1` evaluates to true.
  - `expression2` evaluates to false.
  - Therefore, `expression1 && expression2` is synonymous to `true && false`.
  - Since the value true is not on both sides of the operator, the logical
    expression would return false.
- `||` (**OR**) returns true if either side of the binary operator is true, so:
  - `expression1` evaluates to true.
  - `expression2` evaluates to false.
  - Therefore, `expression1 || expression2` is synonymous to `true || false`.
  - Since the value true is on at least one side of the operator, the logical
    expression would return true.
- `!` (**NOT**) is a unary operator that returns the reverse of its single
  operand, so:
  - `expression1` evaluates to true.
  - Therefore, `!expression1` is the same as `!true`.
  - Well, the opposite of "not true" is false. So the logical expression,
    `!expression1` would return false.
- `^` (**XOR**) pronounced "exclusive or" or "x-or" returns true if and only if
  both sides of the binary operator are different.
  - `expression1` evaluates to true.
  - `expression2` evaluates to false.
  - Therefore, `expression1 ^ expression2` is the same as `true ^ false`.
  - Since the boolean values are different, the logical expression would return
    true.

Logical operators are helpful and often used within conditional clauses.
It would be nice to have a tool though to help us quickly evaluate these
logical expressions. This is where truth tables are helpful!

## Truth Tables

A **truth table** is a tabular representation of input and output combinations.
We can create truth tables for all of our logical operators, so we know what
each combination would return. This tool is helpful for us to look back on
when we may be unsure what an expression should return.

For each of these truth tables, consider X to be the first input and Y to be
the second input (when appropriate) where both X and Y are boolean values.

### AND

| X     | Y     | X && Y |
|-------|-------|--------|
| true  | true  | true   |
| true  | false | false  |
| false | true  | false  |
| false | false | false  |

A note about the `&&` operator is that it makes use of the short-circuit effect.
This means, that if the left-hand operand is false, then the expression will
immediately return false without looking at the right-hand operand.

### OR

| X     | Y     | X &vert;&vert; Y |
|-------|-------|------------------|
| true  | true  | true             |
| true  | false | true             |
| false | true  | true             |
| false | false | false            |

The `||` operator also makes use of the short-circuit effect, but does so a
little differently than the `&&` operator. For the `||` operator, if the
left-hand operand is true, then the expression will immediately return true
without looking at the right-hand operand.

### NOT

| X     | !X    |
|-------|-------|
| true  | false |
| false | true  |

### XOR

| X     | Y     | X ^ Y |
|-------|-------|-------|
| true  | true  | false |
| true  | false | true  |
| false | true  | true  |
| false | false | false |

## De Morgan's Laws

Mathematician, Augustus De Morgan, came up with a few laws regarding negating
sets that we can apply to our logical operators.

> These laws state the expression `!(condition1 && condition2)` is logically
> equivalent to the expression `!condition1 || !condition2`. Also, the
> expression `!(condition1 || condition2)` is logically equivalent to
> `!condition1 && !condition2`.
 
[Java How To Program (Early Objects), Tenth Edition](https://learning.oreilly.com/library/view/java-how-to/9780133813036/ch05lev1sec16.html#ch05lev1sec16)

Consider the following:

```java
boolean p = true;
boolean q = true;

boolean expression = !(p || q);
System.out.println(expression);
```

Notice the `expression` variable is set to `!(p || q)`. Using the values of `p`
and `q`, we can see that `p || q` results in `true`. But when we negate `true`
with the `!` operator, it evaluates the expression to `false`.

According to De Morgan's Law, `!(p || q)` is equal to `!p && !q`. Let's check!
`!p` would be equivalent to `!true`, or `false`. Since the first condition (or
the left-hand operand) evaluates to `false`, we don't even need to evaluate `!q`
since anything `&&` together with a `false` value will immediately return
`false`.

Similarly, we could have this expression:

```java
boolean p = true;
boolean q = true;

boolean expression = !(p && q);
System.out.println(expression);
```

The `expression` variable is now set to `!(p && q)`. Using the values of `p` and
`q`, we can see that `p && q` results in `true`. But when we negate `true` with
the `!` operator, it turns to be `false`.

Per De Morgan's Law, the equivalent of this expression is `!p || !q`.

Now what happens when we have an expression like this:

```java
int a = 0;
int b = 1;

boolean expression = !(a > 5 && b < 10);
System.out.println(expression);
```

We know that, per De Morgan's law, the `&&` would turn into a `||` when we
negate this expression. But what about the operators in the expressions
`a > 5` and `b < 10`? Consider the following table of what happens when each
operator is negated:

| operator | !operator |
|----------|-----------|
| `<`      | `>=`      |
| `>`      | `<=`      |
| `<=`     | `>`       |
| `>=`     | `<`       |
| `==`     | `!=`      |
| `!=`     | `==`      |

So if we wanted to write the equivalent expression to `!(a > 5 && b < 10)` we
can use the table here and what we have leaned to turn this into
`a <= 5 || b >= 10`.

The video here walks through De Morgan's Laws with some more examples if you are
interested:
[DeMorgans Law Java](https://www.youtube.com/watch?v=Q8urfkOAvxE)

## References

- [Java how to Program Early Objects, Tenth Edition](https://learning.oreilly.com/library/view/java-how-to/9780133813036/ch05lev1sec16.html#ch05lev1sec16)
- [DeMorgans Law Java](https://www.youtube.com/watch?v=Q8urfkOAvxE)
- 