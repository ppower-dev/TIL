# Packing & Unpacking
## Packing
### Tuple 처리
- 한 변수에 콤마(,)로 구분된 값을 넣으면 자동으로 tuple로 처리
```python
packed_values = 1, 2, 3, 4, 5
print(packed_values)  # (1, 2, 3, 4, 5)
```
### '*'을 활용한 리스트 패킹
- \* 를 사용하면 "나머지 모든 값"을 리스트로 묶어서 받을 수 있음
```python
numbers = [1, 2, 3, 4, 5]
a, *b, c = numbers

print(a)  # 1
print(b)  # [2, 3, 4]
print(c)  # 5
```

### '*'을 활용한 (함수 parameter 작성 시) 튜플 패킹
- \* 을 사용하면 여러 개의 arguments를 튜플로 묶을 수 있음
```python
def my_func(*args):
  print(args) # (1, 2, 3, 4, 5)
  print(type(args)) # <class 'tuple'>

my_func(1, 2, 3, 4, 5)
```
## Unpacking
```python
packed_values = 1, 2, 3, 4, 5
a, b, c, d, e = packed_values

print(a, b, c, d, e)  # 1 2 3 4 5
```
### * 을 활용한 unpacking
- 시퀀스(리스트, 튜플)를 함수에 전달할 때, 각 요소를 "풀어서" 개별 인자로 넘기기 가능
```python
def my_function(x, y, z):
  print(x, y, z)

names = ['alice', 'jane', 'peter']
my_function(*names) # alice jane peter
```
### ** 을 활용한 unpacking
- 딕셔너리 키-값 쌍을 분리해 전달
```python
def my_function(x, y, z):
  print(x, y, z)

my_dict = {'x' : 1, 'y' : 2, 'z' : 3}
my_function(**my_dict)  # 1 2 3