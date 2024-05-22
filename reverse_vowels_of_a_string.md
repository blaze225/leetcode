https://leetcode.com/problems/reverse-vowels-of-a-string/description

Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

Example 1:

Input: s = "hello"
Output: "holle"

Example 2:

Input: s = "leetcode"
Output: "leotcede"
 

Constraints:

1 <= s.length <= 3 * 105

s consist of printable ASCII characters.

### Solution

Two pointer approach.

``` python
def reverseVowels(self, s: str) -> str:
    s_list = list(s)
    # Initialize pointers
    i = 0
    j = len(s) - 1
    vowels = "aAeEiIoOuU"
    while i<j:
        # Find the indices with a vowel
        while s[i] not in vowels and i<j:
            i += 1
        while s[j] not in vowels and i<j:
            j -= 1
        # Swap
        s_list[i], s_list[j] = s_list[j], s_list[i]
        i += 1
        j -= 1
    return ''.join(s_list)
```
