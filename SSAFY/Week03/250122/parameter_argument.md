# Parameter vs Argument

## 정의
> Parameter(매개변수): 함수 정의할 때, 함수가 받을 값
> Argument(인자): 함수 호출할 때, 실제로 전달되는 값

```python
def add_numbers(x, y):  # x와 y는 parameter
    result = x + y
    return result

a = 2
b = 3
sum_result = add_numbers(a, b)  # a와 b는 argument
print(sum_result)
```

## Arbitrary Argument Lists
- 정해지지 않은 개수의 arguments를 처리하는 argument
- parameter 앞에 '*'를 붙여 사용
- 여러 개의 arguments를 tuple로 처리
```python
def calculate_sum(*args):
    print(args) # (1, 100, 5000, 30)
    print(type(args)) # <class 'tuple'>

calculate_sum(1, 100, 5000, 30)
```

>[!WARNING]
> 항상 *는 tuple로 묶는 것이 아니다!
> \* 는 남는 값을 묶을 때 항상 **컨테이너 타입**에 맞춰 값을 묷는다.
> - 함수 정의에서는 *args 를 tuple로 묶음
> - for 루프에서는 *var를 **list**로 묶음음


## Arbitrary Keyword Argument Lists
- 정해지지 않은 개수의 keyword arguments를 처리하는 argument
- 함수 정의 시 parameter 앞에 '**'를 붙여 사용
- 여러 개의 arguments를 dictionary로 묶어 처리
```python
def print_info(**kwargs):
    print(kwargs)

print_info(name='Eve', age=30)  # {'name': 'Eve', 'age': 30}
```

## Parameter 배치 순서(option)
```python
def func(pos1, pos2, default_arg='default', *args, **kwargs):
    print('pos1: ', pos1)
    print('pos2: ', pos2)
    print('default_arg: ', default_arg)
    print('args: ', args)
    print('kwargs: ', kwargs)

func(1, 2, 3, 4, 5, 6, key1='value1', key2='value2')

# pos1: 1
# pos2: 2
# default_arg: 3
# args: (4, 5, 6)
# kwargs: {'key1': 'value1', 'key2': 'value2'}
```