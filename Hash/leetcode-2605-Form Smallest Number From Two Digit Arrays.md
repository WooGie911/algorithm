# 2716. Minimize String Length

## 문제 : 

Given two arrays of unique digits nums1 and nums2, return the smallest number that contains at least one digit from each array.

<br/>

---

## 입력 예시 :
<br/>


### Example 1:

Input: nums1 = [4,1,3], nums2 = [5,7]
<br/>
Output: 15
<br/>
Explanation: The number 15 contains the digit 1 from nums1 and the digit 5 from nums2. It can be proven that 15 is the smallest number we can have.

<br/>


### Example 2:

Input: nums1 = [3,5,2,6], nums2 = [3,1,7]
<br/>
Output: 3
<br/>
Explanation: The number 3 contains the digit 3 which exists in both arrays.

<br/>

--- 
 
## 조건

### Constraints:

- 1 <= nums1.length, nums2.length <= 9
- 1 <= nums1[i], nums2[i] <= 9
- All digits in each array are unique.

<br/>


---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var minNumber = function(nums1, nums2) {
    let min1=Math.min(...nums1)
    let min2=Math.min(...nums2)
    let min= min1>min2?min2*10+min1 : min1*10+min2

    for(let i=0 ; i< nums1.length ; i++){
        if(nums2.includes(nums1[i]) && nums1[i]<min){
            min=nums1[i]
        }
    }

    return min
};
```

