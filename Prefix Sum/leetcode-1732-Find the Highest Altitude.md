# 1732. Find the Highest Altitude

## 문제 :

There is a biker going on a road trip. <br/>
The road trip consists of n + 1 points at different altitudes.
<br/>
The biker starts his trip on point 0 with altitude equal 0.

You are given an integer array gain of length n where gain[i] is the net gain in altitude between points i​​​​​​ and i + 1 for all (0 <= i < n).
<br/>
Return the highest altitude of a point.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: gain = [-5,1,5,0,-7]
<br/>
Output: 1
<br/>
Explanation: The altitudes are [0,-5,-4,1,1,-6]. The highest is 1.

<br/>

### Example 2:

Input: gain = [-4,-3,-2,-1,4,3,2]
<br/>
Output: 0
<br/>
Explanation: The altitudes are [0,-4,-7,-9,-10,-6,-3,-1]. The highest is 0.

<br/>

---

## 조건

### Constraints:

- n == gain.length
- 1 <= n <= 100
- -100 <= gain[i] <= 100

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} gain
 * @return {number}
 */
var largestAltitude = function(gain) {

    let HighestGain = 0
    let CurrentGain = 0

    for(let i=0; i<gain.length ; i++){
        CurrentGain += gain[i]
        if(CurrentGain > HighestGain){
            HighestGain = CurrentGain
        }
    }

    return HighestGain

};
```
