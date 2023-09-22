# 72. Edit Distance

## 문제 :

Given two strings word1 and word2, return the minimum number of operations required to convert word1 to word2.

You have the following three operations permitted on a word:

- Insert a character
- Delete a character
- Replace a character

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: word1 = "horse", word2 = "ros"
<br/>
Output: 3
<br/>
Explanation:
<br/>
horse -> rorse (replace 'h' with 'r')
<br/>
rorse -> rose (remove 'r')
<br/>
rose -> ros (remove 'e')

<br/>

Input: word1 = "intention", word2 = "execution"
<br/>
Output: 5
<br/>
Explanation:
<br/>
intention -> inention (remove 't')
<br/>
inention -> enention (replace 'i' with 'e')
<br/>
enention -> exention (replace 'n' with 'x')
<br/>
exention -> exection (replace 'n' with 'c')
<br/>
exection -> execution (insert 'u')

<br/>

---

## 조건

### Constraints:

- 0 <= word1.length, word2.length <= 500
- word1 and word2 consist of lowercase English letters.

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {string} word1
 * @param {string} word2
 * @return {number}
 */
var minDistance = function(word1, word2) {
    const row = word1.length;
    const col = word2.length;

    let dp = new Array(row + 1).fill(0).map(() => new Array(col + 1).fill(0));

    for (let i = 0; i <= row; i++) dp[i][0] = i;
    for (let i = 0; i <= col; i++) dp[0][i] = i;

    for (let i = 1; i <= row; i++) {
        for (let j = 1; j <= col; j++) {
            if (word1.charAt(i - 1) === word2.charAt(j - 1)) {
                dp[i][j] = dp[i - 1][j - 1];
            } else {
                let Replace = dp[i - 1][j - 1];
                let Insert = dp[i][j - 1];
                let Delete = dp[i - 1][j];
                dp[i][j] = Math.min(Replace, Insert, Delete) + 1;
            }
        }
    }

    return dp[row][col];
};
```
