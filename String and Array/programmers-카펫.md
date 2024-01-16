# 카펫

## 문제설명 :

Leo는 카펫을 사러 갔다가 아래 그림과 같이 중앙에는 노란색으로 칠해져 있고 테두리 1줄은 갈색으로 칠해져 있는 격자 모양 카펫을 봤습니다.

<img src ='https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/b1ebb809-f333-4df2-bc81-02682900dc2d/carpet.png'>

Leo는 집으로 돌아와서 아까 본 카펫의 노란색과 갈색으로 색칠된 격자의 개수는 기억했지만, 전체 카펫의 크기는 기억하지 못했습니다.

Leo가 본 카펫에서 갈색 격자의 수 brown, 노란색 격자의 수 yellow가 매개변수로 주어질 때 카펫의 가로, 세로 크기를 순서대로 배열에 담아 return 하도록 solution 함수를 작성해주세요.

---

## 제한사항

- 갈색 격자의 수 brown은 8 이상 5,000 이하인 자연수입니다.
- 노란색 격자의 수 yellow는 1 이상 2,000,000 이하인 자연수입니다.
- 카펫의 가로 길이는 세로 길이와 같거나, 세로 길이보다 깁니다.

<br/>

---

## 입출력 예

<img src ='카펫.png'>

<br/>

---

## 답안 ( 내 풀이 ) :

```
// 노란 width = x, 노란 height = y로 생각 했을 때
// x * y = yellow, (x+2) * (y+2) = yellow + brown
// y = yellow / x , 2(x+y) + 4 = brown
// x = ((brown - 4) / 2 + Math.sqrt(Math.pow((brown-4)/2,2) - 4 * yellow)) / 2
// y = yellow / x

function solution(brown, yellow) {
    const x = ((brown - 4) / 2 + Math.sqrt(Math.pow((brown-4)/2,2) - 4 * yellow)) / 2
    const y = yellow / x

    return [Math.max(x+2,y+2),Math.min(x+2,y+2)]
}

```
