https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/description

Given a string s and an integer k, return the _maximum number of vowel letters in any substring of s with length k._

Vowel letters in English are 'a', 'e', 'i', 'o', and 'u'.

Example 1:

Input: s = "abciiidef", k = 3
Output: 3
Explanation: The substring "iii" contains 3 vowel letters.

Example 2:

Input: s = "aeiou", k = 2
Output: 2
Explanation: Any substring of length 2 contains 2 vowels.

Example 3:

Input: s = "leetcode", k = 3
Output: 2
Explanation: "lee", "eet" and "ode" contain 2 vowels.
 

Constraints:

1 <= s.length <= 105

s consists of lowercase English letters.

1 <= k <= s.length

### Solution

Sliding window

``` python
def maxVowels(self, s: str, k: int) -> int:
    vowels = "aeiou"
    maxNum = num = 0
    # Count num vowels in first substring of length k
    for i,c in enumerate(s[:k]):
        if c in vowels:
            num += 1
    maxNum = num
    # Update num vowels by maintaining a window of length k
    # Update maxNum
    for i in range(k, len(s)):
        if s[i-k] in vowels:
            num -= 1
        if s[i] in vowels:
            num += 1
        maxNum = max(maxNum, num)
    return maxNum
```
