
# String.lua - Explanatory Documentation

This module provides utility functions for string manipulation in Roblox.  
Recommended usage: server-side or client-side for handling text and formatting.

# Functions

## String.Split(str, sep)
Splits a string into an array using a separator.  
- **str** : Input string  
- **sep** : Separator pattern (default whitespace)  
- Returns **table of substrings**.

## String.Trim(str)
Removes leading and trailing spaces from a string.  
- **str** : Input string  
- Returns **trimmed string**.

## String.Capitalize(str)
Capitalizes the first character of a string.  
- **str** : Input string  
- Returns **capitalized string**.

## String.ToUpper(str)
Converts a string to uppercase.  
- **str** : Input string  
- Returns **uppercase string**.

## String.ToLower(str)
Converts a string to lowercase.  
- **str** : Input string  
- Returns **lowercase string**.

## String.PadLeft(str, len, char)
Pads the string on the left with a character to reach a desired length.  
- **str** : Input string  
- **len** : Target length  
- **char** : Padding character (default space)  
- Returns **padded string**.

## String.PadRight(str, len, char)
Pads the string on the right with a character to reach a desired length.  
- **str** : Input string  
- **len** : Target length  
- **char** : Padding character (default space)  
- Returns **padded string**.

## String.Replace(str, search, repl)
Replaces all occurrences of a substring with another.  
- **str** : Input string  
- **search** : Substring to replace  
- **repl** : Replacement string  
- Returns **new string**.

## String.StartsWith(str, prefix)
Checks if a string starts with a given prefix.  
- **str** : Input string  
- **prefix** : Prefix to check  
- Returns **boolean**.

## String.EndsWith(str, suffix)
Checks if a string ends with a given suffix.  
- **str** : Input string  
- **suffix** : Suffix to check  
- Returns **boolean**.

## String.Count(str, substr)
Counts occurrences of a substring in a string.  
- **str** : Input string  
- **substr** : Substring to count  
- Returns **integer**.

## String.Reverse(str)
Reverses a string.  
- **str** : Input string  
- Returns **reversed string**.

## String.Join(t, sep)
Joins a table of strings into a single string with a separator.  
- **t** : Table of strings  
- **sep** : Separator (default empty string)  
- Returns **joined string**.

## String.IsEmpty(str)
Checks if a string is empty or nil.  
- **str** : Input string  
- Returns **boolean**.

# Example Usage
local strUtil = require(game.ReplicatedStorage.Lib.String)

print(strUtil.Split("hello world", " ")[1]) -- "hello"
print(strUtil.Trim("  hello  ")) -- "hello"
print(strUtil.Capitalize("hello")) -- "Hello"
print(strUtil.PadLeft("42", 5, "0")) -- "00042"
print(strUtil.Replace("foo bar foo", "foo", "baz")) -- "baz bar baz"
print(strUtil.StartsWith("hello", "he")) -- true
print(strUtil.Count("banana", "a")) -- 3
