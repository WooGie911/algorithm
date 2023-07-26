# 345. Reverse Vowels of a String

## 문제 :

Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: s = "hello"
<br/>
Output: "holle"

<br/>

### Example 2:

Input: s = "leetcode"
<br/>
Output: "leotcede"

<br/>

---

## 조건

### Constraints:

- 1 <= s.length <= 3 \* 10^5
- s consist of printable ASCII characters.

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} s
 * @return {string}
 */
var reverseVowels = function(s) {
    const vowels = ['a', 'e', 'i', 'o', 'u','A', 'E', 'I', 'O', 'U' ]

    const subArr = []
    let res = ''

    for(let i=0 ; i<s.length ; i++){
        if(vowels.includes(s[i])){
            subArr.push(s[i])
        }

    }


    for(let j=0 ; j<s.length ; j++){
        if(vowels.includes(s[j])){
            const vowel = subArr.pop()
            res += vowel
        }else{
            res += s[j]
        }
    }

    return res
};
```
