# Regex Tutorial: Matching a URL with Regular Expressions

A Regular Expression (Regex) is a sequence or series of special characters that define a search pattern. We can use these patterns and search for them in a body of text.

## Summary

In this tutorial, we will breakdown a Regex that is used to match URLs to elucidate the components of a Regex

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)

## Regex Components

Regular expression are considered literal, so must be wrapped up in slash characters `/` as 
in the example (notice the Regex is flanked by `/`):

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

### Anchors

There are two anchors: `^` and `$`.

An `^` anchor signifies a string that begins with the characters that follow it. In our example, it can be found near the beginning of the Regex.

an `$` anchor signifies a string that ends with the characters that precede it, and is located at the end of our Regex in the example immediately inside our slash characters:

`/^.........$/`

### Quantifiers

Quantifiers set the limits of the string that the Regex matches. They often include the minimum and maximum number of characters that the Regex is looking for:

`*`-----Matches pattern 0 or more times
`+`-----Matches pattern one or more times
`?`-----Matches pattern 0 or one time
`{n}`---Matches exactly n times
`{n,}`--Matches at least n number of times
`{n,x}`-Mathces a minimum of n times to a maximum of x times

In the example, these quantifiers are seen in many places and set limits for the preceding pattern/characters:

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

The `?` in the example Regex `(https?:\/\/)?` will accept 0 or 1 pattern matching `https` or `https://`

The `+` in the  example Regex `[\da-z\.-]+` will accept one or more patterns with a string containing numbers, letters (lowercase), dots or hyphens.

The `{2,6}` in the example Regex `[a-z\.]{2,6}` will accept 2-6 patterns with a string containing letters and dots

The `*` in the example Regex `[\/\w \.-]*` will accept 0 or any number of patterns with a string containing `/`, alphanumeric characters, and dots or hyphens.

### OR Operator

An OR operator matches characters on the left or right side of the operator `|` and serves as an and/or. Our example does not have an OR operator..but, for example, if we had a  `a-z|Z` in our example, it would take either lowercase z or uppercase Z.

### Character Classes

A character class defines a set of characters which can occur within an input string:

`.`-----Matches any character except the newline character `\n`
`\d`----Matches any Arabic numeral digit, equivalent to [0-9]
`\w`----Matches any alphanumeric character from the basic Latin alphabet including `_`, equivalent to [A-Za-z0-9_]
`\s`----Matches a single whitespace character including tabs an line breaks

In the example, we can see that we are looking for digits `\d` as well as lowercase letters (a-z).

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

The `/d` in the example Regex `[\da-z\.-]` will match any Arabic numeral digit

The `/w` in the  example Regex `[\/\w \.-]` will match any alphanumeric character from the basic Latin alphabet including `_`


### Flags

Flags are components that can define additional functionality or limits for the Regex. Flags are placed outsied of the wrapping slash characters `/` in the Regex. The example does not have Flags, but the most common are:

`g`-----Global search, test Regex against all possible matches in a string
`i`-----Case-insensitive search, case is ignored when matching in a string
`m`-----Multi-line search, multi-line input is treated as multiple lines

### Grouping and Capturing

Grouping is used to check multiple parts of a string to check if different sections fulfill their different requirements. The primary way these sections are grouped or 'broke up' is by using parentheses `()`

In the example, various sections of the Regex have been grouped:

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Broken down, the sections are: 

`(https?:\/\/)`: This first section is the beginning of our web address `http://`

`([\da-z\.-]+)\.`: This second sections searches for a `string containing: number,lowercase letter, dot, or hypen` then `.`

`([a-z\.]{2,6})` and `([\/\w \.-]*)`: The third and fourth sections searches for a `string containing: lowercase letter, or dot` followed by another group with a `string containing "/" alphanumeric characters, dot, or hypen (this pattern could be more than once)`


### Bracket Expressions

Characters in side `[]` signify a range of characters that we want to match. In the example bracker expressions ar used to to identify subsets of patterns:

`[\da-z\.-]+`: Any Arabic numeral digit and lowercase letter a-z including `.` and `-`.

`[a-z\.]`: Any lowercase letter a-z including `.`. 

`[\/\w \.-]*`: Any alphanumeric character including `.` and `-`.

### Greedy and Lazy Match

Greedy and Lazy quantifiers dictate the length of the string matched. "Greedy" will match the the longest possible string while "Lazy" will match the shortest possible string. In the example, "Greedy" quantifiers are identical to the quantifiers above (`*, +, ?, {n}, {n,}, {n, x}`). There are no "Lazy" quantifiers which are post-fixed with a `?`: (`*?, +?, ??, {n}?, {n,}?, {n, x}?`).

### Boundaries

Boundaries are similar to an anchor and uses the expression `\b` for word boundaries and `\B` for non-word boundaries. They are a zero-length match that marks the beginning and end of an alphanumerical sequence. `\b` allows you to perform a “whole words only” search using a regular expression in the form of `\bword\b`. The example does not have any boundaries.

### Back-references

Backreferences are filters used to match the same text previously matched by a capturing group. The example does not have any boundaries.

## Author

James Sung is a UCLA graduate and UCLA bootcamp student that is aspiring to be a data scientist.
[James Github](https://github.com/JamesDartmouth)  