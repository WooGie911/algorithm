# JadenCase 문자열 만들기

## 문제설명 :

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다.

단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)

문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

---

## 제한 조건

- s는 길이 1 이상 200 이하인 문자열입니다.
- s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
  - 숫자는 단어의 첫 문자로만 나옵니다.
  - 숫자로만 이루어진 단어는 없습니다.
  - 공백문자가 연속해서 나올 수 있습니다.

<br/>

---

## 입출력 예

<img src ='JadenCase 문자열 만들기.png'>

<br/>

---

## 입출력 예 설명

### 입출력 예 #1

사전에서 첫 번째 단어는 "A"이고, 그다음은 "AA", "AAA", "AAAA", "AAAAA", "AAAAE", ... 와 같습니다. "AAAAE"는 사전에서 6번째 단어입니다.

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
//2중 반복문
function solution(s) {
    var answer = '';

    const sArr = s.split(" ")

    for(let i=0; i<sArr.length; i++){
        for(let j=0; j<sArr[i].length; j++){
            if(j===0){
                answer += sArr[i][j].toUpperCase()
            }else{
                answer += sArr[i][j].toLowerCase()
            }
        }
        if(i != sArr.length-1) answer += " "
    }


    return answer;
}


//조건 추가로 반복문 1개
function solution(s) {
    var answer = '';
    for (let i = 0; i < s.length; i++) {
      if (i === 0 || s[i-1] === " ") {
        answer += s[i].toUpperCase();
      } else {
        answer += s[i].toLowerCase();
      }
    }
    return answer;
}
```
