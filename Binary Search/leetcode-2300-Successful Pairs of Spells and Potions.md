# 2300. Successful Pairs of Spells and Potions

## 문제 :

You are given two positive integer arrays spells and potions, of length n and m respectively, where spells[i] represents the strength of the ith spell and potions[j] represents the strength of the jth potion.

You are also given an integer success. A spell and potion pair is considered successful if the product of their strengths is at least success.

Return an integer array pairs of length n where pairs[i] is the number of potions that will form a successful pair with the ith spell.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: spells = [5,1,3], potions = [1,2,3,4,5], success = 7
<br/>
Output: [4,0,3]
<br/>
Explanation:

- 0th spell: 5 \* [1,2,3,4,5] = [5,<u>**10**</u>,<u>**15**</u>,<u>**20**</u>,<u>**25**</u>]. 4 pairs are successful.
- 1st spell: 1 \* [1,2,3,4,5] = [1,2,3,4,5]. 0 pairs are successful.
- 2nd spell: 3 \* [1,2,3,4,5] = [3,6,<u>**9**</u>,<u>**12**</u>,<u>**15**</u>]. 3 pairs are successful.
  Thus, [4,0,3] is returned.

<br/>

### Example 2:

Input: spells = [3,1,2], potions = [8,5,8], success = 16
<br/>
Output: [2,0,2]
<br/>
Explanation:

- 0th spell: 3 \* [8,5,8] = [<u>**24**</u>,15,<u>**24**</u>]. 2 pairs are successful.
- 1st spell: 1 \* [8,5,8] = [8,5,8]. 0 pairs are successful.
- 2nd spell: 2 \* [8,5,8] = [<u>**16**</u>,10,<u>**16**</u>]. 2 pairs are successful.
  Thus, [2,0,2] is returned.

<br/>

---

## 조건

### Constraints:

- n == spells.length
- m == potions.length
- 1 <= n, m <= 10^5
- 1 <= spells[i], potions[i] <= 10^5
- 1 <= success <= 10^10

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} spells
 * @param {number[]} potions
 * @param {number} success
 * @return {number[]}
 */
var successfulPairs = function(spells, potions, success) {
    potions.sort((a, b) => a - b)
    const result = []
    for(let i=0; i<spells.length; i++){
        let low = 0
        let high = potions.length-1
        while (low <= high) {
            let mid = low + ~~((high - low) / 2)
            if (potions[mid] * spells[i] >= success) {
                high = mid - 1
            } else {
                low = mid + 1;
            }
        }
        result.push(potions.length - low)
    }
    return result
};
```
