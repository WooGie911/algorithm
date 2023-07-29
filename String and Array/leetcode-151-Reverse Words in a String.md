# 151. Reverse Words in a String

## 문제 :

Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters.
<br/>
The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words.
<br/>
The returned string should only have a single space separating the words. Do not include any extra spaces.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: s = "the sky is blue"
<br/>
Output: "blue is sky the"

<br/>

### Example 2:

Input: s = " hello world "
<br/>
Output: "world hello"
<br/>
Explanation: Your reversed string should not contain leading or trailing spaces.

<br/>

### Example 3:

Input: s = "a good example"
<br/>
Output: "example good a"
<br/>
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.

<br/>

---

## 조건

### Constraints:

- 1 <= s.length <= 10^4
- s contains English letters (upper-case and lower-case), digits, and spaces ' '.
- There is at least one word in s.

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    const sArr = s.split(" ")
    let res = ""

    for(let i=sArr.length-1 ; i>=0 ; i--){
        if (sArr[i] != "" && sArr[i] != " "){
            res += sArr[i] + " "
        }
    }

    return res.trim()
};
```
