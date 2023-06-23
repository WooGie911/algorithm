# 2716. Minimize String Length

## 문제 : 

You are given an integer array banned and two integers n and maxSum. You are choosing some number of integers following the below rules :


- The chosen integers have to be in the range [1, n].
- Each integer can be chosen at most once.
- The chosen integers should not be in the array banned.
- The sum of the chosen integers should not exceed maxSum.
- Return the maximum number of integers you can choose following the mentioned rules.

<br/>

---

## 입력 예시 :
<br/>


### Example 1:

Input: banned = [1,6,5], n = 5, maxSum = 6
<br/>
Output: 2
<br/>
Explanation: You can choose the integers 2 and 4.
2 and 4 are from the range [1, 5], both did not appear in banned, and their sum is 6, which did not exceed maxSum.

<br/>


### Example 2:

Input: banned = [1,2,3,4,5,6,7], n = 8, maxSum = 1
<br/>
Output: 0
<br/>
Explanation: You cannot choose any integer while following the mentioned conditions.

<br/>

### Example 3:

Input: banned = [11], n = 7, maxSum = 50
<br/>
Output: 7
<br/>
Explanation: You can choose the integers 1, 2, 3, 4, 5, 6, and 7.
<br/>
They are from the range [1, 7], all did not appear in banned, and their sum is 28, which did not exceed maxSum.


<br/>


--- 
 
## 조건

### Constraints:

- 1 <= banned.length <= 104
- 1 <= banned[i], n <= 104
- 1 <= maxSum <= 109

<br/>


---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} banned
 * @param {number} n
 * @param {number} maxSum
 * @return {number}
 */
var maxCount = function(banned, n, maxSum) {

    let Arr = []
    let totalSum =0
    let count =0

    for(let i=1; i<= n ; i++){
        if(!banned.includes(i)){
            Arr.push(i)
        }
    }
 
    for(n of Arr){
        if(totalSum > maxSum){
            break
        }
        totalSum += n
        count ++
    }

    return totalSum >  maxSum ?  count-1 : count
};
```

