# Disjoint Set

并查集只是记录了节点之间的联通关系, 而节点相互联通只需要一个共同的祖先就可以

```python
# 当并查集仅仅由数来表示的时候
class UnionFind:
    def __init__(self, n) -> None:
        self.parent = list(range(n))
    
    def find(self, idx):
        if idx == self.parent[idx]:
            return idx
        
        return self.find(self.parent[idx])
    
    def union(self, idx1, idx2):
        self.parent[self.find(idx1)] = self.find(idx2)
```


```python
# 并查集也可以改为一个dict, 用father来表示
class UnionFind:
    def __init__(self, n) -> None:
        self.parent = list(range(n))
        self.weight =  [1.0] * n
    
    def find(self, x):
        if x != self.parent[x]: # 如果要查找的元素不等于本身, 那么就代表它有parent
            origin = self.parent[x]
            self.parent[x] = self.find(self.parent[x])
            self.weight[x] *= self.weight[origin]
        
        return self.parent[x]
    
    def union(self, x, y, value):
        root_x = self.find(x)
        root_y = self.find(y)

        if root_x != root_y:
            self.parent[root_x] = root_y
            self.weight[root_x] = value * self.weight[y] / self.weight[x]
    
    def query(self, x, y):
        root_x = self.find(x)
        root_y = self.find(y)

        if root_x == root_y:
            return self.weight[x] / self.weight[y]
        else:
            return -1.0
```