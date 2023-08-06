# 283. Move Zeroes

## 문제 :

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [0,1,0,3,12]
<br/>
Output: [1,3,12,0,0]

<br/>

### Example 2:

Input: nums = [0]
<br/>
Output: [0]

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 10^4
- -2^31 <= nums[i] <= 2^31 - 1

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
let moveZeroes = function (nums) {
    let low = 0;
    let high = low + 1;

    while (high <= nums.length - 1) {
        if (nums[low] !== 0) {
            low++;
            high++;
        } else {
            if (nums[high] !== 0) {
                [nums[low], nums[high]] = [nums[high], nums[low]];
                low++;
            }
            high++;
        }
    }
};
```
