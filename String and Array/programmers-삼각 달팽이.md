# 삼각 달팽이

## 문제설명 :

정수 n이 매개변수로 주어집니다. 다음 그림과 같이 밑변의 길이와 높이가 n인 삼각형에서 맨 위 꼭짓점부터 반시계 방향으로 달팽이 채우기를 진행한 후, 첫 행부터 마지막 행까지 모두 순서대로 합친 새로운 배열을 return 하도록 solution 함수를 완성해주세요.

<img src ='https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/e1e53b93-dcdf-446f-b47f-e8ec1292a5e0/examples.png'>

---

## 제한사항

- n은 1 이상 1,000 이하입니다.

<br/>

---

## 입출력 예

<img src ='삼각 달팽이.png'>

<br/>

---

## 입출력 예 설명

### 입출력 예 #1

문제의 예시와 같습니다.

<br/>

### 입출력 예 #2

문제의 예시와 같습니다.

<br/>

### 입출력 예 #3

문제의 예시와 같습니다.

<br/>

---

## 답안 ( 내 풀이 ) :

```
function solution(n) {
    let num = 0
    let currentX = -1;
    let currentY = 0;

    const Arr = Array(n).fill().map((_, i) => Array(i + 1).fill(0));

    // n값을 3씩 줄여가며 n의 값이 유효할 때까지 반복
    while (n > 0) {

        // 위에서 아래로 내려가는 대각선
        for (let i = 0; i < n; i++) {
            currentX++;
            num++;
            Arr[currentX][currentY] = num;
        }

        // 왼쪽에서 오른쪽으로 이동
        for (let j = 0; j < n - 1; j++) {
            currentY++;
            num++;
            Arr[currentX][currentY] = num;
        }

        // 아래에서 위로 내려가는 대각선
        for (let k = 0; k < n - 2; k++) {
            currentX--;
            currentY--;
            num++;
            Arr[currentX][currentY] = num;
        }

        n -= 3;
    }

    return Arr.flat();
}
```
