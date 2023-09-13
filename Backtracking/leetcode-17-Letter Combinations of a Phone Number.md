# 17. Letter Combinations of a Phone Number

## 문제 :

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

<img src = 'https://assets.leetcode.com/uploads/2022/03/15/1200px-telephone-keypad2svg.png'>

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]

<br/>

### Example 2:

Input: digits = ""
Output: []

<br/>

### Example 3:

Input: digits = "2"
Output: ["a","b","c"]

<br/>

---

## 조건

### Constraints:

- 0 <= digits.length <= 4
- digits[i] is a digit in the range ['2', '9'].

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
    if (digits == null || digits.length === 0) return [];

    const chaArr = ["", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"]
    const res = [];

    const BT = (ind, str) => {

        if (ind === digits.length) {
            res.push(str);
            return;
        }

        for (const cha of chaArr[digits[ind]]) {
            BT(ind + 1, str + cha);
        }
    };

    BT(0, '');
    return res;
};
```
