# 줄 서는 방법

## 문제설명 :

n명의 사람이 일렬로 줄을 서고 있습니다. n명의 사람들에게는 각각 1번부터 n번까지 번호가 매겨져 있습니다.

n명이 사람을 줄을 서는 방법은 여러가지 방법이 있습니다.

예를 들어서 3명의 사람이 있다면 다음과 같이 6개의 방법이 있습니다.

- [1, 2, 3]
- [1, 3, 2]
- [2, 1, 3]
- [2, 3, 1]
- [3, 1, 2]
- [3, 2, 1]

사람의 수 n과, 자연수 k가 주어질 때, 사람을 나열 하는 방법을 사전 순으로 나열 했을 때, k번째 방법을 return하는 solution 함수를 완성해주세요.

---

## 제한사항

- n은 20이하의 자연수 입니다.
- k는 n! 이하의 자연수 입니다.

<br/>

---

## 입출력 예

<img src ='줄 서는 방법.png'>

<br/>

---

## 입출력 예 설명

### 입출력 예 #1

문제의 예시와 같습니다.

<br/>

---

## 답안 ( 내 풀이 ) :

```
function solution (n, k) {
    const answer = []
    const indexArr = Array.from({length: n}, (_, idx) => idx + 1)
    const arr = new Array(n).fill(1);
    for(let i = 1; i < n; i++) arr[i] = arr[i-1] + 1

    let nth = k-1

    while(arr.length) {
        if(nth === 0) {
            answer.push(...arr)
            break;
        }
        const fact = factorial(arr.length - 1)
        const index = nth / fact >> 0
        nth = nth % fact
        answer.push(arr[index])
        arr.splice(index, 1)
    }
    return answer
}

const factorial = (n) => {
  let res = 1;
  for(let i = 2; i <= n; i++) res *= i;
  return res;
}
```
