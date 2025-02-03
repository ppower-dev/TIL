클래스는 데이터와 기능을 하나의 틀로 묶어 관리하는 방법이다. 사용자 저으이 객체를 만드는 수단이자 속성과 메서드를 정의한다.

## 📌 클래스 정의
- 클래스 이름은 파스칼 케이스 방식으로 작성하는 편
```python
class MyClass:
  pass
```
- \_\_init\_\_ 메서드는 '생성자 메서드'로 불리며, **새로운 객체를 만들 때** 필요한 초기값을 설정
```python
class Person:
  def __init__(self, name, age):
    self.name = name  # 인스턴스 속성
    self.age = age  # 인스턴스 속성

  def introduce(self):
    print(f'안녕하세요. 저는 {self.name}, 나이는 {self.age}살입니다.')
```

## 📌 인스턴스
- 클래스를 통해 생성된 객체
- 클래스가 설계도라면, 인스턴스는 그 설계도로부터 실제로 만든 '개별 물건'
- 기수가 클래스라면,
  - 아이유는 객체다.(O)
  - 아이유는 인스턴스다.(X)
  - 아이유는 가수의 인스턴스다.(O)
```python
name = 'Alice'
print(type(name))  # <class 'str'>

# 변수 name의 타입은 str 클래스다.
# 변수 name은 str 클래스의 인스턴스다.
# 우리가 사용해왔던 데이터 타입은 사실 모두 클래스였다!
```

## 📌 클래스 변수와 인스턴스 변수
- 클래스 변수와 동일한 이름으로 인스턴스 변수 생성 시 클래스 변수가 아닌 인스턴스 변수에 먼저 참조하게 됨
```python
class Circle:
  pi = 3.14

  def __init__(self, radius):
    self.radius = radius

c1 = Circle(5)
c2 = Circle(10)
print(c1.radius)  # 5
print(c2.radius)  # 10

# c1의 인스턴스 변수 pi를 생성
c1.pi = 100

print(c1.pi)  # 100
print(Circle.pi)  # 3.14

# c2는 인스턴스 변수 pi가 없으므로 클래스 변수 pi를 참조
print(c2.pi)  # 3.14
```

## 📌 인스턴스 메서드
- 클래스로부터 생성된 각 인스턴스에서 호출할 수 있는 메서드
- 클래스가 아니라 인스턴스의 상태를 조작하거나 동작을 수행
- 반드시 첫 번째 인자로 **인스턴스 자신(self)**을 받음
```python
class MyClass:
  def instance_method(self, arg1, arg2)
    pass
```

## 📌 생성자 메서드
- 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
- 인스턴스 변수들의 초기값을 설정
```python
class Person:
  def __init__(self, name):
    self.name = name
    print('인스턴스가 생성되었습니다.')

  def greeting(self):
    print(f'안녕하세요 {self.name}입니다.')

person1 = Person('지민')  # 인스턴스가 생성되었습니다.
person1.greeting()  # 안녕하세요. 지민입니다.
```

## 📌 클래스 메서드
- 클래스가 호출하는 메서드
- 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행
- @classmethod 데코레이터를 사용하의 정의
- 호출 시, 첫번재 인자로 해당 메서드를 호출하는 클래스가 전달됨
- 클래스를 인자로 받아 클래스 속성을 변경하거나 읽는 데 사용
```python
class MyClass:

  @classmethod
  def class_method(cls, arg1, arg2):
    pass
```
```python
class Person:
  population = 0
  def __init__(self, name):
    self.name = name
    Person.increase_population()
  
  @classmethod
  def increase_population(cls):
    cls.population += 1
  
  person1 = Person('Alice')
  person2 = Person('Bella')
  print(Person.population)  # 2
```

## 📌 스태틱 메서드
- 클래스, 인스턴스와 상관없이 독립적으로 동작하는 메서드
- @staticmethod 데코레이터를 사용하여 정의
- 호출 시 자동으로 전달 받는 인자가 없음
- 인스턴스나 클래스 속성에 직접 접근하지 않는, '도우미 함수'와 비슷한 역할
```python
class MyClass:

  @staticmethod
  def static_method(arg1, ...):
    pass
```
```python
class MathUtils:
  @staticmethod
  def add(a, b):
    return (a + b)
```

print(MathUtils.add(3, 5))  # 8

## 📌 활용
```python
class BankAccount:
  interest_rate = 0.02  # 이자율

  def __init__(self, owner, balance=0):
    self.owner = owner
    self.balance = balance
  
  def deposit(self, amount):
    self.balance += amount
  
  def withdraw(self, amount):
    if self.balance >= amount:
      self.balance -= amount
    else:
      print('잔액 부족!')
  
  # 이자율 설정
  @classmethod
  def set_interest_rate(cls, rate):
    cls.interest_rate = rate
  
  # 금액이 양수인지 검증
  @staticmethod
  def is_positive(amount):
    return amount > 0

# 계좌 개설(인스턴스 생성)
alice_acc = BankAccount('Alice', 1000)

# 입금 및 출금(인스턴스 메서드 호출)
alice_acc.deposit(500)
alice_acc.withdraw(200)

# 잔액 확인(인스턴스 변수 참조)
print(alice_acc.balance)  # 1300

# 이자율 변경(클래스 메서드 호출)
BankAccount.set_interest_rate(0.03)
print(BankAccount.interest_rate)  # 0.03

# 잔액이 양수인지 확인(정적 메서드 호출)
print(BankAccount.is_positive(alice_acc.balance))  # True
```