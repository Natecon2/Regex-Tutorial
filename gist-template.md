# Regex Tutorial

In the world of web development and text processing, regular expressions, often referred to as regex, are a set of tools for pattern matching and text manipulation. They allow you to define complex search patterns within strings. In this tutorial, I will explain more in depth on what you can expect from Regex!

## Summary

I will cover regular expressions, and explain the systems behind their syntax and usage. I will cover various components and concepts used in regex, providing clear explanations and practical examples to help you grasp their functionality.

Here is an example!

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

This regex will serve as the guiding example as I explain its elements.

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

### Anchors

Anchors in regular expressions are special characters or constructs that don't match any characters in the string but rather represent specific positions within the string. They are used to specify where in the string a match should begin or end. Anchors "anchor" (Get it?) the regex pattern to a particular location in the input string.

The Caret (^) Anchor: This anchor asserts that the regex pattern must start at the beginning of the string. It does not consume any characters but enforces that the match begins from the start.

Example: /^hello/   // Matches "hello" at the beginning of a string

The Dollar ($) Anchor: This anchor asserts that the regex pattern must end at the end of the string. Similar to the caret anchor, it does not consume characters but requires the match to conclude at the string's end.

Example: /world$/   // Matches "world" at the end of a string

These anchors are incredibly useful when you need to ensure that your regex pattern matches precisely where you want it to within a given string. They provide control and specificity in defining the location of matches.

### Quantifiers

Quantifiers in regular expressions are used to specify how many times a character or group of characters should occur in the input string. They allow you to define the exact quantity or a range of occurrences of a character or group. Quantifiers help make your regex patterns more flexible and adaptable to different scenarios.

The Asterisk (*) Quantifier: The asterisk quantifier specifies that the preceding character or group can occur zero or more times. It matches as many occurrences as possible.

Example: /ba*t/    // Matches "bt", "bat", "baat", "baaat", and so on

The Plus (+) Quantifier: The plus quantifier specifies that the preceding character or group must occur at least once but can occur multiple times.

Example: /ba+t/    // Matches "bat", "baat", "baaat", and so on, but not "bt"

The Question Mark (?) Quantifier: The question mark quantifier specifies that the preceding character or group is optional and can occur zero or one time.

Example: /colou?r/  // Matches both "color" and "colour"

The Curly Braces ({}) Quantifier: The curly braces quantifier allows you to specify an exact number of occurrences or a range of occurrences.

{n}: Matches exactly n occurrences.
{n,}: Matches at least n occurrences.
{n,m}: Matches between n and m occurrences.
Examples: /\d{3}/      // Matches three consecutive digits like "123"
/\w{2,4}/    // Matches word characters with a length between 2 and 4

Quantifiers are powerful tools for defining patterns that involve repetition or varying lengths of characters in your input string. They provide flexibility and precision in matching text.

### Grouping Constructs

Grouping constructs in regular expressions allow you to treat multiple characters or sub-patterns as a single unit. They are enclosed within parentheses and serve several essential purposes.

Grouping for Alternation: You can use grouping to specify alternatives within a pattern using the | (pipe) operator. It allows you to match one of several patterns.

Example:/(cat|dog)/   // Matches either "cat" or "dog"

Quantification: You can apply quantifiers to a group to specify how many times that group should occur.

Example: /(abc){2,4}/  // Matches "abcabc", "abcabcabc", or "abcabcabcabc"

Capturing Groups: When you enclose a part of your regex pattern within parentheses, it creates a capturing group. Capturing groups are used to extract specific portions of the matched text.

Example: /(\d{2})-(\d{2})-(\d{4})/   // Matches and captures a date in the format "DD-MM-YYYY"

Non-Capturing Groups: To group patterns without capturing them, you can use non-capturing groups denoted by (?:...). This is useful when you want to group for quantification or alternation but don't need to extract the matched text.

Example: /(?:https?|ftp):\/\/(\S+)/  // Matches URLs but captures only the domain part

Grouping constructs are invaluable for structuring complex regex patterns and performing more advanced operations. They enable you to create organized and efficient regex expressions.

### Bracket Expressions

Bracket expressions in regular expressions, often referred to as character classes, allow you to specify a set of characters that can match a single character in the input string. They are enclosed within square brackets and provide a way to define a custom character set for matching.

Matching Single Characters: A bracket expression matches a single character that is any one of the characters listed inside the brackets.

Example: /[aeiou]/    // Matches any vowel character: a, e, i, o, or u

Ranges: You can specify a range of characters using a hyphen inside the brackets. For example, [a-z] matches any lowercase letter from 'a' to 'z'.

Example: /[0-9]/     // Matches any digit character: 0, 1, 2, ..., 9
/[A-Z]/     // Matches any uppercase letter

Negation: Placing a caret ^ as the first character inside the brackets negates the character class. It matches any character that is NOT in the specified set.

Example: /[^0-9]/    // Matches any character that is NOT a digit
/[^aeiou]/  // Matches any character that is NOT a vowel

Combining Characters: You can combine characters and ranges within the same character class.

Example: /[A-Za-z]/   // Matches any uppercase or lowercase letter
/[0-9A-F]/   // Matches hexadecimal digits (0-9 and A-F)

Bracket expressions are versatile and allow you to define custom character sets for matching specific patterns within your input strings. They are essential for tasks like validating, extracting, or replacing characters in text.

### Character Classes

Character classes in regular expressions provide a concise way to match specific groups of characters commonly used in text patterns. They are represented by a shorthand notation that simplifies complex character sets.

\d - Digit Character Class: Matches any digit character (0-9).

Example: /\d+/    // Matches one or more digits

\w - Word Character Class: Matches any word character, which includes letters (both uppercase and lowercase), digits, and underscores.

Example: /\w+/    // Matches one or more word characters

\s - Whitespace Character Class: Matches any whitespace character, including spaces, tabs, and line breaks.

Example: /\s+/    // Matches one or more whitespace characters

\D - Non-Digit Character Class: Matches any character that is not a digit (0-9).

Example: /\D+/    // Matches one or more non-digit characters

\W - Non-Word Character Class: Matches any character that is not a word character (letters, digits, underscores).

Example: /\W+/    // Matches one or more non-word characters

\S - Non-Whitespace Character Class: Matches any character that is not a whitespace character.

Example: /\S+/    // Matches one or more non-whitespace characters

[...] - Custom Character Class: You can create custom character classes by enclosing a set of characters inside square brackets.

Example: /[aeiou]/  // Matches any vowel character (a, e, i, o, u)
/[0-9A-F]/  // Matches hexadecimal digits (0-9 and A-F)

Character classes are handy for simplifying regex patterns and making them more readable. They provide a concise way to match specific types of characters within a string.

### The OR Operator

In regular expressions, the OR operator, represented by the pipe symbol |, allows you to specify alternatives within a pattern. It enables you to match one of several expressions. This is particularly useful when you want to search for multiple patterns in your input string.

expression1 | expression2: Matches either expression1 or expression2.

Example 1: /banana|apple/  // Matches either "banana" or "apple"

Example 2: /cat|dog/       // Matches either "cat" or "dog"

You can use parentheses to group expressions and control the scope of the OR operator:

Example: /(apple|banana) juice/  // Matches "apple juice" or "banana juice"

The OR operator is versatile and allows you to create flexible patterns that can match multiple alternatives within your input text. It simplifies the process of searching for various possibilities in a single regular expression.

### Flags

Flags in regular expressions are optional parameters that modify how the regex engine interprets the pattern. They are placed after the closing slash / of the regular expression and are usually represented by a single letter. Each flag serves a specific purpose and alters the behavior of the regex pattern matching.

i - Case-Insensitive Flag: This flag makes the pattern matching case-insensitive. It allows the regex to match both uppercase and lowercase characters.

Example: /apple/i  // Matches "apple", "Apple", "aPpLe", etc.

g - Global Flag: The global flag tells the regex engine to find all matches in the input string, rather than stopping after the first match.

Example: /cat/g  // Matches all occurrences of "cat" in the input string

m - Multiline Flag: The multiline flag affects how ^ and $ anchors work. With this flag, ^ matches the start of each line, and $ matches the end of each line within a multiline input.

Example: /^cat/gm  // Matches "cat" at the start of each line

s - Dot-All Flag: The dot-all flag allows the . character to match any character, including newline characters (\n). By default, . does not match newlines.

Example: /a.b/s  // Matches "a\nb" as a single match

Flags are essential for tailoring regular expressions to specific requirements. They provide control over case sensitivity, global matching, multiline behavior, and more, making regex patterns more versatile and adaptable to different scenarios.

### Character Escapes

Character escapes in regular expressions are used to match specific characters that have special meanings in regex. These characters include metacharacters like ., *, +, ?, and others. To match these characters literally, you can use the backslash \ followed by the character you want to escape.

. - Escaping the Dot: In regex, the dot . is a metacharacter that matches any character except for a newline. To match a literal dot, you can escape it with a backslash \..

Example: /\d+\.\d+/  // Matches numbers with a decimal point, like "3.14"

* - Escaping the Asterisk: The asterisk * is a quantifier in regex that specifies zero or more occurrences of the preceding character or group. To match a literal asterisk, you can escape it with a backslash \*.

Example: /a\*b/  // Matches "a*b" as a literal string

+ - Escaping the Plus: Similar to the asterisk, the plus + is a quantifier that specifies one or more occurrences. To match a literal plus, escape it with a backslash \+.

Example: /1\+1/  // Matches "1+1" as a literal string

? - Escaping the Question Mark: The question mark ? is a quantifier that specifies zero or one occurrence. To match a literal question mark, escape it with a backslash \?.

Example: /May I help\?/  // Matches "May I help?" as a literal string

\ - Escaping the Backslash: The backslash itself is a special character in regex used for escaping. To match a literal backslash, escape it with another backslash \\.

Example: /\\/  // Matches a single backslash

By using character escapes, you can match these special characters literally in your regex patterns, ensuring that they are treated as regular characters and not interpreted as metacharacters.

## Author

Hello! my name is Nathan and this was written by me! Here is my GitHub profile for more! https://github.com/Natecon2
