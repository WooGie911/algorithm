# 463. Island Perimeter

## 문제 :

You are given row x col grid representing a map where grid[i][j] = 1 represents land and grid[i][j] = 0 represents water.

Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells).

The island doesn't have "lakes", meaning the water inside isn't connected to the water around the island. One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src='https://assets.leetcode.com/uploads/2018/10/12/island.png'>

Input: grid = [[0,1,0,0],[1,1,1,0],[0,1,0,0],[1,1,0,0]]
<br/>
Output: 16
<br/>
Explanation: The perimeter is the 16 yellow stripes in the image above.

<br/>

### Example 2:

Input: grid = [[1]]
<br/>
Output: 4

<br/>

### Example 3:

Input: grid = [[1,0]]
<br/>
Output: 4

<br/>

---

## 조건

### Constraints:

- row == grid.length
- col == grid[i].length
- 1 <= row, col <= 100
- grid[i][j] is 0 or 1.
- There is exactly one island in grid.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[][]} grid
 * @return {number}
 */
var islandPerimeter = function(grid) {

    let m = grid.length
    let n = grid[0].length

    let sum =0

    const changeNum = (array,i,j) => {

        let count = 4

        if(i!=0 && array[i-1][j] !=0) count --
        if(j!=0 && array[i][j-1] !=0) count --
        if(i!=m-1 && array[i+1][j] !=0) count --
        if(j!=n-1 && array[i][j+1] !=0) count --

        sum += count

    }

    for(let i =0 ; i<m ; i++){
        for(let j=0 ; j <n ; j++){
            if(grid[i][j]===1){
                changeNum(grid,i,j)
            }

        }
    }

    return sum
};
```
