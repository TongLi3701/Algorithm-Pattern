# Python Skills

## Python List
```Python
t = [[]] * 10
print(t)
t[0].append(1)
print(t[0])
print(t[1])

输出为: 
[[], [], [], [], [], [], [], [], [], []]
[1]
[1]

所以当用这种方式来初始化的时候, t[0] 和 t[1] 共享同样的空间

正确方式
t = [[] for x in range(10)]
以及
dp = [[0] * N for i in range(M)] ok 
但是
dp = [[0] * N ] * M 就不 ok
```

## Dict
```python
a = dict()
for key, val in a.items():
	then we can iterate keys and values

# How to sort dictionary by value
dict(sorted(a.items(), key = lambda x: x[1], reverse = True))
```

## Str and ASCII
*  `Str` to `ASCII`: `ord`
*  `ASCII` to `Str`: `chr`

