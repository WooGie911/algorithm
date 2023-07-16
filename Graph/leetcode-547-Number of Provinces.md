# 547. Number of Provinces

## 문제 :

There are n cities. Some of them are connected, while some are not. If city a is connected directly with city b, and city b is connected directly with city c, then city a is connected indirectly with city c.

A province is a group of directly or indirectly connected cities and no other cities outside of the group.

You are given an n x n matrix isConnected where isConnected[i][j] = 1 if the i th city and the j th city are directly connected, and isConnected[i][j] = 0 otherwise.

Return the total number of provinces.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src = 'https://assets.leetcode.com/uploads/2020/12/24/graph1.jpg'>

<br/>

Input: isConnected = [[1,1,0],[1,1,0],[0,0,1]]
<br/>
Output: 2

<br/>

### Example 2:

<img src = 'https://assets.leetcode.com/uploads/2020/12/24/graph2.jpg'>

<br/>

Input: isConnected = [[1,0,0],[0,1,0],[0,0,1]]
<br/>
Output: 3

<br/>

---

## 조건

### Constraints:

- 1 <= n <= 200
- n == isConnected.length
- n == isConnected[i].length
- isConnected[i][j] is 1 or 0.
- isConnected[i][i] == 1
- isConnected[i][j] == isConnected[j][i]

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[][]} isConnected
 * @return {number}
 */
var findCircleNum = function(isConnected) {
    const visited = Array(isConnected.length).fill(false);
    let count = 0;

    for (let i = 0; i < isConnected.length; i++) {
        if (!visited[i]) {
            visiedIndex(isConnected, visited, i);
            count++;
        }
    }
    return count;
};

const visiedIndex = (graph,visited,index) =>{
    visited[index] = true;

    for(let i =0; i<graph[index].length ; i++){
        if(!visited[i] && graph[index][i]===1){
            visiedIndex(graph,visited,i)
        }
    }
}
```
