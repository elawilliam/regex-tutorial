# Regex Tutorial

Regex, or regular expressions, is a sequence of characters that specifies a match pattern in text. These patterns are used by string-searching algorithms for locating or finding & replacing operations within strings, or for input validation.

## Summary

This tutorial will outline the basic elements of regex and explain how they function. The table of contents below provides an outline of all topics covered. Each component will include an example of how they can be used in every day coding scenarios. 

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
Anchors are special characters used to match positions within a string rather than matching actual characters. They do not match any specific characters, but instead represent positions such as the beginning or end of a line, word or string. Example: Dollar sign ($) matches the end of a line or the end of a string.

### Quantifiers
Quantifiers are symbols that specify the number of occurrences of a preceding element in a regular expression pattern. They allow you to define repetition patterns in the text you want to match. Example: Plus sign (+) matches one or more occurrences of the preceding element.

### OR Operator
OR operator denoted by the pipe symbol (|), is used to specify alternative patterns in a regular expression. It allows you to match either one pattern or another. Here's how it works: Pattern1|Pattern2 - This pattern will match either Pattern1 or Pattern2. If either of the patterns is found in the input text, it will result in a successful match. The OR operator can be used to create more flexible regex patterns by providing multiple options.

### Character Classes
Character classes are used to define a set of characters that can be matched at a specific position within a pattern. They allow you to specify a range or a set of characters that the regex engine will attempt to match. Character classes are enclosed in square brackets ([]). Here are the different types of character classes:

* Range Character Class: A range character class allows you to specify a range of characters using a hyphen (-) inside the square brackets.
Example: [a-z] matches any lowercase letter from "a" to "z".

* Negated Character Class: A negated character class matches any character that is not within the specified set of characters. It is denoted by a caret (^) as the first character inside the square brackets.
Example: [^0-9] matches any character that is not a digit.

* Predefined Character Classes: Regex provides predefined character classes that represent common sets of characters. Some of the commonly used predefined character classes are:

    * \d matches any digit (equivalent to [0-9]).
    * \D matches any non-digit character (equivalent to [^0-9]).
    * \w matches any word character (alphanumeric and underscore).
    * \W matches any non-word character (equivalent to [^A-Za-z0-9_]).
    * \s matches any whitespace character (space, tab, newline).
    * \S matches any non-whitespace character.
    * Example: \d\s\w matches a digit followed by a whitespace character and then a word character.

* Custom Character Class: You can also specify a custom set of characters inside the square brackets to create a character class.
Example: [abc] matches either "a", "b", or "c".

Character classes allow you to define specific sets of characters to match, making your regex patterns more precise and flexible.

### Flags
Flags are optional parameters that modify the behavior of the regex pattern matching. They are added after the closing delimiter of the regex pattern and are represented by a single letter. Flags provide additional control and functionality to the regex engine. Here are some commonly used flags:

* Case Insensitive (i): The "i" flag enables case-insensitive matching, allowing the regex pattern to match characters regardless of their case.
Example: /hello/i matches "hello", "Hello", "HELLO", and so on.

* Global (g): The "g" flag enables global matching, which means the regex pattern will match all occurrences in the input text, rather than stopping after the first match.
Example: /pattern/g matches all occurrences of "pattern" in the input text.

* Multiline (m): The "m" flag enables multiline matching. It changes the behavior of the "^" and "$" anchors to match the beginning and end of each line within the input text, rather than just the beginning and end of the entire string.
Example: /^pattern/m matches "pattern" if it appears at the beginning of any line in the input text.

* Dot All (s): The "s" flag, also known as the single-line flag, allows the dot (.) metacharacter to match newline characters as well.
Example: /.*/s matches any character, including newline characters.

* Unicode (u): The "u" flag enables full Unicode matching, including support for Unicode characters and properties.
Example: /\p{Script=Greek}/u matches any Greek Unicode character.

Flags are used to modify the default behavior of regex patterns and provide more control over matching operations. They allow you to perform case-insensitive matching, match globally, handle multiline input, and work with Unicode characters, among other functionalities.

### Grouping and Capturing
Grouping and capturing refer to the ability to group parts of a pattern together and capture the matched text for later use. Grouping is done using parentheses () in the regex pattern, and capturing allows you to extract the matched content from those groups. Here's how grouping and capturing work:

* Grouping: Parentheses () are used to create groups within a regex pattern. The contents within the parentheses form a subexpression and are treated as a single unit. This allows you to apply quantifiers or other regex constructs to a group of characters.
Example: (ab)+ matches one or more occurrences of the sequence "ab".

* Capturing: Capturing allows you to extract the matched content of specific groups from the regex pattern. Each group within parentheses creates a numbered capture group, starting from 1. The captured content can be accessed or referenced using backreferences.
Example: In the regex pattern (ab)+, if the input text is "ababab", the first captured group (group 1) will be "ab".

To reference captured groups within the regex pattern or in subsequent code, you can use backreferences. The syntax for a backreference is "\n", where "n" is the group number.

Example: In the regex pattern (\w+)\s+\1, the backreference \1 matches the same content as the first captured group. If the input text is "apple apple", it will result in a successful match.

Grouping and capturing in regex allow you to extract specific parts of the matched text or apply quantifiers and other operations to specific subexpressions. They are particularly useful when you need to work with different segments of the matched content or refer back to previously matched patterns.

### Bracket Expressions
Bracket expressions, also known as character classes, are used to define a set of characters that can be matched at a specific position within a pattern. They allow you to specify a range or a set of characters that the regex engine will attempt to match. Bracket expressions are enclosed in square brackets ([]). Here are the different types of bracket expressions:

* Range Bracket Expression: A range bracket expression allows you to specify a range of characters using a hyphen (-) inside the square brackets.
Example: [a-z] matches any lowercase letter from "a" to "z".

* Negated Bracket Expression: A negated bracket expression matches any character that is not within the specified set of characters. It is denoted by a caret (^) as the first character inside the square brackets.
Example: [^0-9] matches any character that is not a digit.

* Set Bracket Expression: A set bracket expression allows you to specify a set of characters that can be matched at that position. Each character within the square brackets represents a potential match.
Example: [abc] matches either "a", "b", or "c".

* Combination of Ranges and Sets: You can combine range and set expressions within a bracket expression to define a larger set of characters to match.
Example: [a-z0-9] matches any lowercase letter or digit.

Bracket expressions allow you to define specific sets of characters to match, making your regex patterns more precise and flexible. They are particularly useful when you need to match a specific range of characters or exclude certain characters from a match.

### Greedy and Lazy Match
The terms "greedy" and "lazy" refer to the behavior of quantifiers when matching patterns in the input text. They determine whether the regex engine should match as much text as possible (greedy) or as little as possible (lazy) to satisfy the pattern.

* Greedy Match: By default, quantifiers in regex are greedy, meaning they try to match as many occurrences of the preceding element as possible. They match as much text as they can while still allowing the overall pattern to match.
Example: In the regex pattern a+, the quantifier "+" is greedy. If the input text is "aaa", the greedy match will consume all three "a" characters.

* Lazy Match: To make a quantifier lazy, you can add a question mark "?" immediately after the quantifier. Lazy matching, also known as non-greedy or reluctant matching, causes the quantifier to match as little text as possible while still allowing the pattern to match.
Example: In the regex pattern a+?, the quantifier "+?" is lazy. If the input text is "aaa", the lazy match will consume only the first "a" character.

Lazy matching is particularly useful when you want to restrict the matching behavior to the smallest possible portion of the input text. It can be helpful in scenarios where you need to match specific patterns within larger patterns or when dealing with complex or nested patterns.

It's important to note that the greedy or lazy behavior only affects the matching behavior of quantifiers. Other parts of the regex pattern, such as anchors or specific character sequences, are not influenced by greediness or laziness.

### Boundaries
Boundaries are special constructs that allow you to match specific positions within a string without matching any actual characters. They are useful for specifying the location of text patterns within a larger string. Here are the commonly used boundary constructs in regex:

* Word Boundary (\b): The word boundary \b matches a position where a word starts or ends. It matches the zero-width position between a word character (\w) and a non-word character (\W), or between a word character and the start or end of the string.
Example: The regex pattern \bcat\b matches the word "cat" as a whole word but does not match it if it appears as part of a longer word like "cattle" or "category".

* Non-Word Boundary (\B): The non-word boundary \B matches a position where a word does not start or end. It matches the zero-width position between two word characters or two non-word characters.
Example: The regex pattern \Bcat\B matches the word "cat" only if it is not part of a longer word, such as "concatenate" or "scattered".

* Start of String/Line (^): The caret symbol ^ matches the position at the start of the string or the start of a line (when used with the multiline flag m). It does not match any characters.
Example: The regex pattern ^Hello matches "Hello" only if it appears at the beginning of a line or the start of the string.

* End of String/Line ($): The dollar sign $ matches the position at the end of the string or the end of a line (when used with the multiline flag m). It does not match any characters.
Example: The regex pattern world$ matches "world" only if it appears at the end of a line or the end of the string.

Boundary constructs in regex allow you to precisely specify the position of desired text patterns within a string without requiring the matching of actual characters. They are useful for finding whole words, matching at the start or end of a line, or ensuring specific boundaries are met in your regex patterns.

### Back-references
Back-references allow you to reference and reuse previously matched content within the same regex pattern. They enable you to refer back to captured groups (subexpressions within parentheses) and use their matched content in subsequent parts of the pattern. Back-references are denoted by the syntax "\n", where "n" is the group number.

Here's how back-references work in regex:

* Capture Groups: To create a capture group, you enclose a portion of the regex pattern within parentheses (). The captured content is assigned a group number based on the order of the opening parentheses, starting from 1.
Example: In the regex pattern (\w+)\s+\1, the parentheses create a capture group (group 1) that matches one or more word characters (\w+). The \1 is a back-reference that matches the exact content captured in group 1.

* Back-References: Back-references are used to refer to the captured content of a specific group within the regex pattern. The back-reference syntax is "\n", where "n" is the group number.
Example: In the regex pattern (\w+)\s+\1, the back-reference \1 matches the same content as the first captured group. If the input text is "apple apple", it will result in a successful match.

* Multiple Back-References: You can have multiple back-references within the same regex pattern to refer to different captured groups. Each back-reference will match the same content as its corresponding group.
Example: In the regex pattern (\w+)\s+(\w+)\s+\2\s+\1, there are two capture groups (group 1 and group 2) and two corresponding back-references (\2 and \1). The pattern will match if the same content is repeated in the input text.

Back-references are useful when you want to match repetitive or duplicated patterns within a string or enforce consistency between different parts of the pattern. They provide a way to reference and reuse previously matched content within the same regex pattern.

### Look-ahead and Look-behind
Look-ahead and look-behind assertions, also known as positive and negative assertions, are advanced features in regular expressions that allow you to match patterns based on the presence or absence of certain conditions without including them in the actual match. Look-ahead and look-behind assertions are zero-width assertions, which means they don't consume any characters during matching. They only determine whether a pattern matches at a particular position in the input text.

* Positive Look-Ahead (?=): Positive look-ahead is denoted by "(?=)" and asserts that the pattern inside the parentheses must be followed by a specific condition without including it in the match. It matches if the condition is met.
Example: The regex pattern foo(?=bar) matches "foo" only if it is followed by "bar". In the input text "foobar", "foo" is matched, but "foo" in "foobaz" is not.

* Negative Look-Ahead (?!): Negative look-ahead is denoted by "(?!)" and asserts that the pattern inside the parentheses must not be followed by a specific condition. It matches if the condition is not met.
Example: The regex pattern foo(?!bar) matches "foo" only if it is not followed by "bar". In the input text "foobaz", "foo" is matched, but "foo" in "foobar" is not.

* Positive Look-Behind (?<=): Positive look-behind is denoted by "(?<=)" and asserts that the pattern inside the parentheses must be preceded by a specific condition without including it in the match. It matches if the condition is met.
Example: The regex pattern (?<=foo)bar matches "bar" only if it is preceded by "foo". In the input text "foobar", "bar" is matched, but "bar" in "bazbar" is not.

* Negative Look-Behind (?<!): Negative look-behind is denoted by "(?<!)" and asserts that the pattern inside the parentheses must not be preceded by a specific condition. It matches if the condition is not met.
Example: The regex pattern (?<!foo)bar matches "bar" only if it is not preceded by "foo". In the input text "bazbar", "bar" is matched, but "bar" in "foobar" is not.

Look-ahead and look-behind assertions provide powerful capabilities to include or exclude patterns based on the context before or after them. They are particularly useful when you need to match patterns based on specific conditions without including those conditions in the actual match.

## Author

This tutorial was compiled by Ela William (https://github.com/elawilliam/regex-tutorial) with the use of Chat GPT.

If you have any questions or feedback, please feel free to leave a comment or reach out to me directly.