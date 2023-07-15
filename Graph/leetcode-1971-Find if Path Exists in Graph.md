# 1971. Find if Path Exists in Graph

## 문제 :

There is a bi-directional graph with n vertices, where each vertex is labeled from 0 to n - 1 (inclusive). The edges in the graph are represented as a 2D integer array edges, where each edges[i] = [ui, vi] denotes a bi-directional edge between vertex ui and vertex vi. Every vertex pair is connected by at most one edge, and no vertex has an edge to itself.

You want to determine if there is a valid path that exists from vertex source to vertex destination.

Given edges and the integers n, source, and destination, return true if there is a valid path from source to destination, or false otherwise.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src = 'https://assets.leetcode.com/uploads/2021/08/14/validpath-ex1.png'>

<br/>

Input: n = 3, edges = [[0,1],[1,2],[2,0]], source = 0, destination = 2
<br/>
Output: true
<br/>
Explanation: There are two paths from vertex 0 to vertex 2:

- 0 → 1 → 2
- 0 → 2

<br/>

### Example 2:

<img src = 'https://assets.leetcode.com/uploads/2021/08/14/validpath-ex2.png'>

<br/>

Input: n = 6, edges = [[0,1],[0,2],[3,5],[5,4],[4,3]], source = 0, destination = 5
<br/>
Output: false
<br/>
Explanation: There is no path from vertex 0 to vertex 5.

<br/>

---

## 조건

### Constraints:

- 1 <= n <= 2 \* 10^5
- 0 <= edges.length <= 2 \* 10^5
- edges[i].length == 2
- 0 <= ui, vi <= n - 1
- ui != vi
- 0 <= source, destination <= n - 1
- There are no duplicate edges.
- There are no self edges.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number} n
 * @param {number[][]} edges
 * @param {number} source
 * @param {number} destination
 * @return {boolean}
 */
var validPath = function(n, edges, source, destination) {
    const graph = createGraph(edges)
    const visited = new Set()
    return recusionFun(source,destination,graph,visited)
};


const createGraph = (edges) => {
    const graph = {};

    for (const [source, dest] of edges) {
        if (graph[source] === undefined) graph[source] = [];
        if (graph[dest] === undefined) graph[dest] = [];

        graph[source].push(dest);
        graph[dest].push(source);
    }
    return graph
}

const recusionFun = (now,arrive,graph,visited) =>{
    if(now===arrive) return true
    if(visited.has(now)) return false
    visited.add(now)
    for(let node of graph[now]){
        if(recusionFun(node,arrive,graph,visited) === true) return true
    }
    return false
}


```
