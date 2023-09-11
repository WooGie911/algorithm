# 162. Find Peak Element

## 문제 :

A peak element is an element that is strictly greater than its neighbors.

Given a 0-indexed integer array nums, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.

You may imagine that nums[-1] = nums[n] = -∞. In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

You must write an algorithm that runs in O(log n) time.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [1,2,3,1]
<br/>
Output: 2
<br/>
Explanation: 3 is a peak element and your function should return the index number 2.

<br/>

### Example 2:

Input: nums = [1,2,1,3,5,6,4]
<br/>
Output: 5
<br/>
Explanation: Your function can return either index number 1 where the peak element is 2, or index number 5 where the peak element is 6.

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 1000
- -2^31 <= nums[i] <= 2^31 - 1
- nums[i] != nums[i + 1] for all valid i.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {number}
 */
function findPeakElement(nums) {
    let low = 0;
    let high = nums.length - 1;
    while (low < high) {
        let mid = Math.floor((low + high) / 2);
        if(nums[mid+1] > nums[mid]) {
            low = mid+1
        } else if(nums[mid-1] > nums[mid]) {
            high = mid-1;
        } else {
            return mid;
        }
    }
    return high;
};
```
