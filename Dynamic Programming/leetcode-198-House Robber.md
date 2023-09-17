# 198. House Robber

## 문제 :

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [1,2,3,1]
<br/>
Output: 4
<br/>
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
<br/>
Total amount you can rob = 1 + 3 = 4.

<br/>

### Example 2:

Input: nums = [2,7,9,3,1]
<br/>
Output: 12
<br/>
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
<br/>
Total amount you can rob = 2 + 9 + 1 = 12.

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 100
- 0 <= nums[i] <= 400

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    let max1 = 0
    let max2 = 0
    let temp = 0
    for (let i = 0; i < nums.length ; i++) {
        temp = Math.max(nums[i] + max1, max2)
        max1 = max2
        max2 = temp
    }
    return max2
};
```
