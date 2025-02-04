## 📌 다중 상속
- 둘 이상의 상위 클래스로부터 여러 행동이나 특징을 상속받을 수 있는 것
- 상속받은 모든 클래스의 요소를 활용 가능
- 중복된 속성이나 메서드가 있는 경우 **상속 순서에 의해 결정**됨
```python
class Person:
  def __init__(self, name):
    self.name = name
  
  def greeting(self):
    return f'안녕, {self.name}'

class Mom(Person):
  gene = 'XX'

  def swim(self):
    return '엄마가 수영'

class Dad(Person):
  gene = 'XY'

  def walk(self):
    return '아빠가 걷기'

class FirstChild(Dad, Mom):
  def swim(self):
    return '첫째가 수영'
  
  def cry(self):
    return '첫째가 응애'

baby1 = FirstChild('아가')
print(baby1.cry())  # 첫째가 응애
print(baby1.swim())  # 첫째가 수영
print(baby1.walk())  # 아빠가 걷기
print(baby1.gene)  # XY
```
### MRO
- MRO(Method Resolution Order) 알고리즘을 사용하여 클래스 목록을 생성
- 부모 클래스로부터 상속된 속성들의 검색을 깊이 우선으로, 왼쪽에서 오른쪽으로, 계층 구조에서 겹치는 같은 클래스를 두 번 검색하지 않음
```python
class D(B, C):
  pass
```
- 그래서, 속성이 D에서 발견되지 않으면, B에서 찾고, 거기에서도 발견되지 않으면, C에서 찾고, 이런식으로 진행됨

### super()
- 다중 상속 상황에서 여러 부모 클래스를 가진 자식 클래스에서 다음에 호출해야 할 부모 메서드를 순서대로 호출할 수 있게 함
아래의 코드를 보고 super()의 동작 방식에 대해 생각해보자.
```python
class ParentA:
  def __init__(self):
    """
    먄약 super.__init__() 을 넣는다면?
    ParentA의 부모 클래스는 없는데?
    아래에 Child 클래스가 존재하고, 거기서 MRO 상 Child -> ParentA -> ParentB 라서 ParentB의 __init__이 호출
    즉, super()는 단순히 "직계 부모 클래스를 가리킨다"가 아니라
    "MRO 순서상 다음 클래스를 기리킨다"가 맞는 말말
    """
    self.value_a = 'ParentA'

  def show_value(self):
    print(f'Value from ParentA: {self.value_a}')

class ParentB:
  def __init__(self):
    self.value_b = 'ParentB'
  
  def show_value(self):
    print(f'Value from ParentB: {self.value_b}')

class Child(ParentA, ParentB):
  def __init__(self):
    super().__init__()  # ParentA 클래스의 __init__ 메서드 호출
    """
    ParentB 클래스의 __init__ 메서드를 호출하고 싶다면
    ParentB.__init__(self) 로 대체하면 됨
    """
    self.value_c = 'Child'
  
  def show_value(self):
    super().show_value()  # ParentA 클래스의 show_value 메서드 호출
    print(f'Value from Child: {self.value_c}')
```
1. super().__init__ 가 동작하는 방식
super() 는 단순히 **직계 부모 클래스의 메서드를 호출하는 것이 아니라, MRO 순서에 따라 다음 클래스를 호출**한다는 점이 중요하다.
```python
class ParentA:
  def __init__(self):
    super().__init__()  # ParentA의 부모 클래스의 __init__()을 호출하려고 함
    self.value_a = 'ParentA'
```
여기서 super().__init__() 을 넣으면 **ParentA의 부모 클래스(즉, object 클래스)가 아니라, MRO 상에서 ParentA 다음에 오는 클래스를 호출**하게 된다.
2. super().__init__()가 MRO 순서에 따라 작동하는 이유
```python
class Child(ParentA, ParentB):
  def __init__(self):
    super().__init__()  # ParentA.__init__()을 호출
```
- super().__init__() 은 MRO 순서에서 **Child 다음 클래스인 ParentA**의 __init__()을 호출한다.
- 그런데 ParentA의 __init__() 내부에서 다시 super().__init__() 을 호출하면?
  - MRO 순서에서 ParentA 다음 클래스인 **ParentB의 __init__() 을 호출**한다.
즉, super()는 단순히 "직계 부모 클래스"가 아니라 **MRO 순서에서 다음 클래스를 가리킨다**는 게 정확한 개념이다.