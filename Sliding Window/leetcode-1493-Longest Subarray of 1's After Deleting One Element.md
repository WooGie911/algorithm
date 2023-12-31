# 1493. Longest Subarray of 1's After Deleting One Element

## 문제 :

Given a binary array nums, you should delete one element from it.

Return the size of the longest non-empty subarray containing only 1's in the resulting array. Return 0 if there is no such subarray.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [1,1,0,1]
<br/>
Output: 3
<br/>
Explanation: After deleting the number in position 2, [1,1,1] contains 3 numbers with value of 1's.

<br/>

### Example 2:

Input: nums = [0,1,1,1,0,1,1,0,1]
<br/>
Output: 5
<br/>
Explanation: After deleting the number in position 4, [0,1,1,1,1,1,0,1] longest subarray with value of 1's is [1,1,1,1,1].

<br/>

### Example 3:

Input: nums = [1,1,1]
<br/>
Output: 2
<br/>
Explanation: You must delete one element.

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 10^5
- nums[i] is either 0 or 1.

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var longestSubarray = function(nums) {

    let start = 0
    let zeroCount = 0;
    let largestWindow =0;

    for (let end = 0; end < nums.length; end++) {
	    zeroCount += (nums[end] == 0 ? 1: 0);

        while(zeroCount>1){
            zeroCount -= (nums[start] == 0 ? 1 : 0);
            start++;
        }

        largestWindow = Math.max(largestWindow, end-start);
    }

    return largestWindow;
};
```
