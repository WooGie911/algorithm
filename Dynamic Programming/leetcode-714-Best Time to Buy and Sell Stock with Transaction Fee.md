# 714. Best Time to Buy and Sell Stock with Transaction Fee

## 문제 :

You are given an array prices where prices[i] is the price of a given stock on the ith day, and an integer fee representing a transaction fee.

Find the maximum profit you can achieve. You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction.

Note:

- You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
- The transaction fee is only charged once for each stock purchase and sale.

<br/>

---

## 입력 예시 :

<br/>

### Example 1:

Input: prices = [1,3,2,8,4,9], fee = 2
<br/>
Output: 8
<br/>
Explanation: The maximum profit can be achieved by:

- Buying at prices[0] = 1
- Selling at prices[3] = 8
- Buying at prices[4] = 4
- Selling at prices[5] = 9

The total profit is ((8 - 1) - 2) + ((9 - 4) - 2) = 8.

<br/>

### Example 2:

Input: prices = [1,3,7,5,10,3], fee = 3
<br/>
Output: 6

<br/>

---

## 조건

### Constraints:

- 1 <= prices.length <= 5 \* 10^4
- 1 <= prices[i] < 5 \* 10^4
- 0 <= fee < 5 \* 10^4

<br/>

---

## 답안 ( 내 풀이 ) :

```
/**
 * @param {number[]} prices
 * @param {number} fee
 * @return {number}
 */
var maxProfit = function(prices, fee) {
    let MaxP = -prices[0]
    let sell = 0

    for(let i = 1; i < prices.length; i++){
        TemP = MaxP
        MaxP = Math.max(MaxP, sell - prices[i])
        sell  = Math.max(sell, (TemP + prices[i]) - fee)
    }

    return sell
};
```
