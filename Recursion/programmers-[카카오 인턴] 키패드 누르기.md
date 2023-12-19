# [카카오 인턴] 키패드 누르기

## 문제설명 :

스마트폰 전화 키패드의 각 칸에 다음과 같이 숫자들이 적혀 있습니다.

<img src ='https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/4b69a271-5f4a-4bf4-9ebf-6ebed5a02d8d/kakao_phone1.png'>

이 전화 키패드에서 왼손과 오른손의 엄지손가락만을 이용해서 숫자만을 입력하려고 합니다.
맨 처음 왼손 엄지손가락은 \* 키패드에 오른손 엄지손가락은 # 키패드 위치에서 시작하며, 엄지손가락을 사용하는 규칙은 다음과 같습니다.

1. 엄지손가락은 상하좌우 4가지 방향으로만 이동할 수 있으며 키패드 이동 한 칸은 거리로 1에 해당합니다.
2. 왼쪽 열의 3개의 숫자 1, 4, 7을 입력할 때는 왼손 엄지손가락을 사용합니다.
3. 오른쪽 열의 3개의 숫자 3, 6, 9를 입력할 때는 오른손 엄지손가락을 사용합니다.
4. 가운데 열의 4개의 숫자 2, 5, 8, 0을 입력할 때는 두 엄지손가락의 현재 키패드의 위치에서 더 가까운 엄지손가락을 사용합니다.

   4-1. 만약 두 엄지손가락의 거리가 같다면, 오른손잡이는 오른손 엄지손가락, 왼손잡이는 왼손 엄지손가락을 사용합니다.

순서대로 누를 번호가 담긴 배열 numbers, 왼손잡이인지 오른손잡이인 지를 나타내는 문자열 hand가 매개변수로 주어질 때, 각 번호를 누른 엄지손가락이 왼손인 지 오른손인 지를 나타내는 연속된 문자열 형태로 return 하도록 solution 함수를 완성해주세요.

---

## 제한사항

- numbers 배열의 크기는 1 이상 1,000 이하입니다.
- numbers 배열 원소의 값은 0 이상 9 이하인 정수입니다.
- hand는 "left" 또는 "right" 입니다.
  - "left"는 왼손잡이, "right"는 오른손잡이를 의미합니다.
- 왼손 엄지손가락을 사용한 경우는 L, 오른손 엄지손가락을 사용한 경우는 R을 순서대로 이어붙여 문자열 형태로 return 해주세요.

<br/>

---

## 입출력 예

<img src ='[카카오 인턴] 키패드 누르기1.png'>

<br/>

---

## 입출력 예 설명

### 입출력 예 #1

순서대로 눌러야 할 번호가 [1, 3, 4, 5, 8, 2, 1, 4, 5, 9, 5]이고, 오른손잡이입니다.

<img src ='[카카오 인턴] 키패드 누르기2.png'>

따라서 "LRLLLRLLRRL"를 return 합니다.

<br/>

### 입출력 예 #2

왼손잡이가 [7, 0, 8, 2, 8, 3, 1, 5, 7, 6, 2]를 순서대로 누르면 사용한 손은 "LRLLRRLLLRR"이 됩니다.

<br/>

### 입출력 예 #3

오른손잡이가 [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]를 순서대로 누르면 사용한 손은 "LLRLLRLLRL"이 됩니다.

<br/>

---

## 답안 ( 내 풀이 ) :

```
function findLocation (key) {
    let keypad = [[1,2,3],[4,5,6],[7,8,9],['*',0,'#']]
    for(let i=0; i< 4; i++){
        for(let j=0; j<3; j++){
            if(keypad[i][j] == key){
                return [i,j]
            }
        }
    }
}

function calculation (a,b) {
    return Math.abs(a[0] - b[0]) + Math.abs(a[1] - b[1])
}

function solution(numbers, hand) {
    var answer = '';

    const left = [1,4,7]
    const right = [3,6,9]
    let leftHand = [3,0]
    let rightHand = [3,2]

    for(let i=0; i<numbers.length; i++){
        if(left.includes(numbers[i])){
            answer += 'L'
            leftHand = findLocation(numbers[i])
        }else if(right.includes(numbers[i])){
            answer += 'R'
            rightHand = findLocation(numbers[i])
        }else{
            if(calculation(findLocation(numbers[i]),leftHand) < calculation(findLocation(numbers[i]),rightHand)){
                answer += 'L'
                leftHand = findLocation(numbers[i])
            }else if(calculation(findLocation(numbers[i]),leftHand) > calculation(findLocation(numbers[i]),rightHand)){
                answer += 'R'
                rightHand = findLocation(numbers[i])
            }else{
                if(hand == 'left'){
                    answer += 'L'
                    leftHand = findLocation(numbers[i])
                }else{
                    answer += 'R'
                    rightHand = findLocation(numbers[i])
                }
            }
        }
    }

    return answer;
}
```
