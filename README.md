# Regex Tutorial

Regex is like a mini programming language that involves regular expressions.  Regular expressions are pattern of notation that allow a user to describe and parse text.  Through Regex, a user can write expressions that can identify what text they want, while bypassing the the text they don't want.  A user can then combine those regular expressions within any programming language construct (Javascript, Python, Java, etc.) to manipulate text and execute a task.  A few example tasks include matching an email, searching for a phone number, replace dialog in text editors, and even in search engines.

## Summary
This assignment will be discussing matching a Hex Value, using the regular expression: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/
There will be explanation of each character in this expression and what represents, how and what it is looking for in the above expression.  
(Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.)

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
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors: ^
Looks at and matches the beginning of the string or line if there multiple flags used.

### Quantifiers: #?
Quantifiers are looking for matches between 0 and 1 of the previous characterl. In this case, the expression is looking for the # character, which is used in hex code values, such as #30D5C8 (the hex code for turquoise).

### OR Operator: |
Alteration/OR operator acts like a boolean OR and matches the expression right before or right after the | character. When looking at the hex value expression: the OR operator is saying it can match either 6 letters from a-f and numbers 0-9, OR 3 letters from a-f and numbers 0-9.  In other words, a hex value can have 6 numbers 0-9 (##008000 or #FFFFFF), 6 letters a-f, or 3 from each, such as #30D5C8.

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
