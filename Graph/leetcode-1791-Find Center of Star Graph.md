# 1791. Find Center of Star Graph

## 문제 :

There is an undirected star graph consisting of n nodes labeled from 1 to n. A star graph is a graph where there is one center node and exactly n - 1 edges that connect the center node with every other node.

You are given a 2D integer array edges where each edges[i] = [ui, vi] indicates that there is an edge between the nodes ui and vi.

Return the center of the given star graph.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src = 'https://assets.leetcode.com/uploads/2021/02/24/star_graph.png'>

<br/>

Input: edges = [[1,2],[2,3],[4,2]]
<br/>
Output: 2
<br/>
Explanation: As shown in the figure above, node 2 is connected to every other node, so 2 is the center.

<br/>

### Example 2:

Input: edges = [[1,2],[5,1],[1,3],[1,4]]
<br/>
Output: 1

<br/>

---

## 조건

### Constraints:

- 3 <= n <= 10^5
- edges.length == n - 1
- edges[i].length == 2
- 1 <= ui, vi <= n
- ui != vi
- The given edges represent a valid star graph.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[][]} edges
 * @return {number}
 */
var findCenter = function(edges) {

    let hasObj = {};

    for(let i=0; i<edges.length ; i++){
        for(let j=0; j<edges[i].length ; j++){
            if (hasObj[edges[i][j]]) {
                hasObj[edges[i][j]] += 1;
            } else {
                hasObj[edges[i][j]] = 1;
            }
            if (hasObj[edges[i][j]] === edges[i].length) {
                console.log(hasObj)
                return edges[i][j];
            }
        }
    }

};
```
