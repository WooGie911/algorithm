# 1318. Minimum Flips to Make a OR b Equal to c

## 문제 :

Given 3 positives numbers a, b and c. Return the minimum flips required in some bits of a and b to make ( a OR b == c ). (bitwise OR operation).

Flip operation consists of change any single bit 1 to 0 or change the bit 0 to 1 in their binary representation.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src = 'https://assets.leetcode.com/uploads/2020/01/06/sample_3_1676.png'>

<br/>

Input: a = 2, b = 6, c = 5
<br/>
Output: 3
<br/>
Explanation: After flips a = 1 , b = 4 , c = 5 such that (a OR b == c)

<br/>

### Example 2:

Input: a = 4, b = 2, c = 7
<br/>
Output: 1

<br/>

### Example 3:

Input: a = 1, b = 2, c = 3
<br/>
Output: 0

<br/>

---

## 조건

### Constraints:

- 1 <= a <= 10^9
- 1 <= b <= 10^9
- 1 <= c <= 10^9

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number} a
 * @param {number} b
 * @param {number} c
 * @return {number}
 */
var minFlips = function(a, b, c) {
    const limit = Math.max(a, b, c);
    let check = 1;
    let result = 0;
    while(check <= limit){
        if(check & c){
            if(!(check & a) && !(check & b)){
                result++;
            }
        }else{
            if(check & a){
                result++;
            }
            if(check & b){
                result++;
            }
        }
        check *= 2;
    }
    return result;
};
```
