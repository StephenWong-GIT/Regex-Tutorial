# Matching an Email

Regular expressions, or regex, are patterns used to find and match specific character combinations in strings or text. These expressions are very useful for when you want to find specific words in files of text. Regular expression can also be used to find ANY phone number, email, etc in text. They can do this by finding characters that follow a specific pattern that matches what you are looking for. In this tutorial, I will explain how regular expressions are created and how the are to be read and interpreted.

## Summary

The regex expression that I will be covering in this tutorial is the email regex. This regex finds any email in any form of text. As you may know, an email is split into three main components; the user's chosen name, the domain and the extension.

```
YummyWongTTV@gmail.com
```

Here we can split up the email like so:

- YummyWongTTV
- gmail
- com

After splitting the email into these three components we can see that they respectively match the components stated above.

Note: In an email there will always be an '@' between the user's chosen name and the domain. Same can be said about a '.' between the domain and the extension.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)

## Regex Components

This is how the email regex looks like.

```
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
```

Our regex has to be wrapped in forward slashes, '/'. Also, each component is put in parantheses,'()'. The brackets, '[]', will also be disussed later in [Bracket Expressions](#bracket-expressions).

If we loosely break up this regex:

- a-z: this string can contain lowercase letters from a to z.
- 0-9: this string can contain numbers from 0 to 9.
- \_.-: this string can contain an underscore, period and a hyphen. (We exclude the backslash since its purpose is to allow the period (.) to be used as a parameter not as a meta character.)

followed by an @, then:

- \d: any digit character, including numbers from 0 to 9.
- a-z: this string can contain lowercase letters from a to z.
- .-: this string can contain a period and hyphen.

followed by a ., then:

- a-z: this string can contain lowercase letters from a to z.
- .: this string can contain a period.

### Anchors

The characters ^ and $ are considered anchors.

```
'^' signifies a string that begins with the characters that follow it. An example, "^pie" will find any words that contain the letters 'p', 'i', and 'e' in that order, like 'piece'. The anchor, ^, will find words that contain the characters that immediately follow it.
```

```
'$' signifies a string that ends with the characters that precede it. An example, "wed$" would find the word 'followed'.
```

### Quantifiers

The final requirement of the regex that we have yet to talk about is the sequence of characters that appears before the $ anchor ({2,6}). That being said, quantifiers are always at the end of a component inside the square brackets. Meaning the '+' at the end of each component is a quantifier.

Quantifiers set the limits of the string that your regex matches. The quantifiers frequently include the minimum and maximum number of characters that your regex is looking for.

Quantifiers are inherently greedy, meaning they match as many occurrences of particular patterns as possible. They include the following:

- \*: Matches the pattern zero or more times
- +: Matches the pattern one or more times
- ?: Matches the pattern zero or one time
- {}: Curly brackets can provide three different ways to set limits for a match:
  - { n }: Matches the pattern exactly n number of times
  - { n, }: Matches the pattern at least n number of times
  - { n, x }: Matches the pattern from a minimum of n number of times to a maximum of x number of times

```
([a-z0-9_\.-]+)
```

Here, the quantifier is '+'.

```
([\da-z\.-]+)
```

Here, that quantifier is also '+'.

```
([a-z\.]{2,6})
```

Finally, the quantifier in this component is '{2,6}'.

Each of these quantifiers can be made lazy by adding the ? symbol after it, meaning it will match as few occurrences as possible. For example, the following strings would meet the requirements: 'hi', 'puddle', and 'supercalifragilisticexpialidocious'.

In our email regex we have two instances of '+' and that just means those components have to be AT LEAST one character long. Furthermore, in the third and final component we have {2,6} meaning the extension component has to between 2 and 6 characters. For example, these strings would meet the requirements: 'so', 'pie', 'case', 'march', and 'sauces'.

### Bracket Expressions

Anything inside square brackets ([]) are characters we wish to match. All components in our regex are contained in distinct square brackets. These 'components' are called bracket expressions. Bracket expressions, in other words, outline the charactes we want to include in our search. For example, [ace] will look for a string that includes 'a' or 'c' or 'e', regardless of the length of the string. Meaning, all of these strings would match: 'aaa', 'court', 'octopus' and 'cea'.

It's important to note that a bracket expression can be turned into a negative character group by adding the '^' symbol to the beginning of the expression inside the brackets. A common example is matching a string that doesnt include any vowels. The pattern [^aeiouaeiou] would find any strings that don't include lowercase or uppercase vowels.

## Author

- https://github.com/StephenWong-GIT
- https://github.com/StephenWong-GIT/Regex-Tutorial
