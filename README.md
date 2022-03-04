# Regex Tutorial

Regex is like a mini programming language that involves regular expressions.  Regular expressions are pattern of notation that allow a user to describe and parse text.  Through Regex, a user can write expressions that can identify what text they want, while bypassing the the text they don't want.  A user can then combine those regular expressions within any programming language construct (Javascript, Python, Java, etc.) to manipulate text and execute a task.  A few example tasks include matching an email, searching for a phone number, replace dialog in text editors, and even in search engines.

## Summary
Regular expressions can be quite useful when searching and updating, as discussed above, and is therefore a great concept to grasp for any technical field.  To name one, programmers can utilize it in VS Code within the 'Find' function, however one could also use Regex for many other cases.

This assignment will be discussing matching a Hex Value, using the Regex regular expression: 
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
There will be explanation of each character in this expression,what each represents, how and what it is looking for in the above expression.  


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

### Anchors
Looks at and matches the beginning or end of the string or line if there multiple flags used.  Typically this means it anchors the position, not the character.  However, an anchor can also be used to match a word boundary, such as the position between a word character and/or non-word character.

In the hex value expression: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ the ^ character appears to anchor the beginning of the expression, and $ marks the end of the expression or string.

### Quantifiers

Quantifiers (such as +, *, ? and |)are typically looking for matches between 0 and 1 of the previous character. There is some further specificity within those characters. The metacharacter + means one or more of the preceding items; * means try to match any number, including none of the previous item; the ? means optional, and can also mean match as few characters as possible. The | character treats the item as a the boolean "OR", and it refers to the expression before or after the |, it can refer to specific items or the entire expression.  The # is mostly known as a delimiter in this context, as is the very beginning symbol in regular expressions, the forward slash (/), and they typically mean to mark the boundary of the expression.  

In the case of the expression above, the expression is looking for the # character, which is sometimes used in hex code values, such as #30D5C8 (the hex code for turquoise).  As sometimes hex values are written without the # character, the ? is logical as it may or may not be included in the hex value (Eg: #FFFF00  is sometimes written as FFFF00).

### OR Operator
Alteration/OR operator acts like a boolean OR and matches the expression right before or right after the | character. 

When looking at the hex value expression: the OR operator is saying it can match either 6 letters from a-f and numbers 0-9, OR 3 letters from a-f and numbers 0-9.  In other words, a hex value can have 6 numbers from 0 to 9 (##008000), 6 letters from a to f (#FFFFFF), or 3 from each, such as #30D5C8. Just the expression itself is a  pretty brillant way to explain it--writing it out in English almost feels clumsy after studying it in this way.

### Character Classes

Character classes are the easiest to explain, as they simply match a character from a specific set, which can be digits, letters (upper and lower case).  There are other designations within the set such as for signifying a range, matching any other characters; there are even some designations for words and not-words, as well as digits and not-digits.

In the case of the hex expression: [a-f0-9]{6} means looking for 6 six letter characters a-f (as hex value letters only go up to the letter f), or 6 digits ranging between 0 and 9.  The next part of the expression says: |[a-f0-9]{3} which reads as OR three letter characters ranging from a-f, or three digit characters ranging from 0 through 9.


### Flags

Flags, or expression flags, can change how the expression is translated.  Another way to think of a flag is an optional parameter that changes the behavior of the default way the expression searches.  There a a few specific flags to note, such as:  g, which matches the pattern several times,  and i which makes the expression case insensitive.  An example of this is found in the expression: /^[\s\S]+$/m, where the forward slashes signify the entire expression, the m at the end will return matches that can span multiple lines, as this tells the seach to match the start and end of any line.

### Grouping and Capturing
 
Grouping is a way to handle multiple characters as a single unit, instead of one at a time.  This can only be done by using paratheses.  Capturing is a half step further than grouping, in that it groups that are captured can be used later on in the regex for matching or can be used as a replacement unit.  Capturing differs from just matching, as beyond just matching the string, it can return something, such searching for an email.

For example: /(\W|^)[\w.\-]{0,25}@(yahoo|hotmail|gmail)\.com(\W|$)/ 
The snippet (yahoo|hotmail|gmail) searches for the grouping of email providers and formats them into domains.  That snippet will help return any email address containing those specified domains.

### Bracket Expressions

Bracket expressions are a list of characters encapsulated by the [ and ], and it matches characters in the list or range provided inside the brackets.  The range of expression within the brackets is two characters separated with a hyphen, and means any character from the beginning and end of the specified range.

As a type of bracket, it's necessary to mention curly braces here, as they are important in the hex value expression-- they are general reptitiion quantifiers, which specifiy a minimum and maximum of permitted matches.  The snippet from the hex value example [a-f0-9], shows the list of characters and specified ranges inside the brackets, meaning the search will be for the letters a-f and 0-9.  The {3} and {6} refers to the minimum and maximum of those provided ranges.

### Greedy and Lazy Match

By default, regular expression quantifiers are greedy, which means they will match as many characters as possible.  The need for limitations then becomes apparent, as a search will need to have more specificity written into it to be useful for clear-cut results.  Lazy matching then, will cause the expression to match as few characters as possible.

The code snippet "#?" from the preceding hex value example, means that the expression can target a # symbol in the search, but that it doesn't necessarly need to be there, as hex values are not always written with a # character at the beginning.  For example, either of these would be acceptable with in the search: #30D5C8 or 30D5C8.

### Boundaries

Boundaries, such as /b  or /B, are similar to anchors (^, $), are assertions about the current position in the string.  While anchors are there to demarcate or assert the beginning or end in the string, boundaries make a pronoucement about what can be matched to the left and to the right of the current position in the given string. The boundary demarcation /b is a word boundary that matches the position of a character, usually a letter, digit or underscore.  It also can mark the spot between the word character and non-word character.  The other demarcation /B, is a non-word boundary, which matches a position and not a character.

An example of this is /Bcat/B, which will find the word "cat", even when fully enveloped  by other word characters.  For instance the word "humidification" would be selected here, as it does contain the word "cat" inside of other letters.


### Back-references

### Look-ahead and Look-behind

## Author:

Jennifer Emanuele, Full Stack Engineering bootcamp student (OSU); RN, BSN.
https://github.com/jenemanuele/
