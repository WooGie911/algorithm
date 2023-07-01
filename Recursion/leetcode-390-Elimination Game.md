# 390. Elimination Game

## 문제 :

You have a list arr of all integers in the range [1, n] sorted in a strictly increasing order. Apply the following algorithm on arr:

- Starting from left to right, remove the first number and every other number afterward until you reach the end of the list.
- Repeat the previous step again, but this time from right to left, remove the rightmost number and every other number from the remaining numbers.
- Keep repeating the steps again, alternating left to right and right to left, until a single number remains.

Given the integer n, return the last number that remains in arr.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: n = 9
<br/>
Output: 6
<br/>
Explanation:
<br/>
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
<br/>
arr = [2, 4, 6, 8]
<br/>
arr = [2, 6]
<br/>
arr = [6]

<br/>

### Example 2:

Input: n = 1
<br/>
Output: 1

<br/>

---

## 조건

### Constraints:

- 1 <= n <= 10^9

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number} n
 * @return {number}
 */

var lastRemaining = function(n) {
    if(n === 1){
        return 1
    }else if(n % 2 === 1){
        return lastRemaining(n-1)
    }else{
        return 2 * ( n / 2 + 1 - lastRemaining( n / 2 ))
    }

};

```
