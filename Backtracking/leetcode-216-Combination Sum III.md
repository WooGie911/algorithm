# 216. Combination Sum III

## 문제 :

Find all valid combinations of k numbers that sum up to n such that the following conditions are true:

- Only numbers 1 through 9 are used.
- Each number is used at most once.

Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: k = 3, n = 7
<br/>
Output: [[1,2,4]]
<br/>
Explanation:
<br/>
1 + 2 + 4 = 7
<br/>
There are no other valid combinations.

<br/>

### Example 2:

Input: k = 3, n = 9
<br/>
Output: [[1,2,6],[1,3,5],[2,3,4]]
<br/>
Explanation:
<br/>
1 + 2 + 6 = 9
<br/>
1 + 3 + 5 = 9
<br/>
2 + 3 + 4 = 9
<br/>
There are no other valid combinations.

<br/>

### Example 3:

Input: k = 4, n = 1
<br/>
Output: []
<br/>
Explanation: There are no valid combinations.
<br/>
Using 4 different numbers in the range [1,9], the smallest sum we can get is 1+2+3+4 = 10 and since 10 > 1, there are no valid combination.

<br/>

---

## 조건

### Constraints:

- 2 <= k <= 9
- 1 <= n <= 60

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number} k
 * @param {number} n
 * @return {number[][]}
 */
var combinationSum3 = function(k, n) {
    if (n > 45) return []
    const res = []

    function BT(i, k, currSum = 0, currDigits = []) {
        if (k === 0 && currSum === n) {
            res.push([...currDigits])
            return
        }

        if (k === 0 || i == 10 || currSum >= n) return

        BT(i + 1, k, currSum, currDigits)
        currDigits.push(i)
        BT(i + 1, k - 1, currSum + i, currDigits)
        currDigits.pop()
    }

    BT(1, k)
    return res
};
```
