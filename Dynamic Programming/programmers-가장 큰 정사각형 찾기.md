# 가장 큰 정사각형 찾기

## 문제설명 :

1와 0로 채워진 표(board)가 있습니다.

표 1칸은 1 x 1 의 정사각형으로 이루어져 있습니다.

표에서 1로 이루어진 가장 큰 정사각형을 찾아 넓이를 return 하는 solution 함수를 완성해 주세요.

(단, 정사각형이란 축에 평행한 정사각형을 말합니다.)

예를 들어

<img src ='가장 큰 정사각형 찾기 1.png'>

가 있다면 가장 큰 정사각형은

<img src ='가장 큰 정사각형 찾기 2.png'>

가 되며 넓이는 9가 되므로 9를 반환해 주면 됩니다.

---

## 제한사항

- 표(board)는 2차원 배열로 주어집니다.
- 표(board)의 행(row)의 크기 : 1,000 이하의 자연수
- 표(board)의 열(column)의 크기 : 1,000 이하의 자연수
- 표(board)의 값은 1또는 0으로만 이루어져 있습니다.

<br/>

---

## 입출력 예

<img src ='가장 큰 정사각형 찾기 3.png'>

<br/>

---

## 입출력 예 설명

### 입출력 예 #1

위의 예시와 같습니다.

<br/>

### 입출력 예 #2

| 0 | 0 | 1 | 1 |

| 1 | 1 | 1 | 1 |

로 가장 큰 정사각형의 넓이는 4가 되므로 4를 return합니다.

<br/>

---

## 답안 ( 내 풀이 ) :

```
function solution(board) {
  var answer = 0;
  const row = board.length;
  const column = board[0].length;

  if (row <= 1 || column <= 1) return 1;

  for (let i = 1; i < row; i++) {
    for (let j = 1; j < column; j++) {
      if (board[i][j] > 0) {
        const up = board[i - 1][j];
        const left = board[i][j - 1];
        const cross = board[i - 1][j - 1];
        const minNum = Math.min(up, left, cross);
        board[i][j] = minNum + 1;
        answer = Math.max(answer, board[i][j]);
      }
    }
  }

  return answer ** 2;
}
```
