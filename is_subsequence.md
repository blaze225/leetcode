https://leetcode.com/problems/is-subsequence/description

Given two strings s and t, return true if s is a **subsequence** of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

Example 1:

Input: s = "abc", t = "ahbgdc"
Output: true

Example 2:

Input: s = "axc", t = "ahbgdc"
Output: false
 
Constraints:

0 <= s.length <= 100

0 <= t.length <= 104

s and t consist only of lowercase English letters.
 
### Solution

Two pointer approach.

``` python
def isSubsequence(self, s: str, t: str) -> bool:
    # Initialize pointers
    p1 = p2 = 0
    # Increment p1 only when a match is found
    while p2 < len(t) and p1 < len(s):
        if t[p2] == s[p1]:
            p1 += 1
        p2 += 1
    # If we reached the end of string s then all characters are present in string t
    return p1 == len(s)
```
