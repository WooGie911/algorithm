# 399. Evaluate Division

## 문제 :

You are given an array of variable pairs equations and an array of real numbers values, where equations[i] = [Ai, Bi] and values[i] represent the equation Ai / Bi = values[i]. Each Ai or Bi is a string that represents a single variable.

You are also given some queries, where queries[j] = [Cj, Dj] represents the jth query where you must find the answer for Cj / Dj = ?.

Return the answers to all queries. If a single answer cannot be determined, return -1.0.

Note: The input is always valid. You may assume that evaluating the queries will not result in division by zero and that there is no contradiction.

Note: The variables that do not occur in the list of equations are undefined, so the answer cannot be determined for them.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input:
<br/>
equations = [["a","b"],["b","c"]],
<br/>
values = [2.0,3.0],
<br/>
queries = [["a","c"],["b","a"],["a","e"],["a","a"],["x","x"]]
<br/>
Output: [6.00000,0.50000,-1.00000,1.00000,-1.00000]
<br/>
Explanation:
<br/>
Given: a / b = 2.0, b / c = 3.0
<br/>
queries are: a / c = ?, b / a = ?, a / e = ?, a / a = ?, x / x = ?
<br/>
return: [6.0, 0.5, -1.0, 1.0, -1.0 ]
<br/>
note: x is undefined => -1.0

<br/>

### Example 2:

Input:
<br/>
equations = [["a","b"],["b","c"],["bc","cd"]],
<br/>
values = [1.5,2.5,5.0],
<br/>
queries = [["a","c"],["c","b"],["bc","cd"],["cd","bc"]]
<br/>
Output: [3.75000,0.40000,5.00000,0.20000]

<br/>

### Example 3:

Input:
<br/>
equations = [["a","b"]],
<br/>
values = [0.5],
<br/>
queries = [["a","b"],["b","a"],["a","c"],["x","y"]]
<br/>
Output: [0.50000,2.00000,-1.00000,-1.00000]

<br/>

---

## 조건

### Constraints:

- 1 <= equations.length <= 20
- equations[i].length == 2
- 1 <= Ai.length, Bi.length <= 5
- values.length == equations.length
- 0.0 < values[i] <= 20.0
- 1 <= queries.length <= 20
- queries[i].length == 2
- 1 <= Cj.length, Dj.length <= 5
- Ai, Bi, Cj, Dj consist of lower case English letters and digits.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string[][]} equations
 * @param {number[]} values
 * @param {string[][]} queries
 * @return {number[]}
 */
var calcEquation = function(equations, values, queries) {

  // Step 1: Build the graph
  let graph = {};

  for (let i = 0; i < equations.length; i++) {

    let [numerator, denominator] = equations[i];

    let value = values[i];

    if (!graph[numerator]) {
      graph[numerator] = {};
    }

    if (!graph[denominator]) {
      graph[denominator] = {};
    }

    graph[numerator][denominator] = value;
    graph[denominator][numerator] = 1 / value;
  }

  // Step 2: Evaluate queries using DFS
  let evaluateQuery = (numerator, denominator, visited) => {

    if (!(numerator in graph) || !(denominator in graph)) {
      return -1.0;
    }

    if (numerator === denominator) {
      return 1.0;
    }

    visited.add(numerator);
    let neighbors = graph[numerator];

    for (let neighbor in neighbors) {

      if (!visited.has(neighbor)) {

        let result = evaluateQuery(neighbor, denominator, visited);

        if (result !== -1.0) {
          return neighbors[neighbor] * result;
        }
      }
    }

    return -1.0;
  };

  // Step 3: Process queries
  let results = [];

  for (let query of queries) {

    let [numerator, denominator] = query;
    let visited = new Set();
    let result = evaluateQuery(numerator, denominator, visited);
    console.log(visited)

    results.push(result);
  }

  return results;
};
```
