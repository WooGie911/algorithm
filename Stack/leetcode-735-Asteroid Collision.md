# 735. Asteroid Collision

## 문제 :

We are given an array asteroids of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). <br/>
Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions.
<br/>
If two asteroids meet, the smaller one will explode.
<br/>
If both are the same size, both will explode.
<br/>
Two asteroids moving in the same direction will never meet.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: asteroids = [5,10,-5]
<br/>
Output: [5,10]
<br/>
Explanation:
<br/>
The 10 and -5 collide resulting in 10.
<br/>
The 5 and 10 never collide.

<br/>

### Example 2:

Input: asteroids = [8,-8]
<br/>
Output: []
<br/>
Explanation:
<br/>
The 8 and -8 collide exploding each other.

<br/>

### Example 3:

Input: asteroids = [10,2,-5]
<br/>
Output: [10]
<br/>
Explanation:
<br/>
The 2 and -5 collide resulting in -5.
<br/>
The 10 and -5 collide resulting in 10.

<br/>

---

## 조건

### Constraints:

- 2 <= asteroids.length <= 10^4
- -1000 <= asteroids[i] <= 1000
- asteroids[i] != 0

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} asteroids
 * @return {number[]}
 */
var asteroidCollision = function(asteroids) {
    const n = asteroids.length;
    const s = [];
    for (let i = 0; i < n; i++) {
        if (asteroids[i] > 0 || s.length === 0) {
            s.push(asteroids[i]);
        }
        else {
            while (s.length > 0 && s[s.length - 1] > 0 && s[s.length - 1] < Math.abs(asteroids[i])) {
                s.pop();
        }
        if (s.length > 0 && s[s.length - 1] === Math.abs(asteroids[i])) {
            s.pop();
        }
        else {
            if (s.length === 0 || s[s.length - 1] < 0) {
                s.push(asteroids[i]);
            }
        }
        }
    }
    const res = new Array(s.length);
    for (let i = s.length - 1; i >= 0; i--) {
        res[i] = s.pop();
    }
    return res;
}
```
