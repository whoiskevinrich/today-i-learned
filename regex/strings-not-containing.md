# Capturing Strings not containing a substring

## Problem

Using windows PowerRename, I wanted to rename all files that did not contain the substring `[S` in the filename.

## Solution

Use the following regex pattern to match all strings that do not contain the substring `[S`:

```regex
^(?!.*\[S)
```

-   `^` asserts position at the start of a line.
-   `(?!.*\[S)` is a negative lookahead that asserts that the string does not contain the substring `[S`.
