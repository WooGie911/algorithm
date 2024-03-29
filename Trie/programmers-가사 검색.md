# 가사 검색

## 문제설명 :

친구들로부터 천재 프로그래머로 불리는 "프로도"는 음악을 하는 친구로부터 자신이 좋아하는 노래 가사에 사용된 단어들 중에 특정 키워드가 몇 개 포함되어 있는지 궁금하니 프로그램으로 개발해 달라는 제안을 받았습니다.

그 제안 사항 중, 키워드는 와일드카드 문자중 하나인 '?'가 포함된 패턴 형태의 문자열을 뜻합니다.

와일드카드 문자인 '?'는 글자 하나를 의미하며, 어떤 문자에도 매치된다고 가정합니다.

예를 들어 "fro??"는 "frodo", "front", "frost" 등에 매치되지만 "frame", "frozen"에는 매치되지 않습니다.

가사에 사용된 모든 단어들이 담긴 배열 words와 찾고자 하는 키워드가 담긴 배열 queries가 주어질 때, 각 키워드 별로 매치된 단어가 몇 개인지 순서대로 배열에 담아 반환하도록 solution 함수를 완성해 주세요.

---

## 가사 단어 제한사항

- words의 길이(가사 단어의 개수)는 2 이상 100,000 이하입니다.
- 각 가사 단어의 길이는 1 이상 10,000 이하로 빈 문자열인 경우는 없습니다.
- 전체 가사 단어 길이의 합은 2 이상 1,000,000 이하입니다.
- 가사에 동일 단어가 여러 번 나올 경우 중복을 제거하고 words에는 하나로만 제공됩니다.
- 각 가사 단어는 오직 알파벳 소문자로만 구성되어 있으며, 특수문자나 숫자는 포함하지 않는 것으로 가정합니다.

<br/>

---

## 검색 키워드 제한사항

- queries의 길이(검색 키워드 개수)는 2 이상 100,000 이하입니다.
- 각 검색 키워드의 길이는 1 이상 10,000 이하로 빈 문자열인 경우는 없습니다.
- 전체 검색 키워드 길이의 합은 2 이상 1,000,000 이하입니다.
- 검색 키워드는 중복될 수도 있습니다.
- 각 검색 키워드는 오직 알파벳 소문자와 와일드카드 문자인 '?' 로만 구성되어 있으며, 특수문자나 숫자는 포함하지 않는 것으로 가정합니다.
- 검색 키워드는 와일드카드 문자인 '?'가 하나 이상 포함돼 있으며, '?'는 각 검색 키워드의 접두사 아니면 접미사 중 하나로만 주어집니다.
  - 예를 들어 "??odo", "fro??", "?????"는 가능한 키워드입니다.
  - 반면에 "frodo"('?'가 없음), "fr?do"('?'가 중간에 있음), "?ro??"('?'가 양쪽에 있음)는 불가능한 키워드입니다.

<br/>

---

## 입출력 예

<img src ='가사 검색.png'>

<br/>

---

## 입출력 예 설명

- "fro??"는 "frodo", "front", "frost"에 매치되므로 3입니다.
- "????o"는 "frodo", "kakao"에 매치되므로 2입니다.
- "fr???"는 "frodo", "front", "frost", "frame"에 매치되므로 4입니다.
- "fro???"는 "frozen"에 매치되므로 1입니다.
- "pro?"는 매치되는 가사 단어가 없으므로 0 입니다.

---

## 답안 ( 내 풀이 ) :

```
// 정규식 사용. 효율성 통과 X.
function solution(words, queries) {
    var answer = [];

    const regex = queries.map(id => new RegExp(`^${id.replaceAll('?', '.')}$`));

    for(let querie of regex){
        let cnt = 0
        for(let word of words){
            if(word.match(querie)){
                cnt++
            }
        }
        answer.push(cnt)
    }

    return answer;
}

// 효율성 통과를 위해 트리 사용.

class Trie {
    constructor() {
        this.children = {};
        this.count = 0;
    }

    insert(word) {
        let trie = this;
        ++this.count;

        for (const letter of word) {
            if (typeof trie.children[letter] === 'undefined') {
                trie.children[letter] = new Trie();
            }

            trie = trie.children[letter];
            ++trie.count;
            // 문자열이 삽입될 때마다 count
            // queries에 있는 문자열들을 search했을 때 길이가 같은 단어가 몇개인지 바로 알 수 있음
        }
    }

  // node에 등록되어 있는 단어의 수를 return
    getCount(query) {
        let trie = this;
        for (const letter of query) {
            if (letter === '?') {
                return trie.count;
            } else if (typeof trie.children[letter] === 'undefined') {
                return 0;
            }

            trie = trie.children[letter];
        }
    }
}

function solution(words, queries) {
    const tries = {}; // 일반 Trie
    const reverseds = {}; // Reverse Trie

    for (const word of words) {
        const length = word.length;

      	//단어의 길이을 구하고, 그 길이에 해당하는 Trie 배열에 새로운 Trie를 추가해주면 됩니다.
       // ex) length = 5, 길이가 5인 Trie들이 모인 Trie[5]에 해당 단어를 추가해주면 됩니다.
        if (typeof tries[length] === 'undefined') {
            tries[length] = new Trie();
            reverseds[length] = new Trie();
        }

       // 인덱스가 tries[i]의 길이값인 곳에 단어 길이 i인 문자열만 삽입된 tries, reverseds를 만듦
       // ?가 뒤에 있는 경우
        tries[length].insert(word);
       // ?가 앞에 있는 경우
      	reverseds[length].insert([...word].reverse().join(''));
    }

    return queries.map((query) => {
        const length = query.length;

        // 해당 length에 해당하는 Trie 배열을 탐색
      	// 만약 undefined값이 나온다면 사전에 등록되어 있지 않은 것 -> 0반환
        if (typeof tries[length] === 'undefined') {
            return 0;
        }

      	// 처음으로 ?가 나오는 순간에 현재 노드의 등록된 단어수를 반환
        if (query[0] === '?') {
            return reverseds[length].getCount([...query].reverse().join(''));
        }

        return tries[length].getCount(query);
    });
}
```
