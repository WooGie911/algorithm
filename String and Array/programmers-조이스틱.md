# 조이스틱

## 문제설명 :

조이스틱으로 알파벳 이름을 완성하세요.

맨 처음엔 A로만 이루어져 있습니다.

ex) 완성해야 하는 이름이 세 글자면 AAA, 네 글자면 AAAA

조이스틱을 각 방향으로 움직이면 아래와 같습니다.

<img src ='조이스틱 1.png'>

예를 들어 아래의 방법으로 "JAZ"를 만들 수 있습니다.

<img src ='조이스틱 2.png'>

만들고자 하는 이름 name이 매개변수로 주어질 때, 이름에 대해 조이스틱 조작 횟수의 최솟값을 return 하도록 solution 함수를 만드세요.

---

## 제한사항

- name은 알파벳 대문자로만 이루어져 있습니다.
- name의 길이는 1 이상 20 이하입니다.

<br/>

---

## 입출력 예

<img src ='조이스틱 3.png'>

<br/>

---

## 답안 ( 내 풀이 ) :

```
function solution(name) {
    var answer = 0;

    const chars = name.split('').map((c) => findChar(c));
    let minMove = chars.length - 1;

    chars.forEach((char, idx) => {
        answer += char;

        let cursor = idx + 1;
        while(cursor < chars.length && chars[cursor] === 0) cursor++;

        minMove = Math.min(
            //정 방향으로 전진
            minMove,
            //뒤로 돌아가기
            (idx * 2) + chars.length - cursor,
            //뒤의 요소를 먼저 입력하기
            idx + 2 * (chars.length - cursor));
    })

    return answer + minMove;
}


const findChar = (find) => {
    //A의 아스키코드
    const min = 65;

    //Z의 아스키코드 + A->Z로 가는 횟수 1회
    const max = 90 + 1;

    const findCode = find.charCodeAt();

    return Math.min(findCode - min, max - findCode);
}
```
