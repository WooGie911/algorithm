# 숫자의 표현

## 문제설명 :

Finn은 요즘 수학공부에 빠져 있습니다. 수학 공부를 하던 Finn은 자연수 n을 연속한 자연수들로 표현 하는 방법이 여러개라는 사실을 알게 되었습니다.

예를들어 15는 다음과 같이 4가지로 표현 할 수 있습니다.

- 1 + 2 + 3 + 4 + 5 = 15
- 4 + 5 + 6 = 15
- 7 + 8 = 15
- 15 = 15

자연수 n이 매개변수로 주어질 때, 연속된 자연수들로 n을 표현하는 방법의 수를 return하는 solution를 완성해주세요.

---

## 제한 조건

- n은 10,000 이하의 자연수 입니다.

<br/>

---

## 입출력 예

<img src ='숫자의 표현.png'>

<br/>

---

## 입출력 예 설명

### 입출력 예 #1

문제의 예시와 같습니다.

<br/>

---

## 답안 ( 내 풀이 ) :

```
// 투포인터
function solution(n) {
    let count = 1
    let left = 1
    let sum = 1

    for(let right=1; right < n ; right++){

        sum += right

        if(sum === n) count++

        while(sum < n){
            sum -= left
            left++
        }
    }
    return count
}

//문제 직역
function solution(n) {
    let answer = 1
    let next = 1
    for(let i=1; i<n/2; i++){
        let sum = i

        while(sum < n){
            sum -= next
            next++
        }

        if(sum === n) answer++
    }
    return answer
}

//"주어진 자연수를 연속된 자연수의 합으로 표현하는 방법의 수" = "주어진 수의 홀수인 약수 갯수"
function solution(n) {
  let answer = 0;

  for(let i = 0; i <= n; i++) {
  	if(n%i === 0 && i%2 === 1) answer++;
  }

  return answer;
}

```
