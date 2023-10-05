# 739. Daily Temperatures

## 문제 :

Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: temperatures = [73,74,75,71,69,72,76,73]
<br/>
Output: [1,1,4,2,1,1,0,0]

<br/>

### Example 2:

Input: temperatures = [30,40,50,60]
<br/>
Output: [1,1,1,0]

<br/>

### Example 3:

Input: temperatures = [30,60,90]
<br/>
Output: [1,1,0]

<br/>

---

## 조건

### Constraints:

- 1 <= temperatures.length <= 10^5
- 30 <= temperatures[i] <= 100

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} temperatures
 * @return {number[]}
 */
var dailyTemperatures = function(temperatures) {

    let days = new Array(temperatures.length).fill(0)
    let stack = []

    for(let i = 0; i < temperatures.length; i++){

        while(temperatures[i] > temperatures[stack[stack.length - 1]]){
            let lastOfStack = stack.pop()
            let different = i - lastOfStack
            days[lastOfStack] = different
        }

        stack.push(i)
    }


    return days

};



// Not Monotonic Stack
var dailyTemperatures = function(temperatures) {

    let result =[]

    for(let i=0; i< temperatures.length-1 ; i++){
        let j=i+1

        while(temperatures[j]<=temperatures[i]){
            j++
        }
        if(temperatures.includes(temperatures[j])){
            result.push(j-i)
        }else{
            result.push(0)
        }
    }
    result.push(0)
    return result
};
```
