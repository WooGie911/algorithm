# 1143. Longest Common Subsequence

## 문제 :

Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".

A common subsequence of two strings is a subsequence that is common to both strings.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: text1 = "abcde", text2 = "ace"
<br/>
Output: 3  
<br/>
Explanation: The longest common subsequence is "ace" and its length is 3.

<br/>

### Example 2:

Input: text1 = "abc", text2 = "abc"
<br/>
Output: 3
<br/>
Explanation: The longest common subsequence is "abc" and its length is 3.

<br/>

### Example 3:

Input: text1 = "abc", text2 = "def"
<br/>
Output: 0
<br/>
Explanation: There is no such common subsequence, so the result is 0.

<br/>

---

## 조건

### Constraints:

- 1 <= text1.length, text2.length <= 1000
- text1 and text2 consist of only lowercase English characters.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} text1
 * @param {string} text2
 * @return {number}
 */
var longestCommonSubsequence = function(text1, text2) {
    const dp = Array.from({length: text1.length + 1}, () => new Array(text2.length + 1).fill(0));

    for (let i = 1; i < text1.length + 1; i++) {
        for (let j = 1; j < text2.length + 1; j++) {
           if (text1[i - 1] === text2[j - 1]) {
               dp[i][j] = dp[i-1][j-1] + 1;
           } else {
               dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
           }
        }
    }

    return dp[text1.length][text2.length];
};
```
