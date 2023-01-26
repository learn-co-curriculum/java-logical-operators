# Logical Operators

## Learning Goals

- Explain logical operators.
- Discuss Truth Tables.

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
