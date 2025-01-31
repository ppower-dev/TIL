# 관통 프로젝트
---
- 관통 프로젝트는 조미료와 같은 역할
- 하루만에 끝내는 것이 아니라 빌드업하는 방식
- 중간의 어느 시점까지는 개인 pjt이며, 주제 변경도 가능
- **하지만 어느 시점부터는 변경 불가능이며 그룹 pjt**

## 버전 선택
1. 금융 상품 비교 앱
   - since 10기
2. 영화 추천 서비스
   - 자료가 널림
3. 도서 정보 검색 서비스
   - since 13기
   - 도서 정보를 검색하고 요약하여 짧은 오디오 북으로 제작
   - 마일리지 충전과 사용을 통한 도서 구매 및 대여 시스템 구현

## 서버에 정보를 달라는 파이썬 코드
```python
import requests
import pprint

print = pprint.pprint

# 하드 코딩하는 변수는 대문자로 작성하는 편
URL = 'https://fakestoreapi.com/carts'
# .get(URL) : URL에 GET 요청을 보내는 메서드
data = requests.get(URL)
print(data)
# 출력결과: <Response [200]>
# [200]: 웹의 응답 코드 -> 정상적으로 응답했다는 의미
# [404]: 웹의 응답 코드 -> 알 수 없는 주소로 요청했다는 의미

# .json() : 데이터를 JSON 형식으로 변환하는 메서드
json_data = data.json()
print(json_data)
```

# 날씨 데이터 수집
---
## API가 사용하는 데이터 형식: JSON
- JavaScript Object Notation
- **경량의 텍스트 기반의 데이터 형식**

## 파이썬에서의 JSON
- 파싱
  - 데이터를 의미 있는 구조로 분석하고 해석하는 과정
- json.loads()
  - JSON 형식의 문자열을 파싱하여 python dictionary 로 변환

## OpenWeatherMap API 실습
```python
import requests
import pprint
print = pprint.pprint

# 서울의 위도
lat = 37.56
# 서울의 경도
lon = 126.97

API_KEY = '여기에 본인의 api key를 입력하면 됨'
URL = f'https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={API_KEY}'

data = requests.get(URL).json()
print(data)
# 이 데이터를 요리조리 잘 조리해보자
```

# 데이터 사이언스
---
- **다양한 데이터로부터 새로운 지식과 정보룰 추출**하기 위해 과학적 방법론, 프로세스, 알고리즘, 시스템을 동원하는 융합 분야

## 필요한 정보를 추출하는 5가지 단계
1. 문제 정의
2. 데이터 수집
3. 데이터 전처리(정제)
4. 데이터 분석
5. 결과 해석 및 공유

