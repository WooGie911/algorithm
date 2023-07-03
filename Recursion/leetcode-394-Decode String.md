# 394. Decode String

## 문제 :

Given an encoded string, return its decoded string.

The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc.
<br/>
Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k.
<br/>
For example, there will not be input like 3a or 2[4].

The test cases are generated so that the length of the output will never exceed 10^5.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: s = "3[a]2[bc]"
<br/>
Output: "aaabcbc"

<br/>

### Example 2:

Input: s = "3[a2[c]]"
<br/>
Output: "accaccacc"

<br/>

### Example 3:

Input: s = "2[abc]3[cd]ef"
<br/>
Output: "abcabccdcdcdef"

<br/>

---

## 조건

### Constraints:

- 1 <= s.length <= 30
- s consists of lowercase English letters, digits, and square brackets '[]'.
- s is guaranteed to be a valid input.
- All the integers in s are in the range [1, 300].

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} s
 * @return {string}
 */
var decodeString = function(s) {

    let stringDecoding = (str, p) => {
        let num = 0;
        let word = ''
        let i = p
        while(i < str.length){
            let ch = s[i]
            if(ch >= '0' && ch <= '9'){
                num = 10 * num + (ch - '0')
            }else if(ch >= 'a' && ch <= 'z'){
                word+=ch
            }else if(ch == '['){
                let [sts, pos] = stringDecoding(str, i+1)
                word+=sts.repeat(num)
                i=pos
                num=0
            }else{
                return [word,i]
            }
            i++
        }
        return [word,0]
    }

    return stringDecoding(s, 0)[0]
};
```
