# 912. Sort an Array

## 문제 :

Given an array of integers nums, sort the array in ascending order and return it.

You must solve the problem without using any built-in functions in O(nlog(n)) time complexity and with the smallest space complexity possible.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums = [5,2,3,1]
<br/>
Output: [1,2,3,5]
<br/>
Explanation: After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), while the positions of other numbers are changed (for example, 1 and 5).

<br/>

### Example 2:

Input: nums = [5,1,1,2,0,0]
<br/>
Output: [0,0,1,1,2,5]
<br/>
Explanation: Note that the values of nums are not necessairly unique.

<br/>

---

## 조건

### Constraints:

- 1 <= nums.length <= 5 \* 10^4
- -5 _ 10^4 <= nums[i] <= 5 _ 10^4

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums
 * @return {number[]}
 */

function merge(left,right) {
    var result = [],lLen = left.length, rLen = right.length, l = 0, r = 0;
    while(l < lLen && r < rLen){
        if(left[l] < right[r]){
            result.push(left[l++]);
        }
        else{
            result.push(right[r++]);
        }
    }
    return result.concat(left.slice(l)).concat(right.slice(r));
}

var sortArray = function(nums) {
    if (nums.length < 2) return nums;
    var mid   = Math.floor(nums.length/2);
    var left  = nums.slice(0,mid);
    var right = nums.slice(mid);

    return merge(sortArray(left),sortArray(right));
};


```
