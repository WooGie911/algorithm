# 55. Jump Game

## 문제 :

You are given an integer array nums.
<br/>
You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [2,3,1,1,4]
<br/>
Output: true
<br/>
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.

<br/>

### Example 2:

Input: nums = [3,2,1,0,4]
<br/>
Output: false
<br/>
Explanation: You will always arrive at index 3 no matter what.
<br/>
Its maximum jump length is 0, which makes it impossible to reach the last index.

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 10^4
- 0 <= nums[i] <= 10^5

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var canJump = function(nums) {

    let dp = 0

    for(let i=0 ; i<nums.length-1 ; i++){
        dp = Math.max(dp-1,nums[i])
        if(dp <= 0) return false;
    }

    return true
};

or

/**
 * @param {number[]} nums
 * @return {boolean}
 */
var canJump = function(nums) {
    nums.unshift(0);
    for(let i = 1; i < nums.length -1 ; i++){
        nums[i] = Math.max(nums[i - 1] - 1, nums[i]);
        if(nums[i] <= 0) return false;
    }
    return true;
};
```
