# 2215. Find the Difference of Two Arrays

## 문제 :

Given two 0-indexed integer arrays nums1 and nums2, return a list answer of size 2 where:

- answer[0] is a list of all distinct integers in nums1 which are not present in nums2.
- answer[1] is a list of all distinct integers in nums2 which are not present in nums1.

Note that the integers in the lists may be returned in any order.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: nums1 = [1,2,3], nums2 = [2,4,6]
<br/>
Output: [[1,3],[4,6]]
<br/>
Explanation:
<br/>
For nums1, nums1[1] = 2 is present at index 0 of nums2, whereas nums1[0] = 1 and nums1[2] = 3 are not present in nums2. Therefore, answer[0] = [1,3].
<br/>
For nums2, nums2[0] = 2 is present at index 1 of nums1, whereas nums2[1] = 4 and nums2[2] = 6 are not present in nums2. Therefore, answer[1] = [4,6].

<br/>

### Example 2:

Input: nums1 = [1,2,3,3], nums2 = [1,1,2,2]
<br/>
Output: [[3],[]]
<br/>
Explanation:
<br/>
For nums1, nums1[2] and nums1[3] are not present in nums2. Since nums1[2] == nums1[3], their value is only included once and answer[0] = [3].
<br/>
Every integer in nums2 is present in nums1. Therefore, answer[1] = [].

<br/>

---

## 조건

### Constraints:

- 1 <= nums1.length, nums2.length <= 1000
- -1000 <= nums1[i], nums2[i] <= 1000

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[][]}
 */
var findDifference = function(nums1, nums2) {
    const nSet1 = new Set(nums1)
    const nSet2 = new Set(nums2)

    let nArr1 = []
    let nArr2 = []
    let res = []
    for (const value1 of nSet1) {
        if(!nSet2.has(value1)){
            nArr1.push(value1)
        }
    }
    for (const value2 of nSet2) {
        if(!nSet1.has(value2)){
            nArr2.push(value2)
        }
    }


    res.push(nArr1)
    res.push(nArr2)
    return res
};
```
