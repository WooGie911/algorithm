# 733. Flood Fill

## 문제 :

An image is represented by an m x n integer grid image where image[i][j] represents the pixel value of the image.

You are also given three integers sr, sc, and color. You should perform a flood fill on the image starting from the pixel image[sr][sc].

To perform a flood fill, consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with color.

Return the modified image after performing the flood fill.

<br/>

---

## 입력 예시 :

<br/>

<img src = 'https://assets.leetcode.com/uploads/2021/06/01/flood1-grid.jpg'>

<br/>

### Example 1:

Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2
<br/>
Output: [[2,2,2],[2,2,0],[2,0,1]]
<br/>
Explanation: From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.
<br/>
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.

<br/>

### Example 2:

Input: image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, color = 0
<br/>
Output: [[0,0,0],[0,0,0]]
<br/>
Explanation: The starting pixel is already colored 0, so no changes are made to the image.

<br/>

---

## 조건

### Constraints:

- m == image.length
- n == image[i].length
- 1 <= m, n <= 50
- 0 <= image[i][j], - color < 216
- 0 <= sr < m
- 0 <= sc < n

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[][]} image
 * @param {number} sr
 * @param {number} sc
 * @param {number} color
 * @return {number[][]}
 */



var floodFill = function(image, sr, sc, newColor) {

    const color = image[sr][sc];
    const dfs = (image, r, c, color, newColor) => {
        if (image[r][c] === color) {
            image[r][c] = newColor;
            if (r >= 1) {
                dfs(image, r-1, c, color, newColor);
            }
            if (c >= 1) {
                dfs(image, r, c-1, color, newColor);
            }
            if (r+1 < image.length) {
                dfs(image, r+1, c, color, newColor);
            }
            if (c+1 < image[0].length) {
                dfs(image, r, c+1, color, newColor);
            }
        }
    }
    if (newColor !== color) {
        dfs(image, sr, sc, color, newColor);
        return image;
    } else {
        return image;
    }
};
```
