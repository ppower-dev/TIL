# 메서드
클래스 내부에 정의되는 함수.
 >[!IMPORTANT]
 메서드는 어딘가(클래스)에 속해 있는 함수이며, 각 데이터 타입별로 다양한 기능을 가진 메서드가 존재

 ```python
def add(x, y):
  return x + y

class Calculator:
  def add(self, a, b):
    return a + b

# 함수 호출
add(1, 2)

# 메서드 호출
a.add(x, y)

# 예를 들어 append는 list class의 method
 ```

 ## 문자열 메서드
 ### 조회/탐색 및 검증 메서드드
 | 메서드 | 설명 |
|:---------:|:------------|
| s.find(x)       | x의 첫 번째 위치를 반환. 없으면 -1을 반환.         |
| s.index(x)       | x의 첫 번째 위치를 반환. 없으면 오류 발생.         |
| s.isupper() | 문자열 내의 모든 문자가 대문자인지 확인 |
| s.islower() | 문자열 내의 모든 문자가 소문자인이 확인 |
|s.isalpha() | 문자열 내의 모든 문자가 알파벳인지 확인(한글 포함) |

```python
print('banana'.find('a')) # 1
print('banana'.find('z')) # -1

print('banana'.index('a'))  # 1
print('banana'.index('z'))  # ValueError: substring not found

string1 = 'HELLO'
string2 = 'Hello'
print(string1.isupper())  # True
print(string2.isupper())  # False
print(string1.islower())  # False
print(string1.islower())  # False

string1 = 'Hello'
string2 = '123heis98576ssh'
print(string1.isalpha())  # True
print(string2.isalpha())  # False
```

### 조작 메서드(새 문자열 반환)
문자열은 불변 타입. 문자열 조작 메서드는 원본을 수정하는 것이 아니라 사본을 반환하는 메서드.
| 메서드 | 설명 |
|:-----:|:------|
| s.replace(old, new[, count]) | 바꿀 대상 글자르 새로운 글자로 바꿔서 반환 |
|s.strip([chars]) | 공백이나 특정 문자를 제거 |
|s.split(sep=None, maxsplit=-1) | sep를 구분자 문자열로 사용하여 문자열에 있는 단어들의 리스트를 반환 |
| 'seperator'.join(iterable) | 구분자로 iterable의 문자열을 연결한 문자열을 반환 |
| s.capitalize() | 가장 첫 번째 글자를 대문자로 변경 |
| s.title() | 문자열 내 띄어쓰기 기준으로 각 단어의 첫 글자는 대문자로, 나머지는 소문자로 반환 |
| s.upper() | 모두 대문자로 변경 |
| s.lower() | 모두 소문자로 변경 |
| s.swapcase() | 대 <-> 소문자 서로 변경 |

```python
text = 'Hello, world! world world'
new_text1 = text.replace('world', 'Python')
new_text2 = text.replace('world', 'Python', 1)
print(new_text1)  # Hello, Python! Python Python
print(new_text1)  # Hello, Python! world world

text = '      Hello, world!   '
new_text = text.strip()
print(new_text) # 'Helo, world!'

text = 'Hello, world!'
words1 = text.split(',')
words2 = text.split()
print(words1) # ['Hello', ' world!']
print(words2) # ['Hello,', 'world!']

words = ['Hello', 'world!']
text = '-'.join(words)
```

## 리스트
### 값 추가 및 삭제 메서드
| 메서드 | 설명 |
|:-----:|:-----|
| L.extend(m) | Iterable m의 모든 항목들을 리스트 끝에 추가 |
| L.insert(i, x) | 리스트 인덱스 i에 항목 x를 삽입 |
| L.clear() | 리스트의 모든 항목 삭제 |

```python
my_list = [1, 2, 3]
my_list.extend([4, 5, 6])
print(my_list)  # [1, 2, 3, 4, 5, 6]

my_list = [1, 2, 3]
my_list.insert(1, 5)
print(my_list)  # [1, 5, 2, 3]
```

### 탐색 및 정렬 메서드
| 문법 | 설명 |
|:----:|:-----|
| L.index(x) | 리스트에서 첫 번째로 일치하는 항목 x의 인덱스를 반환 |
| L.count(x) | 리스트에서 항목 x의 개수를 반환 |

```python
my_list = [1, 2, 3]
index = my_list = my_list.index(2)
print(index)  # 1

my_list = [1, 2, 2, 3, 3, 3]
count = my_list.count(3)
print(count)
```