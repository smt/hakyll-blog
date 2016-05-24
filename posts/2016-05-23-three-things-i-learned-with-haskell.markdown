---
date: 2016-05-23 20:36:04
title: Three Things I've Learned With Haskell
tags: Haskell, Mad Coding
---

This is the first of a series of posts. We'll see how it goes if I try to keep each one limited to "three things." That seems a nice, manageable number.

While picking my way through [Haskell Programming from First Principles] (hereafter referred to as <abbr title="Haskell Programming from First Principles">HPFP</abbr>), I've come across a number of interesting syntactic concepts that I haven't seen much of (or at all) in my prior programming experience until recently.

_Note: I've been a front-end developer primarily focused on JavaScript and other dynamic languages for most of my professional life, while these things are new to **me**, I'm fully aware that they may not be new for **you**. As always, I welcome any constructive feedback._

  [Haskell Programming from First Principles]: http://haskellbook.com

## Lambdas

Being a functional language, Haskell features anonymous functions (or _lambdas_) rather prominently. It was exciting to learn that parts of the Haskell language are merely syntactic sugar around these lambdas. <abbr title="Haskell Programming from First Principles">HPFP</abbr> has a whole chapter dedicated solely to the lambda calculus, which underpins many major concepts of Haskell's design.

In JavaScript, a lambda looks like this:

```javascript
function (x) { return "yeah " + x + "!"; }
```

If you're one of those people who likes their ES2015 arrow functions, you might be more at home with this:

```javascript
x => "yeah " + x + "!"
```

In the following example of a Haskell lambda, you can see how the design of the ES2015 lambda might have drawn inspiration:

```haskell
\x -> "yeah " ++ x ++ "!"
```

It's a small thing, but one of my favorite things about using Haskell lambdas is how my editor is configured to treat them. In a lambda, the \\ is replaced by a λ: a lambda character! It helps me when I see that instead of a backslash:

```haskell
λx -> "yeah " ++ x ++ "!"
```

## Pattern Matching

My exposure to _pattern matching_ is totally backwards, because the first time I saw it was in some [Elixir] code. However, the Elixir examples I've seen tend to use pattern matching with destructuring variable binding:

```elixir
{x, y} = {1, 2}  # {1, 2}
x  # 1
y  # 2

[h | _] = [1, 2, 3]  # [1, 2, 3]
h  # 1
```

I haven't gotten far enough with my Haskell learning to know how it treats destructuring assignment (I'm fairly sure my brain will melt when I get to that point). For conventional assignment, it's pretty great to be able to express functions in this clear a way:

```haskell
isItTen :: Integer -> Bool
isItTen 10 = True
isItTen _  = False
```

As with some other languages like Go and Elixir, `_` acts like a catch-all bitbucket for unneeded values. It's interesting to me that the patterns are matched against values rather than types. Pattern matching can help prevent some needlessly verbose logic in the function body.

  [Elixir]: http://elixir-lang.org

## Guards

Every language has its own concept of control flow. In JavaScript and other languages in the C family, most of the burden falls on `if`/`else` statements, and occasionally a `switch`/`case`.

```javascript
function goodRange(temp) {
  var out;
  switch (temp) {
  case temp < 64:
    out = "too low";
    break;
  case temp > 78:
    out = "too high";
    break;
  default:
    out = "just right";
    break;
  }
  return out;
}
```

Haskell also has an `if-then-else` pattern that you can use, but it only supports two possible outcomes. When writing a function definition, especially one with more than two possible outcomes, _guard_ syntax can come in handy. It resembles pattern matching.

```haskell
goodRange :: Integer -> String
goodRange x
  | x < 64    = "too low"
  | x > 78    = "too high"
  | otherwise = "just right"
```

The `goodRange` function is expressive and clear: for an Integer `x`, return a string depending on where `x` falls within a predetermined range.

Here's another example, taken right out of the <abbr title="Haskell Programming from First Principles">HPFP</abbr> book because it's so great:

```haskell
avgGrade :: (Fractional a, Ord a) => a -> Char
avgGrade x
  | y >= 0.9  = 'A'
  | y >= 0.8  = 'B'
  | y >= 0.7  = 'C'
  | y >= 0.59 = 'D'
  | y < 0.59  = 'F'
  where y = x / 100
```

For a given `x` that implements `Fractional` and `Ord` typeclasses (think of them like interfaces or mixins that provide access to certain functions), divide `x` by 100 (scoped to the variable `y` in the `where` clause) and return a "grade" character based on several ranks of comparison... ranks that most of us have come to either love or despise.
