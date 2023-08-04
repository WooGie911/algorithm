# 334. Increasing Triplet Subsequence

## 문제 :

Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k].
<br/>
If no such indices exists, return false.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [1,2,3,4,5]
<br/>
Output: true
<br/>
Explanation: Any triplet where i < j < k is valid.

<br/>

### Example 2:

Input: nums = [5,4,3,2,1]
<br/>
Output: false
<br/>
Explanation: No triplet exists.

<br/>

### Example 3:

Input: nums = [2,1,5,0,4,6]
<br/>
Output: true
<br/>
Explanation: The triplet (3, 4, 5) is valid because nums[3] == 0 < nums[4] == 4 < nums[5] == 6.

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 5 \* 10^5
- -2^31 <= nums[i] <= 2^31 - 1

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var increasingTriplet = function(nums) {
    let first = Infinity
    let second =Infinity
    for(let i=0 ; i<nums.length ; i++){
        if(nums[i]<= first){
            first =nums[i]
        } else if (nums[i] <= second){
            second =nums[i]
        }else{
            return true
        }
    }
    return false
};
```
