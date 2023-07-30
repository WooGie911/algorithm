# 238. Product of Array Except Self

## 문제 :

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [1,2,3,4]
<br/>
Output: [24,12,8,6]

<br/>

### Example 2:

Input: nums = [-1,1,0,-3,3]
<br/>
Output: [0,0,9,0,0]

<br/>

---

## 조건

### Constraints:

- 2 <= nums.length <= 10^5
- -30 <= nums[i] <= 30
- The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var productExceptSelf = function(nums) {

    let res = []

    for(let i=0; i< nums.length ; i++){
        let mul = 1
        for(let j=0; j< nums.length ; j++){
            if(i != j){
                mul *= nums[j]
            }
        }
        res.push(mul)
    }

    return res
};
```
