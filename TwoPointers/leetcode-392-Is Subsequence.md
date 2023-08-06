# 392. Is Subsequence

## 문제 :

Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: s = "abc", t = "ahbgdc"
<br/>
Output: true

<br/>

### Example 2:

Input: s = "axc", t = "ahbgdc"
<br/>
Output: false

<br/>

---

## 조건

### Constraints:

- 0 <= s.length <= 100
- 0 <= t.length <= 10^4
- s and t consist only of lowercase English letters.

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isSubsequence = function(s, t) {

    if(s.length <1){
        return true
    }

    let i =0

    for(let j=0 ; j<t.length ; j++){
        if(s[i] === t[j]){
            i++
        }
        if(i === s.length){
            return true
        }
    }

    return false

};
```
