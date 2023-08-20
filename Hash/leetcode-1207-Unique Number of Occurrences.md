# 1207. Unique Number of Occurrences

## 문제 :

Given an array of integers arr, return true if the number of occurrences of each value in the array is unique or false otherwise.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: arr = [1,2,2,1,1,3]
<br/>
Output: true
<br/>
Explanation: The value 1 has 3 occurrences, 2 has 2 and 3 has 1. No two values have the same number of occurrences.

<br/>

### Example 2:

Input: arr = [1,2]
<br/>
Output: false

<br/>

### Example 3:

Input: arr = [-3,0,1,-3,1,1,1,-3,10,0]
<br/>
Output: true

<br/>

---

## 조건

### Constraints:

- 1 <= arr.length <= 1000
- -1000 <= arr[i] <= 1000

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} arr
 * @return {boolean}
 */
var uniqueOccurrences = function(arr) {
    const hashmap = {};

    for (let i = 0; i < arr.length; i++) {
        const item = arr[i];
        if (hashmap[item]) {
            hashmap[item] = hashmap[item] + 1;
        } else {
            hashmap[item] = 1;
        }
    }
    console.log(hashmap)

    const valuse = Object.values(hashmap)
    const set = new Set(valuse);

    return set.size === valuse.length
};
```
