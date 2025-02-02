Python에서 .env 파일은 **환경 변수(environment variables)** 를 저장하는 용도로 사용된다. 주로 API 키, 데이터베이스 접속 정보, 비밀번호 등 민감한 정보를 코드에서 직접 하드코딩하는 대신 .env 파일에 저장하여 관리하는 데 활용된다.

## 📌 .env 파일이란?
- 환경 변수(key-value 형태)
- 코드와 분리하여 **보안성을 높이고**, 환경에 따라 설정을 변경하기 쉽게 만듦
- Git 등에 포함되지 않도록 **.gitignore에 추가**하는 것이 일반적

## 📌 .env 파일의 형식
.env 파일은 일반적으로 다음과 같이 작성된다.
```env
SECRET_KEY=mysecretkey123
DATABASE_URL=postgresql://user:password@localhost:5432/mydb
DEBUG=True
```
- 각 줄은 key=value 형태로 작성
- 문자열을 따옴표 없이 사용해도 되지만, 일부 경우에는 "값" 혹은 '값' 형태로 감싸는 것이 안전

## 📌 Python에서 .env 파일 불러오기
Python에서 .env 파일을 불러오려면 dotenv 라이브러리를 사용하는 것이 일반적이다.
1. Python-dotenv 라이브러리 설치
```bash
pip install python-dotenv
```
2. .env 파일 로드
```python
import os
from dotenv import load_dotenv

# .env 파일 로드
load_dotenv()

# 환경 변수 가져오기
SECRET_KEY = os.getenv("SECRET_KEY")
DATABASE_URL = os.getenv("DATABASE_URL")
DEBUG = os.getenv("DEBUG")

# 값 출력
print("SECRET_KEY:", SECRET_KEY)
print("DATABASE_URL:", DATABASE_URL)
print("DEBUG:", DEBUG)  # True 가 아니라 "True" string이 반환됨
```
.env 에서 가져오는 모든 값은 **문자열(str)** 로 반환된다. 따라서, 필요한 경우 적절한 타입으로 변환해야 한다.

## 📌 .gitignore에 .env 추가하기
- .env 파일은 **비공개 정보**를 포함하므로 **GitHub에 업로드되지 않도록 해야한다.**
- .gitignore 파일에 다음 내용을 추가하면 .env 파일이 Git에서 무시된다.
```gitignore
# .gitignore
.env
```

## 📌 정리
- .env 파일은 **환경 변수**를 저장하는 텍스트 파일
- python-dotenv 라이브러리로 Python에서 쉽게 불러올 수 있음
- 모든 값이 **문자열(str)** 이므로 필요하면 타입 변환해야 함
- Git 저장소에 포함되지 않도록 **.gitignore에 추가**하는 것이 중요