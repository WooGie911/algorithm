# 136. Single Number

## 문제 :

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [2,2,1]
Output: 1

<br/>

### Example 2:

Input: nums = [4,1,2,1,2]
Output: 4

<br/>

### Example 3:

Input: nums = [1]
Output: 1

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 3 \* 10^4
- -3 _ 10^4 <= nums[i] <= 3 _ 10^4
- Each element in the array appears twice except for one element which appears only once.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    return nums.reduce((prev, curr) => prev^curr)
};
```
