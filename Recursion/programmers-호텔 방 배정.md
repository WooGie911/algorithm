# 호텔 방 배정

## 문제설명 :

"스노우타운"에서 호텔을 운영하고 있는 "스카피"는 호텔에 투숙하려는 고객들에게 방을 배정하려 합니다.

호텔에는 방이 총 k개 있으며, 각각의 방은 1번부터 k번까지 번호로 구분하고 있습니다.

처음에는 모든 방이 비어 있으며 "스카피"는 다음과 같은 규칙에 따라 고객에게 방을 배정하려고 합니다.

1. 한 번에 한 명씩 신청한 순서대로 방을 배정합니다.
2. 고객은 투숙하기 원하는 방 번호를 제출합니다.
3. 고객이 원하는 방이 비어 있다면 즉시 배정합니다.
4. 고객이 원하는 방이 이미 배정되어 있으면 원하는 방보다 번호가 크면서 비어있는 방 중 가장 번호가 작은 방을 배정합니다.

예를 들어, 방이 총 10개이고, 고객들이 원하는 방 번호가 순서대로 [1, 3, 4, 1, 3, 1] 일 경우 다음과 같이 방을 배정받게 됩니다.

<img src ='호텔 방 배정 1.png'>

전체 방 개수 k와 고객들이 원하는 방 번호가 순서대로 들어있는 배열 room_number가 매개변수로 주어질 때, 각 고객에게 배정되는 방 번호를 순서대로 배열에 담아 return 하도록 solution 함수를 완성해주세요.

---

## 제한사항

- k는 1 이상 1012 이하인 자연수입니다.
- room_number 배열의 크기는 1 이상 200,000 이하입니다.
- room_number 배열 각 원소들의 값은 1 이상 k 이하인 자연수입니다.
- room_number 배열은 모든 고객이 방을 배정받을 수 있는 경우만 입력으로 주어집니다.
  - 예를 들어, k = 5, room_number = [5, 5] 와 같은 경우는 방을 배정받지 못하는 고객이 발생하므로 이런 경우는 입력으로 주어지지 않습니다.

<br/>

---

## 입출력 예

<img src ='호텔 방 배정 2.png'>

<br/>

---

## 입출력 예 설명

### 입출력 예 #1

문제의 예시와 같습니다.

첫 번째 ~ 세 번째 고객까지는 원하는 방이 비어 있으므로 즉시 배정받을 수 있습니다.

네 번째 고객의 경우 1번 방을 배정받기를 원했는데, 1번 방은 빈 방이 아니므로, 1번 보다 번호가 크고 비어 있는 방 중에서 가장 번호가 작은 방을 배정해야 합니다.

1번 보다 번호가 크면서 비어있는 방은 [2번, 5번, 6번...] 방이며, 이중 가장 번호가 작은 방은 2번 방입니다. 따라서 네 번째 고객은 2번 방을 배정받습니다.

마찬가지로 5, 6번째 고객은 각각 5번, 6번 방을 배정받게 됩니다.

<br/>

### 입출력 예 #2

"AAAE"는 "A", "AA", "AAA", "AAAA", "AAAAA", "AAAAE", "AAAAI", "AAAAO", "AAAAU"의 다음인 10번째 단어입니다.

<br/>

### 입출력 예 #3

"I"는 1563번째 단어입니다.

<br/>

### 입출력 예 #4

"EIO"는 1189번째 단어입니다.

<br/>

---

## 답안 ( 내 풀이 ) :

```
// 방 배열을 저장하며 비교하여 배정하는 방식.
// 런타임 에러.
function solution(k, room_number) {
    const answer = new Array(room_number.length).fill(0)
    const room = new Array(k).fill(0)

    const rec = (index,num) => {
        if(room[num] != 0){
            rec(index,num+1)
        }else{
            room[num] = num
            answer[index] = num
            return
        }
    }
    for(let i=0; i<room_number.length; i++){
        rec(i,room_number[i])
    }

    return answer;
}

// map을 사용하여 효율성 해결.
function solution(k, room_number) {
    const answer = new Array(room_number.length).fill(0)
    const rooms = new Map();

    const rec = (num) => {
        if(!rooms.get(num)){
            rooms.set(num, num + 1);

            return num;
        }
        const newNum = rec(rooms.get(num));
        rooms.set(num, newNum + 1);

        return newNum;
    }

    for(let i=0; i<room_number.length; i++){
        answer[i] = rec(room_number[i])
    }

    return answer;
}
```
