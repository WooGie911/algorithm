# 2390. Removing Stars From a String

## 문제 :

You are given a string s, which contains stars \*.

In one operation, you can:

- Choose a star in s.
- Remove the closest non-star character to its left, as well as remove the star itself.

Return the string after all stars have been removed.

Note:

- The input will be generated such that the operation is always possible.
- It can be shown that the resulting string will always be unique.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: s = "leet\**cod*e"
<br/>
Output: "lecoe"
<br/>
Explanation: Performing the removals from left to right:

- The closest character to the 1st star is 't' in "lee<u>**t**</u>\*\*cod\*e". s becomes "lee\*cod\*e".
- The closest character to the 2nd star is 'e' in "le<u>**e**</u>\*cod\*e". s becomes "lecod\*e".
- The closest character to the 3rd star is 'd' in "leco<u>**d**</u>\*e". s becomes "lecoe".
  There are no more stars, so we return "lecoe".

<br/>

### Example 2:

Input: s = "erase**\***"
<br/>
Output: ""
<br/>
Explanation: The entire string is removed, so we return an empty string.

<br/>

---

## 조건

### Constraints:

- 1 <= s.length <= 10^5
- s consists of lowercase English letters and stars \*.
- The operation above can be performed on s.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} s
 * @return {string}
 */
var removeStars = function(s) {

    const sArr = s.split("")
    let rArr = []

    for(let i=0; i<sArr.length ; i++){
        if(sArr[i]==="*"){
            rArr.pop()
        }else{
            rArr.push(sArr[i])
        }
    }

    return rArr.join('')

};
```
