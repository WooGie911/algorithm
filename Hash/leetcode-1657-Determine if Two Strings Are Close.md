# 1657. Determine if Two Strings Are Close

## 문제 :

Two strings are considered close if you can attain one from the other using the following operations:

- Operation 1: Swap any two existing characters.
  For example, abcde -> aecdb
- Operation 2: Transform every occurrence of one existing character into another existing character, and do the same with the other character.
  - For example, aacabb -> bbcbaa (all a's turn into b's, and all b's turn into a's)

You can use the operations on either string as many times as necessary.

Given two strings, word1 and word2, return true if word1 and word2 are close, and false otherwise.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: word1 = "abc", word2 = "bca"
<br/>
Output: true
<br/>
Explanation: You can attain word2 from word1 in 2 operations.
<br/>
Apply Operation 1: "a<u>bc</u>" -> "a<u>cb</u>"
<br/>
Apply Operation 1: "<u>a</u>c<u>b</u>" -> "<u>b</u>c<u>a</u>"

<br/>

### Example 2:

Input: word1 = "a", word2 = "aa"
<br/>
Output: false
<br/>
Explanation: It is impossible to attain word2 from word1, or vice versa, in any number of operations.

<br/>

### Example 3:

Input: word1 = "cabbba", word2 = "abbccc"
<br/>
Output: true
<br/>
Explanation: You can attain word2 from word1 in 3 operations.
<br/>
Apply Operation 1: "ca<u>b</u>bb<u>a</u>" -> "ca<u>a</u>bb<u>b</u>"
<br/>
Apply Operation 2: "<u>c</u>aa<u>bbb</u>" -> "<u>b</u>aa<u>ccc</u>"
<br/>
Apply Operation 2: "<u>baa</u>ccc" -> "<u>abb</u>ccc"

<br/>

---

## 조건

### Constraints:

- 1 <= word1.length, word2.length <= 10^5
- word1 and word2 contain only lowercase English letters.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} word1
 * @param {string} word2
 * @return {boolean}
 */
var closeStrings = function(word1, word2) {
    if(word1.length !== word2.length) return false

    const map1 = new Map()
    const map2 = new Map()

    for(let i = 0; i < word1.length; i++){
        map1.set(word1[i], (map1.get(word1[i]) ?? 0) + 1)
        map2.set(word2[i], (map2.get(word2[i]) ?? 0) + 1)
    }

    for(let key of map1.keys()){
        if(!map2.has(key)) return false
    }

    return [...map1.values()].sort((a,b) => a - b).join('') === [...map2.values()].sort((a,b) => a - b).join('')
};
```
