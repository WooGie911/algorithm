# 374. Guess Number Higher or Lower

## 문제 :

We are playing the Guess Game. The game is as follows:

I pick a number from 1 to n. You have to guess which number I picked.

Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess.

You call a pre-defined API int guess(int num), which returns three possible results:

- -1: Your guess is higher than the number I picked (i.e. num > pick).
- 1: Your guess is lower than the number I picked (i.e. num < pick).
- 0: your guess is equal to the number I picked (i.e. num == pick).

Return the number that I picked.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: n = 10, pick = 6
<br/>
Output: 6

<br/>

### Example 2:

Input: n = 1, pick = 1
<br/>
Output: 1

<br/>

### Example 3:

Input: n = 2, pick = 1
<br/>
Output: 1

<br/>

---

## 조건

### Constraints:

- 1 <= n <= 2^31 - 1
- 1 <= pick <= n

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * Forward declaration of guess API.
 * @param {number} num   your guess
 * @return 	     -1 if num is higher than the picked number
 *			      1 if num is lower than the picked number
 *               otherwise return 0
 * var guess = function(num) {}
 */

/**
 * @param {number} n
 * @return {number}
 */
var guessNumber = function(n) {
    let low = 1;
    let high = n;
    while (low <= high) {
        let mid = low + ~~((high - low) / 2);
        const response = guess(mid)
        if (response == 0) return mid;
        else if (response < 0) high = mid - 1;
        else low = mid + 1;
    }
    return -1;
};
```
