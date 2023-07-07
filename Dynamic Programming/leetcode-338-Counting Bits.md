# 338. Counting Bits

## 문제 :

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: n = 2
<br/>
Output: [0,1,1]
<br/>
Explanation:

- 0 --> 0
- 1 --> 1
- 2 --> 10

<br/>

### Example 2:

Input: n = 5
<br/>
Output: [0,1,1,2,1,2]
<br/>
Explanation:

- 0 --> 0
- 1 --> 1
- 2 --> 10
- 3 --> 11
- 4 --> 100
- 5 --> 101

<br/>

---

## 조건

### Constraints:

- 0 <= n <= 10^5

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number} n
 * @return {number[]}
 */
var countBits = function(n) {
    let res = [0]
    for(let i=1;i<=n;i++){
      if(i%2 === 0){
        res.push(res[~~(i/2)])
      } else {
        res.push(res[~~(i/2)]+1)
      }
    }
    return res
};
```
