# Graph

## 기초 용어 정리

- 정점(Vertex , Node) : Vertex라고도 표현하고 Node라는 용어를 사용하기도 한다. 같은 것이라고 생각하면 되겠다. 정점은 위 그래프에서 동그라미 친 1,2,3,4,5,6 과 같은 각각의 지점을 의미한다.

- 간선(Edge, Link) : 역시 Edge와 Link 두가지 용어를 사용한다. 그래프에서 각 정점들을 연결하는 선이다. 화살표 표시가 된 것도 있고 그냥 직선으로 표시된 것도 있는데, 둘 다 '간선' 이라고 사용한다.

- 가중치 : 간선 위에 표시된 숫자이다. 가중치가 있는 그래프가 있고 없는 그래프가 있는데, 가중치가 없다면 모두 동일한 가중치를 가진다고 보면 된다. 해당 간선을 타고 이동할 때 필요한 비용 등을 표현하는 것에 사용된다.

- Directed Graph : 말 그대로 방향성이 있는 그래프이다. 위 두개의 그래프 중 왼쪽 그래프가 Directed Graph이다. 간선의 방향에 따른 이동만이 가능한 경우에 사용한다.

- undirected Graph : 오른쪽 그래프 처럼 간선이 방향성이 없는 일반 실선으로 표시된 그래프이다. 방향성이 없다고 이동을 못하는 것이 아니라, 모든 간선들은 양방향 이동이 가능함을 의미한다.

- Self-loops : 정점에서 자기 자신으로 돌아오는 간선을 뜻한다. 오른쪽 그래프에서 6번 정점에 연결된 가중치 2의 간선이 이에 해당한다.

- Adjacency : 방향성이 있는 directed graph에서의 간선으로 연결된 인접 정점을 뜻한다. 하지만 이는 쌍방향 모두에 적용되는 것이 아니다. 예를들어 위 Directed Graph에서 정점4가 정점1에 Adjacency하다고 한다면, 정점1은 정점4에 Adjacency하다고 표현할 수 없다.

- Degree : 각 정점에 연결되어 있는 Edge들의 수이다. 이 중 out-degree는 해당 정점에서 나가는 간선을, in-degree는 해당 정점으로 들어오는 간선이다. 따라서 특정 정점에서의 모든 out-degree와 in-degree를 더하면 그 정점의 Degree가 된다.

- Path : 정점 A에서 정점 B로 이동할 수 있는 경로를 의미한다. 그래프 내에서 정점 끼리의 path는 하나만 존재할 수 있는 것이 아니라, 여러 종류의 길이 존재할 수 있다. 또한 두 개의 정점이 이동할 수 없기도 한다. 여기서 정점A 에서 정점 B로 가는 Path가 존재한다면 정점 B는 정점 A로부터 reachable하다고 표현한다.

- Simple Path : 경로 상의 모든 정점들이 중복되지 않는다면 이 경로를 simple path라고 한다. 예를 들어 위의 그래프에서 경로 <1,4,2,3,5> 는 simple path 라고 할 수 있지만 <1,4,2,1>은 simple path가 아니다.

- Cycle : 그래프가 path를 따라 동일한 정점으로 돌아올 수 있는 경우를 의미한다. 위 그래프의 왼쪽 컴포넌트는 <1,4,2> path가 cycle을 이룬다. 이 중, 돌아오는 경로 안에서 중복된 노드가 시작점(끝점) 이외에는 발생하지 않는 경우를 Simple Cycle이라고 표현한다.

- An acyclic graph : 그래프에 싸이클이 없는 경우 그 그래프를 acyclic graph라고 부른다.

- Connected Graph : 기본적으로 connected graph는 방향성이 없는 그래프이다. 모든 쌍의 정점들이 path로 연결이 가능한 그래프를 connected graph라고 칭한다.

- Connected Component : 위 그래프 전체도 하나의 그래프이다. 이 중 방향이없는 그래프의 정점 하위 집합을 최대로 연결한 것을 Connected Component라고 한다.

- Forest : 그래프 중 Acyclic하고 Undirected하면 Forest라고 부른다.

- Tree : Forest에서 하나 하나의 Component들은 Tree가 된다. 따라서 Connected, Acyclic, Undirected 모두를 만족하는 graph가 Tree라고 볼 수 있다.

- Dag : Tree가 방향성이 없고 싸이클이 존재하지 않는 그래프라면, Dag는 방향성이 있는 그래프 중 싸이클이 나오지 않는 그래프를 의미한다.

## 그래프의 정의

그래프라 하면 일반적으로 '정점(노드)'과 '간선(엣지)'으로 이루어진 자료구조를 의미한다.

또한 간선의 방향 유무에 따라서 단방향 그래프와 무방향 그래프(또는 양방향)로 나뉜다.

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfMTgx/MDAxNDg1ODQzNTQ4NTgz.nh0nifj5nlyy2jx7fer2oCErJLBPlTTWh_E7UpyGf1cg.-mKQRyyDUzyHWGrRziXyi7Ptosd-kBqWhJTqt7sbNFQg.JPEG.occidere/%25EB%258B%25A8%25EB%25B0%25A9%25ED%2596%25A5%25EB%25AC%25B4%25EB%25B0%25A9%25ED%2596%25A5.JPG?type=w800'>

## 그래프의 표현

그래프를 표현하는 방식은 크게 인접 행렬 그래프와 인접 리스트 그래프의 두가지로 나눌 수 있다.

일반적으로는 인접행렬 방식을 많이 사용하며, 경우에 따라 인접리스트 방식을 사용한다.

### 1. 인접 행렬 그래프 - "모든 정보를 저장"

- 장점: 직관적이며 쉽게 구현 가능.

- 단점: 불필요한 정보의 저장이 많으며, 그래프의 크기가 커지면 메모리 초과가 발생 가능.

- 구현: int형의 2차원 배열을 주로 이용하며, 이동할 수 있으면 1, 없으면 0으로 표기.

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfMTAy/MDAxNDg1ODQzNTU5NTYw.emxOr6a5-YI-IqPFG4pMWFzylg-Y3aFc0gvD2bdxvXIg.HiAfnWGkn_4jH5d5O2MpKeGbU5_FNJr6lLebEdRTYS4g.JPEG.occidere/image_5867957401485829917305.jpg?type=w800'>

### 2. 인접 리스트 그래프 - "갈 수 있는 곳만 저장"

- 장점: 필요한 정보만 저장하여 메모리 절약 가능.

- 단점: 인접행렬에 비해 다소 어려움.

- 구현: 리스트(List)나 벡터(Vector)등의 자료구조를 이용하여 각 정점에서 이동가능한 정점들을 저장. (List나 Vector를 이용한 2차원 배열)

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfMjM5/MDAxNDg1ODQzNTY5MzAx.LuvDUrY0ZNJDyT7sXSPtdvprIUxN5uRE8YJGbkPvmfcg.b6z71d7VkH75ByBGfXzJa_EfUAagKh1WwObjP9mJpU4g.JPEG.occidere/%25EC%259D%25B8%25EC%25A0%2591%25EB%25A6%25AC%25EC%258A%25A4%25ED%258A%25B8%25EB%258B%25A8%25EB%25B0%25A9%25ED%2596%25A5.JPG?type=w800'>

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfMjkx/MDAxNDg1ODQzNTc5OTc5.SxJSDnBn9eS-q2T6IvifbmHaUjG84zKbhPnFszDoOKQg.abtanX15WZje27L_dNJyb8e8Lqlevd8YaDJ2DmsnCNYg.JPEG.occidere/image_1713515921485831634971.jpg?type=w800'>

## 그래프의 탐색

### 1. 그래프의 탐색 기법

그래프의 탐색 기법은 크게 4가지로 나눌 수 있으며 각 상황에 맞춰 사용된다.

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfODUg/MDAxNDg1ODQzNTkyNjkw.SzK-2vES5pQG8fCS9Z8_uRSEILUQmUNADX8S6RiXcwkg.o7sT5ynV52o-63JvEZEuIZlP4FUA3QDrxIjAF8s7AOgg.JPEG.occidere/%25EA%25B7%25B8%25EB%259E%2598%25ED%2594%2584%25ED%258A%25B9%25EC%25A7%2595%25ED%2591%259C.JPG?type=w800'>

### 1-1. BFS 탐색

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfMjE5/MDAxNDg1ODQzNjA4NjQ0.Tqo7QQTpiMyBS3U8Xx9VbtilM4SnQ45IEoklfur5594g.wScSyqd47Ope8HhNIwDcEMsJckusYZQ3h9tfFQY-6CAg.JPEG.occidere/image_3850977491485838880343.jpg?type=w800'>

BFS(Breadth First Search; 너비 우선 탐색)는 현재 정점과 연결된 정점들에 대해 우선적으로 넓게 탐색하는 방식이다.

큐(Queue)를 이용해서 구현하며, 아래로 깊은 그래프에 대해선 좋은 성능을 기대할 수 있으나, 옆으로 넓은 그래프에서는 탐색시간이 오래 걸린다.

예를들어 A 정점에서 H정점을 방문하려 할 때, DFS를 사용하면 한번에 방문이 가능하나, BFS로는 8번만에 방문이 가능하다.

위의 그래프는 완전 이진 트리인데 BFS는 트리 탐색에서 Level Order와 동일하다.

### 1-2. DFS 탐색

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxODAzMDZfNjIg/MDAxNTIwMzQ0Njk5ODcw.ex7YhokiWi2ULwuN_qea6Y9wDVWFmSo2BCYJmt_BgRIg.iEKO6L7pm88QyzR1cHMUn4bDMHK7RCUGcaD_R0H2IAUg.PNG.occidere/image.png?type=w800'>

DFS(Depth First Search; 깊이 우선 탐색)는 현재 정점에서 연결된 정점을 하나 골라 파고들수 있는 최대한 깊게 파고들어가며 탐색하는 방법이다.

탐색 순서가 약간 난해하게 느껴질 수도 있는데 쉽게 생각해서 "갈 수 있는 길을 찾아 쭉 내려감 -> 더 이상 못가면 1번 되돌아 간 뒤 -> 또 갈 수 있는 길을 찾아 쭉 내려감 -> .... " 을 반복한다고 보면 된다.
이 원리를 응용한 알고리즘이 '백 트래킹(역추적)'이다.

스택(Stack)을 이용해서 구현하며, 직접 스택을 구현해도 되고, 시스템 스택(재귀 호출)을 사용할 수도 있다.

옆으로 넓은 그래프에 대해서 준수한 성능을 보이나 아래로 깊은 그래프의 경우 좋은 성능을 기대하기는 힘들다.

예를들어 C 정점을 방문하려 할 때, BFS에선 3번만에 방문할 수 있으나, DFS로는 12번만에 방문이 가능하다.
트리에서 DFS는 Inorder와 동일하다.

### 1-3. 다익스트라

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfMTcy/MDAxNDg1ODQzNjMzMTA5.vNinscdDoQT4sANCCH_Q3PrT3UMwSYjAum9ck0e1Iv0g.bSmfZRMhbgYCotbhD8ZnGv-pzpJUHyJN6yPjlLje3IMg.JPEG.occidere/image_6359776771485841053989.jpg?type=w800'>

다익스트(Dijkstra)라 알고리즘은 BFS의 응용으로 "어느 한 정점에서 모든 정점까지의 최단 경로"를 찾는데 사용되며, 매 탐색마다 해당 정점까지의 가중치의 합을 최소값으로 갱신시켜나가는 방식이다.

일반적으로 큐 대신 최소 힙(PriorityQueue; 우선순위 큐)을 사용하여 시간을 단축시킨다.

일반 큐를 이용하면 O(V^2)의 시간이 소요되는 반면, 최소 힙을 사용하면 O(E+Vlog⁡V)의 시간 안으로 끝낼 수 있다. (일반적으로 거의 모든 경우에 최소 힙을 사용한다.)

단, 음이 아닌 가중치에 대해서만 사용이 가능하다는 점에 유의해야 한다.

### 1-4. 플로이드 와샬

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfMjIw/MDAxNDg1ODQzNjQzNjM2.BMVGdp_1YhX6iwcfV-xZ9RAKPr1na8ygULvdhqGgSrQg.prrxd4BxgQmWR_tHTmvkeQQqcVU-oRxkOd6ajCRH614g.JPEG.occidere/image_6323615901485841577936.jpg?type=w800'>

다익스트라가 특정 정점에서 각 정점까지의 최단거리를 구하는 알고리즘이였다면, 플로이드 와샬(Floyd Washall)알고리즘은 "모든 정점에서 각 정점까지의 최단거리"를 구하는 알고리즘이다.

3중 For문을 이용하여 각 정점마다 다른 정점까지의 최단 거리를 모든 정점에 대해 구하기 때문에, 모든 정점들의 최단거리를 모두 파악할 수 있지만 O(V^3)의 시간이 걸린다.

그러나 양과 음의 모든 가중치에 대해 계산이 가능하고, 4줄밖에 안되는 코드라는 단순함 때문에 자주 이용된다.

## 2. 그래프의 탐색 유형

그래프의 탐색 유형은 크게 미로 탐색 유형과 정점 이동 유형의 2가지로 나눌 수 있다.

<img src = 'https://mblogthumb-phinf.pstatic.net/MjAxNzAxMzFfODEg/MDAxNDg1ODQzNjU1NDQ0.Z2GhsS5VNR8oc1BCmOwuv3GO723QVPjVWYiels4N3Csg.4WLB5Niq4o4EqFOxNzp5opccFlOG4nIIRP-babdFFeIg.JPEG.occidere/%25EA%25B7%25B8%25EB%259E%2598%25ED%2594%2584%25EC%259C%25A0%25ED%2598%2595.JPG?type=w800'>

미로 탐색 유형은 주로 현재 좌표에서 상, 하, 좌, 우 로 이동(x, y 값을 가감)하면서 길을 찾아나가는 방식이다.
<br/>
주로 인접행렬 형태로 그래프가 주어지며, 해당 행렬을 가지고 우측과 같은 그래프를 그릴 수 없는 경우가 대부분이다.
<br/>
행렬을 그래프 표기로 이해하려기 보다는 지도나 그림 자체로 바라보는 것이 편하다.

반면 정점 탐색 유형은 현재 정점에서 인접 정점으로 갈 수 있는지에 대한 정보가 주어지고, 해당 정보를 바탕으로 인접 행렬(또는 리스트)을 생성해서 연결된 길을 찾아 탐색해나가는 방식이다.
<br/>
특정 정점을 방문했는지 여부를 boolean 배열을 이용하여 체크해 나가는 방식으로 주로 탐색한다.

## 참고

https://www.leafcats.com/77

https://m.blog.naver.com/occidere/220923695595
