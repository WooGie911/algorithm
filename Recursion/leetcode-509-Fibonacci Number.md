# 509. Fibonacci Number

## 문제 :

The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

F(0) = 0, F(1) = 1
<br/>
F(n) = F(n - 1) + F(n - 2), for n > 1.
<br/>

Given n, calculate F(n).

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: n = 2
<br/>
Output: 1
<br/>
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.

<br/>

### Example 2:

Input: n = 3
<br/>
Output: 2
<br/>
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.

<br/>

### Example 3:

Input: n = 4
<br/>
Output: 3
<br/>
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.

<br/>

---

## 조건

### Constraints:

- 0 <= n <= 30

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number} n
 * @return {number}
 */

var fib = function(n) {
    if(n<=1){
        return n;
    }
    return fib(n-1) + fib(n-2)
};

```
