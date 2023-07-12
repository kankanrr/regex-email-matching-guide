# Matching an Email RegEx

In this guide we will be covering how we can use this `RegEx (Regular Expression)` to match and validate a user inputted email. This will prove to be useful when validating emails in the back-end using technologies such as Node and/or MongoDB.

## Summary

We will be using this RegEx example and walking through what each component does.

> `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

The following expression is used when we match emails specifically.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## RegEx Components

### Anchors

---

> Current RegEx: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

There are two anchors in our RegEx which are `^` & `$`.

- The `^` anchor indicates that the code must appear at the beginning of a string
- On the contrary, `$` indicates the the code must appear at the end of a string

Now since our regular expression contain both anchors above this means that a given string must match all the given specifications exactly, or it will not match.

- Email example: `email@service.com`

<!-- Although this sounds limiting, you will see how quantifiers, grouping and bracket expressions allow a large range of variation in the given string. -->

### Quantifiers

---

> Current RegEx: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Quantifiers are used to specify how many times a given character is expected to appear. Our RegEx uses two quantifiers: `+` & `{2,6}`.

Our expression also uses `[a-z0-9_.-]+` which means that any character matching one that is inside the brackets is expected to appear atleast once, with no upper limit.
The same is true for `[\da-z.-]+`. `[a-z.]{2,6}` means that 2 to 6 characters matching those inside the brackets are expected.

The numbers inside the curly braces specify the lower and upper limit of the number of characters expected.

> - Email example: `email@service.com`

- `+` follows the character set of `[a-z0-9_/.-]`
- This checks for one or more of an allowed character in the `email` field
- `{2,6}` follows the character set: `[a-z\.]`
- The quantifier would say "Match between 2 and 6 of the corresponding characters `.com`"

### Character Classes

---

> Current RegEx: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

RegEx uses special character classes to match different types of characters.

In our expression, `\d` is used to match any digit character. The `\ (backslash)` is necessary since it differentiates the digit class from a plain letter "d".

Although we only have one character class in the expression, the function of a backslash is helpful in understanding another art of the expression which is the ".".

Unlike the other character classes, `\d`, `\w (matching a word character)`, and `\s (matching a whitespace character)`, the character class `".`, `which matches any character`, does not require a backslash. Because of the unique behavior of ".", the backslash must be used to negate its use as a character class and interpret it as just the character ".".

> - Email example: `email@service.com`

All characters within the email are allowed by the character classes `a-z`, `0-9`,`/d`,`/.`, and `@`. Therfore the email remains valid.

### Grouping and Capturing

---

> Current RegEx: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Grouping and Capturing is done with `()` within RegEx. Anything within a set of parentheses is taken as a single group, which allows all the information inside to be treated as a single unit.

If we take a look at the expression and pay attention to the parentheses...

> `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Between `/^` & `$/` are three different character groups, which are `([a-z0-9_.-]+)`, `([\da-z.-]+)`, and `([a-z.]{2,6})`.

- The first group is looking for any lowercase letter, any digit, any underscore, hyphen, period in a set prior to the `@`.
- Group 2 looks for any digit, lowercase letter, period, or hyphen prior to the escaped period `/.`
- Group 3 is searching for between 2-6 characters containing lowercase letters and/or a period.

If we disregard the logic regarding these expressions, then wecan also express this RegEx as: `(1)@(2).(3)`. By splitting this into 3 parts we can see that is corresponds to the regular format of an email being `(name)@(email)(site ext.)`.

> Email example: `email@service.com`
> Group 1 is

### Bracket Expressions

---

> Current RegEx: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Lastly, we have the bracket expressions component of a RegEx. Currently in our email expression we have 3 being:

- `[a-z0-9_.-]`

  > - Found:/^(`[a-z0-9_\.-]`+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

- `[\da-z.-]`

  > - Found:/^([a-z0-9_\.-]+)@(`[\da-z\.-]`+)\.([a-z\.]{2,6})$/

- `[a-z.]`
  > - Found:/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.(`[a-z\.]`{2,6})$/

A bracket expression represents a single character. The character can be anything that is within the brackets. For example: `[a-z0-9_.-]`, this character will be matched by any lowercase letters from a-z, any digit from 0-9, or a period. Combined with the quantifier `+`, this code means that any number of characters matching what is specified in the brackets will match.

### Greedy and Lazy Match

---

This RegEx does include greedy matches, since it includes the `+` quantifier. This will match as many times as possible giving back as needed. Another greedy quantifier used in this RegEx is `{}` when matching `{2,6}` for the last capture group.

## Author

---

Thanks for reading this guide ! Hope it helped ! Feel free to find me on github: https://github.com/kankanrr
