# map & zip
## map
> map(function, iterable)
> Iterable의 모든 요소에 함수를 적용하고, 그 결과를 map object로 반환

```python
numbers = [1, 2, 3]
result = map(str, numbers)

print(result) # <map object at 0x00000239C915D760>
print(list(result)) # ['1', '2', '3']
```
## zip
> zip(*iterables)
> 임의의 iterable을 모아 tuple을 원소로 하는 zip object 반환
```python
girls = ['jane', 'ashley']
boys = ['peter', 'jay']
pair = zip(girsl, boys)

print(pair) # <zip object at 0x000001C76DE68700>
print(list(pair)) # [('jane', 'peter'), ('ashley', 'jay')]
```
```python
scores = [
  [10, 20, 30],
  [40, 50, 39],
  [20, 40, 50]
]

for score in zip(*scores):
  print(score)
# (10, 40, 20)
# (20, 50, 40)
# (30, 39, 50)

# *은 iterable을 풀어서 개별 요소로 전달한다!
# *scores = [10, 20, 30], [40, 50, 39], [20, 40, 50]
# list(zip(*scores)) = [(10, 40, 20), (40, 50, 39), (20, 40, 50)]
```
```python
scores = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90],
]

for i, *score in zip(range(1, 4), *scores):
    print(f'{i}: {score}')


# zip((1, 2, 3), [10, 20, 30], [40, 50, 60], [70, 80, 90])
# 1, 10, 40, 70
# 2, 20, 50, 80
# 3, 30, 60, 90
```