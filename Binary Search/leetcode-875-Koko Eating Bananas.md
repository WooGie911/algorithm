# 875. Koko Eating Bananas

## 문제 :

Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.

Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return the minimum integer k such that she can eat all the bananas within h hours.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: piles = [3,6,7,11], h = 8
<br/>
Output: 4

<br/>

### Example 2:

Input: piles = [30,11,23,4,20], h = 5
<br/>
Output: 30

<br/>

### Example 3:

Input: piles = [30,11,23,4,20], h = 6
<br/>
Output: 23

<br/>

---

## 조건

### Constraints:

- 1 <= piles.length <= 10^4
- piles.length <= h <= 10^9
- 1 <= piles[i] <= 10^9

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} piles
 * @param {number} h
 * @return {number}
 */
var minEatingSpeed = function(piles, h) {
    let min = 1
    let max = Math.max(...piles)
    let best = max

    while (min <= max) {
        mid = Math.floor((min+(max-min)/2))
        let hours = 0
        for(let p of piles){
            hours+=Math.ceil(p/mid);
        }

        if (hours <= h) {
            best = mid
            max = mid - 1
        } else
            min = mid + 1
    }

    return best
};
```
