# 1456. Maximum Number of Vowels in a Substring of Given Length

## 문제 :

Given a string s and an integer k, return the maximum number of vowel letters in any substring of s with length k.

Vowel letters in English are 'a', 'e', 'i', 'o', and 'u'.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: s = "abciiidef", k = 3
<br/>
Output: 3
<br/>
Explanation: The substring "iii" contains 3 vowel letters.

<br/>

### Example 2:

Input: s = "aeiou", k = 2
<br/>
Output: 2
<br/>
Explanation: Any substring of length 2 contains 2 vowels.

<br/>

### Example 3:

Input: s = "leetcode", k = 3
<br/>
Output: 2
<br/>
Explanation: "lee", "eet" and "ode" contain 2 vowels.

<br/>

---

## 조건

### Constraints:

- 1 <= s.length <= 10^5
- s consists of lowercase English letters.
- 1 <= k <= s.length

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} s
 * @param {number} k
 * @return {number}
 */

var maxVowels = function(s, k) {
    let Vowels = ['a', 'e', 'i', 'o', 'u','A', 'E', 'I', 'O', 'U']
    let maxCount = 0
    let start = 0
    let count = 0

    for (let end = 0; end < s.length; end++) {
	    if (Vowels.includes(s[end])) {
            count ++
        }

        if (end - start + 1 > k) {
            if(Vowels.includes(s[start])) {
                count --
            }
            start ++
        }
        maxCount = Math.max(maxCount, count)

        if (maxCount == k) return maxCount;
    }
    return maxCount;
};
```
