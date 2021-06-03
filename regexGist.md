# Matching an Email Using Regex

This Gist explores how to translate Regular Expressions! Below you will find a breakdown of the various compenents that help write and search with Regex.

## Summary

This walkthrough handles the analyisis of a regex that specifies a search pattern for emails. The specific regex we will be working with looks like this:
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components
A regex expression must always be contained between two slashes / to signify the beginning and end.

### Anchors
The characters ^ and $ both signify anchors, and they indicate that a string begins with the characters that follow and precede, respectively.

Our email expression includes the following anchors:
`^` to prepend the entire expression, following the first slash and `$` to append the entire expression preceding the final slash.

### Quantifiers
Quantifiers set the limits of the string that is being searched. * searches the pattern zero or more times, + searches the pattern one or more times, ? searches the pattern zero or one time, and curly braces {} proved a few different ways of searching:
 - { x } searches the pattern x number of times
 - { x, } searches the pattern a minimum of x times
 - { x, y } searches the pattern a minimum of x and maximum of y

Our email expression includes the following quantifiers:
`{2,6}`
The quantifier above tells the regex that the web suffix must be at least 2 characters long and at most 6 characters long. We know that it is only applied to the web suffix because it is contained within the corresponding grouping construct.

### Grouping Constructs
Used to separate searches of a string that fulfill different requirements, grouping constructs are either capturing or non-capturing. Simply, capturing groups grap the matched characters for potential reuse, and non capturing do not. 

Our email expression includes the following grouping constructs:
`([a-z0-9_\.-]+)`
`([\da-z\.-]+)`
`([a-z\.]{2,6})`

The first group specifies details of the email string that precede the @ symbol, the second looks for the string details of the domain call that occurs before the web suffix, and the third looks for the suffix itself. Looking between the constructs, we can see the @ and . symbols that format the email as a whole.


### Bracket Expressions
A set of square brackets [] indicates a range of characters that we would like to match. They are inclusive and are used to identify the characters that we want to include in a search, but they are not dependent on each other for matches. For example, [def] will find any string that includes d or e or f independtly of the others.

An important note here is that by adding the ^ character before a bracket, we can exclude the enclosed characters from search.

Our email expression includes the following bracket notation:
`[a-z0-9_\.-]`
`[\da-z\.-]`
`[a-z\.]`

Here, the first set of brackets define the characters that may be included in the given email which are any lowercase letters, any numbers, an underscore, a period which is escaped by the backslash, and a hyphen. 

The second searches for domain names and allows for any digits as indicated by the \d character class, any lowercase letters, another escaped period, and a hyphen.

The third identifies the site suffixes and so only includes lowercase letters, and a period.


### Character Classes
A character class defines a set of characters that may occur in a string search.

Our email expression includes the following character classes:

`\d` is added to the domain string search to include any numbers that might occur.


### The OR Operator
The OR operator | serves to make grouping constructs less rigid. For example, while (def):(uvw) strictly searches for matches, while (d|e|f):(u|v|w) will match any combination of the letters on their respective sides.

Our email expression does not include the OR operator.

### Flags
Flags are appended to the end of a regex, after the closing slash. These characters define any extra functionality, like g for a glabal search or i for case-insesitivity.

Our email expression does not include any flags.

### Character Escapes
The backslash \ functions to indicate that the following character should be interpreted as itself, rather than as part of an expression. For example, \{ indicates that the expression should match a curly brace as a character instead of as part of a quantifier.

Our email expression includes the following escapes:

`\.` We see this escape used a couple of times in order to include the period as a symbol in potential email strings without using it as a character class.

## Author

Phil Garip is a Brooklyn-based web developer and glass artist interested in the intersection of technology and craft. 
[Github](https://github.com/phil-garip)
