# 435. Non-overlapping Intervals

## 문제 :

Given an array of intervals intervals where intervals[i] = [starti, endi], return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: intervals = [[1,2],[2,3],[3,4],[1,3]]
<br/>
Output: 1
<br/>
Explanation: [1,3] can be removed and the rest of the intervals are non-overlapping.

<br/>

### Example 2:

Input: intervals = [[1,2],[1,2],[1,2]]
<br/>
Output: 2
<br/>
Explanation: You need to remove two [1,2] to make the rest of the intervals non-overlapping.

<br/>

### Example 3:

Input: intervals = [[1,2],[2,3]]
<br/>
Output: 0
<br/>
Explanation: You don't need to remove any of the intervals since they're already non-overlapping.

<br/>

---

## 조건

### Constraints:

- 1 <= intervals.length <= 10^5
- intervals[i].length == 2
- -5 _ 10^4 <= starti < endi <= 5 _ 10^4

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[][]} intervals
 * @return {number}
 */

var eraseOverlapIntervals = function(intervals) {
    intervals.sort((a, b) => a[1] - b[1]);
    let prev = intervals[0]
    let remove = 0

    for(let i = 1; i < intervals.length; i++) {
        if(intervals[i][0] < prev[1]){
            remove++;
        }else{
            prev = intervals[i];
        }
    }
    return remove;
};
```
