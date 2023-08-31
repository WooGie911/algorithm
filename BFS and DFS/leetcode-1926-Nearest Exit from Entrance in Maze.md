# 1926. Nearest Exit from Entrance in Maze

## 문제 :

You are given an m x n matrix maze (0-indexed) with empty cells (represented as '.') and walls (represented as '+'). You are also given the entrance of the maze, where entrance = [entrancerow, entrancecol] denotes the row and column of the cell you are initially standing at.

In one step, you can move one cell up, down, left, or right. You cannot step into a cell with a wall, and you cannot step outside the maze. Your goal is to find the nearest exit from the entrance. An exit is defined as an empty cell that is at the border of the maze. The entrance does not count as an exit.

Return the number of steps in the shortest path from the entrance to the nearest exit, or -1 if no such path exists.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

<img src = 'https://assets.leetcode.com/uploads/2021/06/04/nearest1-grid.jpg'>

<br/>

Input: maze = [["+","+",".","+"],[".",".",".","+"],["+","+","+","."]], entrance = [1,2]
<br/>
Output: 1
<br/>
Explanation: There are 3 exits in this maze at [1,0], [0,2], and [2,3].
<br/>
Initially, you are at the entrance cell [1,2].

- You can reach [1,0] by moving 2 steps left.
- You can reach [0,2] by moving 1 step up.

It is impossible to reach [2,3] from the entrance.
Thus, the nearest exit is [0,2], which is 1 step away.

<br/>

### Example 2:

<img src = 'https://assets.leetcode.com/uploads/2021/06/04/nearesr2-grid.jpg'>

<br/>

Input: maze = [["+","+","+"],[".",".","."],["+","+","+"]], entrance = [1,0]
<br/>
Output: 2
<br/>
Explanation: There is 1 exit in this maze at [1,2].
<br/>
[1,0] does not count as an exit since it is the entrance cell.
<br/>
Initially, you are at the entrance cell [1,0].

- You can reach [1,2] by moving 2 steps right.

Thus, the nearest exit is [1,2], which is 2 steps away.

<br/>

### Example 3:

<img src = 'https://assets.leetcode.com/uploads/2021/06/04/nearest3-grid.jpg'>

<br/>

Input: maze = [[".","+"]], entrance = [0,0]
<br/>
Output: -1
<br/>
Explanation: There are no exits in this maze.

<br/>

---

## 조건

### Constraints:

- maze.length == m
- maze[i].length == n
- 1 <= m, n <= 100
- maze[i][j] is either '.' or '+'.
- entrance.length == 2
- 0 <= entrancerow < m
- 0 <= entrancecol < n
- entrance will always be an empty cell.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {character[][]} maze
 * @param {number[]} entrance
 * @return {number}
 */
const nearestExit = function(maze, entrance) {
    const mazeWidth = maze.length;
    const mazeHeight = maze[0].length;
    let hasCheckedEntranceCell = false;
    let stepsCounter = 0;

    const queue = [{ x: entrance[0], y: entrance[1] }];

    while (queue.length > 0) {
        const l = queue.length;

        for (let i = 0; i < l ; i++) {
            const position = queue.shift();

            if (maze[position.x][position.y] === '.') {
                maze[position.x][position.y] = 'x'; // visited

                if (hasCheckedEntranceCell && (
                    position.x === 0 ||
                    position.y === 0 ||
                    position.x === mazeWidth -1 ||
                    position.y === mazeHeight -1)) {
                    return stepsCounter;
                }

                hasCheckedEntranceCell = true;

                if (position.x + 1 < mazeWidth) queue.push({ x: position.x + 1, y: position.y });
                if (position.y + 1 < mazeHeight) queue.push({ x: position.x, y: position.y + 1 });
                if (position.x - 1 >= 0) queue.push({ x: position.x - 1, y: position.y });
                if (position.y - 1 >= 0) queue.push({ x: position.x, y: position.y - 1 });
            }
        }

        stepsCounter++;
    }

    return -1;
};
```
