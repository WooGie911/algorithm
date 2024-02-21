# 징검다리

## 문제설명 :

출발지점부터 distance만큼 떨어진 곳에 도착지점이 있습니다. 그리고 그사이에는 바위들이 놓여있습니다. 바위 중 몇 개를 제거하려고 합니다.

예를 들어, 도착지점이 25만큼 떨어져 있고, 바위가 [2, 14, 11, 21, 17] 지점에 놓여있을 때 바위 2개를 제거하면 출발지점, 도착지점, 바위 간의 거리가 아래와 같습니다.

<img src ='징검다리 1.png'>

위에서 구한 거리의 최솟값 중에 가장 큰 값은 4입니다.

출발지점부터 도착지점까지의 거리 distance, 바위들이 있는 위치를 담은 배열 rocks, 제거할 바위의 수 n이 매개변수로 주어질 때, 바위를 n개 제거한 뒤 각 지점 사이의 거리의 최솟값 중에 가장 큰 값을 return 하도록 solution 함수를 작성해주세요.

---

## 제한사항

- 도착지점까지의 거리 distance는 1 이상 1,000,000,000 이하입니다.
- 바위는 1개 이상 50,000개 이하가 있습니다.
- n 은 1 이상 바위의 개수 이하입니다.

<br/>

---

## 입출력 예

<img src ='징검다리 2.png'>

<br/>

---

## 입출력 예 설명

문제에 나온 예와 같습니다.

<br/>

---

## 답안 ( 내 풀이 ) :

```
function solution(distance, rocks, n) {
    var answer = 0;

    let start = 1;
    let end = distance;
    rocks.sort((a,b)=>a-b)
    rocks.push(distance)

    while(start<=end){
        const mid = Math.floor((start+end)/2)
        let rock_count = 0
        let temp = 0
        for(let rock of rocks){
            if(rock - temp < mid) {
                rock_count++
            }else{
                temp = rock
            }
        }

        if(rock_count > n){
            end = mid -1
        }else{
            start = mid +1

        }
    }

    answer = end

    return answer;
}
```
