# N개의 최소공배수

## 문제설명 :

두 수의 최소공배수(Least Common Multiple)란 입력된 두 수의 배수 중 공통이 되는 가장 작은 숫자를 의미합니다.

예를 들어 2와 7의 최소공배수는 14가 됩니다. 정의를 확장해서, n개의 수의 최소공배수는 n 개의 수들의 배수 중 공통이 되는 가장 작은 숫자가 됩니다.

n개의 숫자를 담은 배열 arr이 입력되었을 때 이 수들의 최소공배수를 반환하는 함수, solution을 완성해 주세요.

---

## 제한사항

- arr은 길이 1이상, 15이하인 배열입니다.
- arr의 원소는 100 이하인 자연수입니다.

<br/>

---

## 입출력 예

<img src ='N개의 최소공배수.png'>

<br/>

---

## 답안 ( 내 풀이 ) :

```
function solution(arr) {
    let n = 1
    let flag = false
    arr.sort((a,b)=>a-b)

    while(!flag){
        n++
        for(let i = 1; i < arr.length; ++i){
            if((arr[0] * n) % arr[i]  === 0){
                flag = true
            } else {
                flag = false
                break
            }
        }
    }
    return arr[0] * n
}

// reduce 사용 (누산기)
function solution(arr) {
    return arr.reduce((acc, cur) => {
        const recursive = (min, max) =>{
          return (min % max) === 0 ? max : recursive(max, min % max);
        }

        let max = 0;
        return acc*cur / recursive(acc,cur);
    });
}

// 유클리드 호제법 gcd((a,b)=> gcd(b,a%b)) , lcm = a*b/gcd(a,b)
function getGcd(a, b) {
  if (b === 0) return a;
  return getGcd(b, a % b);
}

function solution(arr) {
  return arr.reduce((a, b) => (a * b) / getGcd(a, b));
}
```
