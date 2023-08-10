# 1679. Max Number of K-Sum Pairs

## 문제 :

You are given an integer array nums and an integer k.

In one operation, you can pick two numbers from the array whose sum equals k and remove them from the array.

Return the maximum number of operations you can perform on the array.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [1,2,3,4], k = 5
<br/>
Output: 2
<br/>
Explanation: Starting with nums = [1,2,3,4]:

- Remove numbers 1 and 4, then nums = [2,3]
- Remove numbers 2 and 3, then nums = []

  There are no more pairs that sum up to 5, hence a total of 2 operations.

<br/>

### Example 2:

Input: nums = [3,1,3,4,3], k = 6
<br/>
Output: 1
<br/>
Explanation: Starting with nums = [3,1,3,4,3]:

- Remove the first two 3's, then nums = [1,4,3]

  There are no more pairs that sum up to 6, hence a total of 1 operation.

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 10^5
- 1 <= nums[i] <= 10^9
- 1 <= k <= 10^9

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var maxOperations = function(nums, k) {
    nums.sort(function(a, b){return a - b});
    var i = 0, j = nums.length - 1, count = 0;
    while (i < j){
        if (nums[i] + nums[j] == k){
            count ++;
            i ++;
            j --;
        }
        else if (nums[i] + nums[j] < k){
            i ++;
        }else{
            j --;
        }
    }
    return count;
};
```
