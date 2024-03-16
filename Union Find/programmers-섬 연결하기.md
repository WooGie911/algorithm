# 섬 연결하기

## 문제설명 :

n개의 섬 사이에 다리를 건설하는 비용(costs)이 주어질 때, 최소의 비용으로 모든 섬이 서로 통행 가능하도록 만들 때 필요한 최소 비용을 return 하도록 solution을 완성하세요.

다리를 여러 번 건너더라도, 도달할 수만 있으면 통행 가능하다고 봅니다.

예를 들어 A 섬과 B 섬 사이에 다리가 있고, B 섬과 C 섬 사이에 다리가 있으면 A 섬과 C 섬은 서로 통행 가능합니다.

---

## 제한사항

- 섬의 개수 n은 1 이상 100 이하입니다.
- costs의 길이는 ((n-1) \* n) / 2이하입니다.
- 임의의 i에 대해, costs[i][0] 와 costs[i] [1]에는 다리가 연결되는 두 섬의 번호가 들어있고, costs[i] [2]에는 이 두 섬을 연결하는 다리를 건설할 때 드는 비용입니다.
- 같은 연결은 두 번 주어지지 않습니다. 또한 순서가 바뀌더라도 같은 연결로 봅니다. 즉 0과 1 사이를 연결하는 비용이 주어졌을 때, 1과 0의 비용이 주어지지 않습니다.
- 모든 섬 사이의 다리 건설 비용이 주어지지 않습니다. 이 경우, 두 섬 사이의 건설이 불가능한 것으로 봅니다.
- 연결할 수 없는 섬은 주어지지 않습니다.

<br/>

---

## 입출력 예

<img src ='섬 연결하기.png'>

<br/>

---

## 입출력 예 설명

costs를 그림으로 표현하면 다음과 같으며, 이때 초록색 경로로 연결하는 것이 가장 적은 비용으로 모두를 통행할 수 있도록 만드는 방법입니다.

<img src ='https://grepp-programmers.s3.amazonaws.com/files/production/13e2952057/f2746a8c-527c-4451-9a73-42129911fe17.png'>

<br/>

---

## 답안 ( 내 풀이 ) :

```
const getParent = (parent, x) => {
  if(parent[x] === x) return x;
  return parent[x] = getParent(parent, parent[x]);
}

const unionParent = (parent, a, b) => {
  const n1 = getParent(parent, a);
  const n2 = getParent(parent, b);
  if(n1 < n2) return parent[n2] = n1;
  else return parent[n1] = n2;
}

const findParent = (parent, a, b) => {
  const n1 = getParent(parent, a);
  const n2 = getParent(parent, b);
  if(n1 === n2) return true;
  else return false;
}

function solution(n, costs) {
    var answer = 0;
    const parent = [];

    // 각 노드 별로 자기 자신 넣기.
    for(let i = 0; i < n; i++){
        parent.push(i);
    }

    // 간선 비용 기준 오름차순 정렬.
    costs.sort((a, b) => a[2] - b[2]);

    // 사이클이 형성 되지 않는다면 비용 추가.
    for(const cost of costs) {
        if(!findParent(parent, cost[0], cost[1])) {
        answer += cost[2];
        unionParent(parent, cost[0], cost[1]);
        }
    }

    return answer;
}

```
