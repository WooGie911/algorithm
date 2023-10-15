# 행렬의 곱셈

## 문제설명 :

2차원 행렬 arr1과 arr2를 입력받아, arr1에 arr2를 곱한 결과를 반환하는 함수, solution을 완성해주세요.

---

## 제한 조건

- 행렬 arr1, arr2의 행과 열의 길이는 2 이상 100 이하입니다.
- 행렬 arr1, arr2의 원소는 -10 이상 20 이하인 자연수입니다.
- 곱할 수 있는 배열만 주어집니다.

<br/>

---

## 입출력 예

<img src ='행렬의 곱셈.png'>

<br/>

---

## 답안 ( 내 풀이 ) :

```
function solution(arr1, arr2) {
    var answer = [[]];

    let Arr1 =[]
    for(let i=0; i<arr1.length; i++){
        let Arr2 = []
        for(let k=0; k<arr2[0].length; k++){
            let sum =0
            for(let j=0; j<arr2.length; j++){ //arr2.length == arr1[i].length
                sum += arr1[i][j]*arr2[j][k]
            }
            Arr2.push(sum)
        }
        Arr1.push(Arr2)
    }

    return Arr1;
}
```
