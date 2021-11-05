# 开始刷题

## 题目简介

【Day 52 】2021-10-31 - Shortest-Cycle-Containing-Target-Node
-------------------


### 题目思路

+ BFS


## 题目代码
### 代码块
``` python
class Solution:
    def solve(self, graph, target):
        q = collections.deque([target])
        visited = set()
        steps = 0
        while q:
            for i in range(len(q)):
                cur = q.popleft()
                visited.add(cur)
                for neighbor in graph[cur]:
                    if neighbor not in visited:
                        q.append(neighbor)
                    elif neighbor == target:
                        return steps + 1
            steps += 1
        return -1

```
### 复杂度
+ 时间复杂度  O(v+e)
+ 空间复杂度 O(v)


