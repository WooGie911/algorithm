# 단어 변환

## 문제설명 :

두 개의 단어 begin, target과 단어의 집합 words가 있습니다.

아래와 같은 규칙을 이용하여 begin에서 target으로 변환하는 가장 짧은 변환 과정을 찾으려고 합니다.

1. 한 번에 한 개의 알파벳만 바꿀 수 있습니다.

2. words에 있는 단어로만 변환할 수 있습니다.

예를 들어 begin이 "hit", target가 "cog", words가 ["hot","dot","dog","lot","log","cog"]라면 "hit" -> "hot" -> "dot" -> "dog" -> "cog"와 같이 4단계를 거쳐 변환할 수 있습니다.

두 개의 단어 begin, target과 단어의 집합 words가 매개변수로 주어질 때, 최소 몇 단계의 과정을 거쳐 begin을 target으로 변환할 수 있는지 return 하도록 solution 함수를 작성해주세요.

---

## 제한사항

- 각 단어는 알파벳 소문자로만 이루어져 있습니다.
- 각 단어의 길이는 3 이상 10 이하이며 모든 단어의 길이는 같습니다.
- words에는 3개 이상 50개 이하의 단어가 있으며 중복되는 단어는 없습니다.
- begin과 target은 같지 않습니다.
- 변환할 수 없는 경우에는 0를 return 합니다.

<br/>

---

## 입출력 예

<img src ='단어 변환.png'>

<br/>

---

## 입출력 예 설명

### 입출력 예 #1

문제의 예시와 같습니다.

<br/>

### 입출력 예 #2

target인 "cog"는 words 안에 없기 때문에 변환할 수 없습니다.

<br/>

---

## 답안 ( 내 풀이 ) :

```
const checkWords = (str1, str2) =>{
    let cnt = 0
    for(let i=0; i<str1.length; i++){
        if(str1[i] !== str2[i]){
            cnt++
        }
    }

    return cnt > 1 ? false : true
}

function solution(begin, target, words) {
    var answer = 51;
    let visited = new Array(words.length).fill(false)
    let cnt = 0

    if(!words.includes(target)){
        return 0
    }

    const DFS = (currentWord, count) => {
        if(currentWord == target){
            return answer = Math.min(answer,count)
        }

        for(let i=0; i<words.length; i++){
            if(checkWords(words[i], currentWord) && !visited[i]){
                visited[i] = true
                DFS(words[i], count+1)
                visited[i] = false
            }
        }
    }

    DFS(begin, cnt)

    return answer;
}
```
