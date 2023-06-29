# 240. Search a 2D Matrix II

## 문제 :

Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:

- Integers in each row are sorted in ascending from left to right.
- Integers in each column are sorted in ascending from top to bottom.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src = 'https://assets.leetcode.com/uploads/2020/11/24/searchgrid2.jpg'>

Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5
<br/>
Output: true

<br/>

### Example 2:

<img src = 'https://assets.leetcode.com/uploads/2020/11/24/searchgrid.jpg'>

Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 20
<br/>
Output: false

<br/>

---

## 조건

### Constraints:

- m == matrix.length
- n == matrix[i].length
- 1 <= n, m <= 300
- -10^9 <= matrix[i][j] <= 10^9
- All the integers in each row are sorted in ascending order.
- All the integers in each column are sorted in ascending order.
- -10^9 <= target <= 10^9

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */

const findfun = (matrix,target) =>{
    return matrix[0].find(element => element === target) ===undefined ? false:true
}


var searchMatrix = function(matrix, target) {
    if (matrix.length < 2) {
        return findfun(matrix,target)
    }

    const mid   = Math.floor(matrix.length/2);
    const left  = matrix.slice(0,mid);
    const right = matrix.slice(mid);

    return searchMatrix(left,target) ||  searchMatrix(right,target)
};
```
