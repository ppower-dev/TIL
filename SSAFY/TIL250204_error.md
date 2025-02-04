## 📌 try-except 구문
```python
try:
  x = int(input('숫자를 입력하세요:'))
  y = 10 / x
except ZeroDivisionError:
  print('0으로 나눌 수 업습니다.')
except ValueError:
  print('유효한 숫자가 아닙니다.')
else:
  print(f'결과: {y}')
finally:
  print('프로그램이 종료되었습니다.')
```
- 예외가 발생하면 프로그램 흐름은 try 블록을 빠져나와 해당 예외에 대응하는 except 블록으로 이동
  
## 📌 예외 처리 주의사항
### 내장 예외의 상속 계층구조 주의
- 아래와 같이 예외를 작성하면 코드는 2번째 except 절에 이후로 도달하지 못함
```python
try:
  num = int(input('100으로 나눌 값을 입력하시오 : '))
  print(100 / num)
except BaseException:
  print('숫자를 넣어주세요.')
# 이 이후의 절절에 도달하지 못함
except ZeroDivisionError:
  print('0으로 나눌 수 없습니다.')
except:
  print('에러가 발생하였습니다.')
```
- 내장 예외 클래스는 상속 계층구조를 가지기 때문에 except 절로 분기 시 **반드시 하위 클래스를 먼저 확인 할 수 있도록 작성**해야 함함
```python
try:
  num = int(input('100으로 나눌 값을 입력하시오 : '))
  print(100 / num)
except BaseException:
  print('숫자를 넣어주세요.')
except:
  print('에러가 발생하였습니다.')
except ZeroDivisionError:
  print('0으로 나눌 수 없습니다.')
```
- 공식 문서로 순서 확인 가능