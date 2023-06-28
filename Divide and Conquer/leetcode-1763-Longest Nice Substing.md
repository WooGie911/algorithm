# 1763. Longest Nice Substring

## 문제 :

A string s is nice if, for every letter of the alphabet that s contains, it appears both in uppercase and lowercase. For example, "abABB" is nice because 'A' and 'a' appear, and 'B' and 'b' appear. However, "abA" is not because 'b' appears, but 'B' does not.

Given a string s, return the longest substring of s that is nice. If there are multiple, return the substring of the earliest occurrence. If there are none, return an empty string.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: s = "YazaAay"
<br/>
Output: "aAa"
<br/>
Explanation: "aAa" is a nice string because 'A/a' is the only letter of the alphabet in s, and both 'A' and 'a' appear.
<br/>
"aAa" is the longest nice substring.

<br/>

### Example 2:

Input: s = "Bb"
<br/>
Output: "Bb"
<br/>
Explanation: "Bb" is a nice string because both 'B' and 'b' appear. The whole string is a substring.

<br/>

### Example 3:

Input: s = "c"
<br/>
Output: ""
<br/>
Explanation: There are no nice substrings.

<br/>

---

## 조건

### Constraints:

- 1 <= s.length <= 100
  <br/>
- s consists of uppercase and lowercase English letters.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} s
 * @return {string}
 */

var longestNiceSubstring = function(s) {
    if (s.length <= 1) {
        return '';
    }

    const fun = (array)=> {
        const sArr = array.split('');
        const sSet = new Set(sArr);

        for (let i=0;i<=array.length-1;i++) {
            if (sSet.has(sArr[i].toLowerCase()) && sSet.has(sArr[i].toUpperCase())) {
                continue;
            }

            const subS1 = fun(array.slice(0, i));
            const subS2 = fun(array.slice(i+1));

            return subS1.length >= subS2.length ? subS1 : subS2;
        }

        return array
    }
    return fun(s);
};

```
