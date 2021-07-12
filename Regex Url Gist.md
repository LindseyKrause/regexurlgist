# Regex: Matching a URL

This Gist describes the basic componenets of Regular Expressions (Regex) specifically as they pertain to matching a URL.  The Regex below will be examined and described.

```regex
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```

## Summary

Regular expressions or "Regexes" are at their core groups of letters, numbers, and charactars that represent a different specific pattern of letters, numbers, and charactars.  Although it sounds like what I just described is the same thing, there is a subtle difference between regular expressions beyond simply representing other combinations of letters, numbers, and characters.  Regexes focus on pattern, even when some of the pattern's characters are unknown.  The utility of such phrases lies in the ability to represent patterns in order to search for them.  Think of the find and replace tool on your document editor. When you ask "find all the instances of 'tree'" in my document.  Your computer doesn't necessarily know what a tree is, but it does know what a pattern is and excels at performing tedious tasks like checking each word in your document, letter by letter, to see if each word matches your search term.  In the case of tree, your computer can understand that given 4 characters, if the first one matches t, the second, r, the third, e, and the fourth, e, then that word matches what you are looking for.  What if you wanted to find all the instances of a url in your document, in order to compile a reference list? How would you do that since the pattern isn't exactly the same every time? This is where regular expressions truly shine.  

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


## Regex Components

### Anchors
Anchors can signify the beginning, end, word boundary, or not word boundary.  In the url regex, the / before and after the entire expression indicate the beginning and end of the expression. 
### Quantifiers
Quantifiers indicate, as stated, the quantity of the previous portion of the regex.  In our example where it says {2,6}, it is specifying that there should be between 2 and six characters (a-z) preceding the ".".  That means that as long as a url has between 2-6 letters --> www.example ***************
### OR Operator
Our example expression does not include an alternation, however, if we wanted to be more specific in our formatting, we could use the OR operator in the beginning of our expression to indicate that http:// OR https:// are both passable instances of a url we are looking for. 
### Character Classes
Our example expression uses a combination of the following to specify its parameters: 
Character set [ABC]
Range [A-Z]
Dot .
Match Any [\s\s]
Word \w
Digit \d

(img)

### Flags
This expression uses the multi-line flag by utilizing the ^ and the $ at the beginning and end of the expression, respectively.  These signify the beginning and end of a line or string. 
### Grouping and Capturing
Capture groups indicate a substring to be searched for and the URL expression has four capture groups each indicated by an opening and closing parenthesis. 

Capture groups allow you to refer to an entire sub-expression when needed.  In our case, for example, 

```regex
(https?:\/\/)?
```
the question mark is referring to the entire set of characters within the parentheses.  The question mark is a quantifier signifying that the search criteria is to look for anything that matches 0-1 of the preceding search within the parenthesis.  In our case, we are specifying that if a phrase begins with https://, it is to be included, but if it doesn't, it can also be included (in a case where the text does not include the https:// but is still a url).
### Bracket Expressions
Brackets are used to find a range of characters.  In the URL expression brackets are used to indicate three different sets of expressions: 

```regex
[\da-z\.-]
[a-z\.]
[\/\w \.-]
```
### Greedy and Lazy Match
Greedy and lazy describe quantifiers.  By default, quantifiers are "greedy" or they attempt to match as many portions of the expression as possible.  However, you can indicate that a search should match as few characters as possible by utilizing the question mark.  

In our example, the questions mark is used twice to indicate that as little should match as possible in the preceding set of characters (after https closing bracket and before the closing dollar side at the end of the expression).

```regex
^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$.
```

### Boundaries
Boundaries can indicate the beginning of an expression, the end of an expression, word boundaries, and not word boundaries.
Beginning ^ 
End $
Word Boundary \b
Not a Word Boundary \B

Our expression only uses the beginning and end boundaries. 

## Author

Lindsey Krause
Github: https://github.com/LindseyKrause

