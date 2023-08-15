# 643. Maximum Average Subarray I

## 문제 :

You are given an integer array nums consisting of n elements, and an integer k.

Find a contiguous subarray whose length is equal to k that has the maximum average value and return this value.

Any answer with a calculation error less than 10-5 will be accepted.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [1,12,-5,-6,50,3], k = 4
<br/>
Output: 12.75000
<br/>
Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75

<br/>

### Example 2:

Input: nums = [5], k = 1
<br/>
Output: 5.00000

<br/>

---

## 조건

### Constraints:

- n == nums.length
- 1 <= k <= n <= 10^5
- -10^4 <= nums[i] <= 10^4

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findMaxAverage = function(nums, k) {
    let max =  -Infinity
    let idx = k-1
    while(idx < nums.length){
        let sum = 0
        for(let i=idx-k+1 ; i<=idx ; i++){
            sum += nums[i]
        }
        max = Math.max(max,sum)
        idx++
    }

    return (max / k)
};
```
