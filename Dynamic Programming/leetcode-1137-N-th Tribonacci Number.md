# 1137. N-th Tribonacci Number

## 문제 :

The Tribonacci sequence Tn is defined as follows:

T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.

Given n, return the value of Tn.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: n = 4
<br/>
Output: 4
<br/>
Explanation:
<br/>
T_3 = 0 + 1 + 1 = 2
<br/>
T_4 = 1 + 1 + 2 = 4

<br/>

### Example 2:

Input: n = 25
<br/>
Output: 1389537

<br/>

---

## 조건

### Constraints:

- 0 <= n <= 37
- The answer is guaranteed to fit within a 32-bit integer, ie. answer <= 2^31 - 1.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number} n
 * @return {number}
 */
var tribonacci = function(n) {
    if(n===0){
        return 0
    }else if(n===1){
        return 1
    }else if(n===2){
        return 1
    }
    let dp = []
    dp[0] = 0;
    dp[1] = 1;
    dp[2] = 1;
    for (let i = 3; i <= n; i++) {
        dp[i] = dp[i-1] + dp[i-2] + dp[i-3]
    }
    return dp[dp.length - 1];
};
```
