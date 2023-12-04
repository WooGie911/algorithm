# 933. Number of Recent Calls

## 문제 :

You have a RecentCounter class which counts the number of recent requests within a certain time frame.

Implement the RecentCounter class:

- RecentCounter() Initializes the counter with zero recent requests.
- int ping(int t) Adds a new request at time t, where t represents some time in milliseconds, and returns the number of requests that has happened in the past 3000 milliseconds (including the new request). Specifically, return the number of requests that have happened in the inclusive range [t - 3000, t].

It is guaranteed that every call to ping uses a strictly larger value of t than the previous call.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input
<br/>
["RecentCounter", "ping", "ping", "ping", "ping"]
<br/>
[[], [1], [100], [3001], [3002]]
Output
[null, 1, 2, 3, 3]

Explanation
<br/>
RecentCounter recentCounter = new RecentCounter();
<br/>
recentCounter.ping(1); // requests = [1], range is [-2999,1], return 1
<br/>
recentCounter.ping(100); // requests = [1, 100], range is [-2900,100], return 2
<br/>
recentCounter.ping(3001); // requests = [1, 100, 3001], range is [1,3001], return 3
<br/>
recentCounter.ping(3002); // requests = [1, 100, 3001, 3002], range is [2,3002], return 3

<br/>

---

## 조건

### Constraints:

- 1 <= t <= 10^9
- Each test case will call ping with strictly increasing values of t.
- At most 10^4 calls will be made to ping.

<br/>

---

## 답안 ( 내 풀이 ) :

```
var RecentCounter = function() {
    this.arr = []
    this.left = 0
};

/**
 * @param {number} t
 * @return {number}
 */
RecentCounter.prototype.ping = function(t) {
    this.arr.push(t)
    while (this.arr[this.arr.length - 1] - this.arr[this.left] > 3000){
        this.left++
    }
    return this.arr.length - this.left
};

/**
 * Your RecentCounter object will be instantiated and called as such:
 * var obj = new RecentCounter()
 * var param_1 = obj.ping(t)
 */
```