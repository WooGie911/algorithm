# 790. Domino and Tromino Tiling

## 문제 :

You have two types of tiles: a 2 x 1 domino shape and a tromino shape. You may rotate these shapes.

<img src = 'https://assets.leetcode.com/uploads/2021/07/15/lc-domino.jpg'>

Given an integer n, return the number of ways to tile an 2 x n board. Since the answer may be very large, return it modulo 109 + 7.

In a tiling, every square must be covered by a tile. Two tilings are different if and only if there are two 4-directionally adjacent cells on the board such that exactly one of the tilings has both squares occupied by a tile.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src = 'https://assets.leetcode.com/uploads/2021/07/15/lc-domino1.jpg'>

Input: n = 3
<br/>
Output: 5
<br/>
Explanation: The five different ways are show above.

<br/>

### Example 2:

Input: n = 1
<br/>
Output: 1

<br/>

---

## 조건

### Constraints:

- 1 <= n <= 1000

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number} n
 * @return {number}
 */
var numTilings = function(n) {
    const MOD = Math.pow(10,9) + 7
    let dp = {}
    dp[1] = 1
    dp[2] = 2
    dp[3] = 5
    for (let i = 4; i <= n ; i++) {
        dp[i] = (2 * dp[i-1] + dp[i-3]) % MOD
    }
    return dp[n]
}
```
