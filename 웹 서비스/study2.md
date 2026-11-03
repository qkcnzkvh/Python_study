HTML
HTML이란?
HyperText Markup Language
- 웹 페이지의 구조를 정의하는 마크업 언어
- 서버가 HTML 문서를 생성하여 브라우저에 전달
- 브라우저가 HTML을 해석하여 화면에 표시
HTML 기본 구조
- 태그(Tag)의 조합으로 구성
- <태그이름> 형태로 작성
- 대부분 시작 태그와 종료 태그로 구성
<!DOCTYPE html>
<html>
<head>
    <title>내 페이지</title>
</head>
<body>
    <h1>제목</h1>
    <p>내용</p>
</body>
</html>


- <!DOCTYPE html>: HTML5 문서임을 선언
- <html>: HTML 문서의 최상위 요소
- <head>: 웹 페이지의 설정 및 메타 정보
- <body>: 실제 브라우저에 표시되는 내용
참고 명령어

- ! + Enter 또는 Tab: HTML 기본 구조 자동 생성 (VS Code Emmet)
HTML 주석
<!-- 주석 내용 -->


기본 태그
태그	역할
<p>	문단 생성
<hr>	가로 구분선 생성
<br>	줄바꿈
<ul>	순서 없는 목록
<ol>	순서 있는 목록
<li>	목록 항목
<input>	사용자 입력 영역
<img>	이미지 표시
<head>	문서 설정 및 정보
<body>	실제 화면에 표시되는 내용

목록 태그
순서 없는 목록 (Unordered List)
<ul>
    <li>사과</li>
    <li>바나나</li>
</ul>


- 일반적으로 ● 형태로 표시

순서 있는 목록 (Ordered List)
<ol type="1">
    <li>사과</li>
    <li>바나나</li>
</ol>


- 숫자, 로마자 등으로 순서를 표시
- type 속성으로 표시 형식 지정
이미지 태그
<img src="cat.jpg" alt="고양이">


- src: 이미지의 출처 또는 파일 주소
- alt: 이미지가 표시되지 않을 때 대체할 텍스트
id와 class
- id: 특정 HTML 요소를 식별하는 고유한 이름 (한 문서 내에서 중복 사용하지 않는 것이 원칙)
- class: 여러 HTML 요소를 하나의 그룹으로 묶을 때 사용
Form 태그
- 사용자가 입력한 데이터를 서버로 전달하기 위한 태그
<form action="/submit" method="post">
    <label for="email">이메일</label>

    <input
        id="email"
        name="email"
        type="email"
        placeholder="이메일을 입력하세요"
    >

    <button type="submit">접속</button>
</form>


주요 속성
속성	역할
action	데이터를 보낼 서버 주소
method	데이터를 전달하는 HTTP 메서드
id	입력 요소의 고유 식별자
for	label과 연결할 input의 id
name	서버에 전달할 데이터의 이름
placeholder	입력 전에 보여주는 안내 문구
type	입력 데이터의 종류

Semantic HTML
HTML 요소의 의미에 맞는 태그를 사용하는 방식

일반적인 영역 구분
<body>
    <div></div>
    <div></div>
    <div></div>
</body>


시맨틱 태그 사용
<body>
    <header></header>
    <main></main>
    <footer></footer>
</body>


주요 시맨틱 태그
- <header>: 페이지 또는 영역의 머리말
- <main>: 주요 콘텐츠
- <footer>: 페이지 또는 영역의 하단 정보
- <nav>: 내비게이션 영역
- <section>: 주제별 콘텐츠 영역
- <article>: 독립적으로 구분할 수 있는 콘텐츠
Table 태그
- 표 형태의 데이터를 표시할 때 사용
<table>
    <thead>
        <tr>
            <th>ID</th>
            <th>이름</th>
            <th>이메일</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>1</td>
            <td>Alex</td>
            <td>alex@example.com</td>
        </tr>

        <tr>
            <td>2</td>
            <td>Bob</td>
            <td>bob@example.com</td>
        </tr>

        <tr>
            <td>3</td>
            <td>Chris</td>
            <td>chris@example.com</td>
        </tr>
    </tbody>
</table>


- <table>: 표 전체
- <thead>: 표의 제목 영역
- <tbody>: 표의 데이터 영역
- <tr>: 행(Row)
- <th>: 제목 셀
- <td>: 일반 데이터 셀

CSS
CSS란?
Cascading Style Sheets
- HTML 요소의 모양과 배치를 정하는 스타일 언어
- 글자 크기, 색상, 간격, 정렬, 레이아웃 등을 설정
CSS의 특징
- 부모 요소의 일부 스타일 속성을 자식 요소가 상속받음
- 자식 요소에서 별도로 스타일을 지정하면 해당 설정이 우선 적용될 수 있음
- 모든 CSS 속성이 상속되는 것은 아님
CSS 적용 방법
1. Inline Style (인라인 스타일)

HTML 태그에 직접 스타일을 작성하는 방식
<p style="font-size: x-large; font-weight: bold; text-align: center;">
    김새봄
</p>


2. Internal Style (내부 스타일)

HTML 문서의 <head> 안에 <style> 태그를 작성하는 방식
<head>
    <style>
        #contents {
            text-align: center;
        }
    </style>
</head>

<body>
    <div id="contents">
        <header>김새봄</header>
    </div>
</body>


3. External Style (외부 스타일)

별도의 CSS 파일을 생성하여 HTML에 연결하는 방식
<link rel="stylesheet" href="./style.css">


CSS 선택자
선택자	의미	예시
태그명	특정 태그 선택	p
#id명	특정 ID 선택	#contents
.클래스명	특정 클래스 선택	.container

Box Model
- HTML 요소가 화면에서 차지하는 공간을 설명하는 모델
- 요소의 크기와 여백을 구성하는 개념
주요 구성 요소
1. Content: 실제 콘텐츠 영역
2. Padding: 콘텐츠와 테두리 사이의 내부 여백
3. Border: 테두리
4. Margin: 요소 바깥쪽의 외부 여백

CSS Grid
Grid란?
- 2차원 레이아웃 시스템
- 행(Row)과 열(Column)을 기준으로 화면의 요소를 배치하는 방식
- 화면 전체의 영역을 나누고 요소의 위치를 지정할 수 있음
주요 특징
- 행과 열을 동시에 관리
- 복잡한 레이아웃을 쉽게 구성
- 요소의 크기와 간격을 유연하게 조절 가능

JavaScript
JavaScript란?
- 웹 브라우저에서 동작하는 프로그래밍 언어
- 웹 페이지의 동작과 상호작용을 담당
주요 역할
- 버튼 클릭 처리
- 사용자 입력 처리
- 화면 내용 변경
- 이벤트 처리
웹 개발의 기본 구성
기술	역할
HTML	구조
CSS	디자인
JavaScript	동작

JavaScript 기본 문법
변수와 상수
let

- 값을 변경할 수 있는 변수를 선언
let name = "Alex";


const

- 재할당할 수 없는 상수를 선언
const age = 30;


출력
console.log("Hello World");


자료형 (Data Type)
1. Number (숫자형)
let number = 10;


2. String (문자열)
let name = "Alex";
let message = 'Hello';


- 큰따옴표와 작은따옴표 모두 사용 가능

3. Boolean (불리언)

- 참과 거짓을 나타내는 자료형
let isActive = true;
let isDone = false;


4. Null

- 의도적으로 값이 없음을 나타냄
let value = null;


5. Undefined

- 값이 할당되지 않은 상태
let value;


6. Object (객체)

- 여러 데이터를 하나의 구조로 묶어서 관리
let user = {
    name: "Alex",
    age: 30
};


7. Array (배열)
- 여러 데이터를 순서대로 저장하는 자료형
- 인덱스를 이용하여 데이터에 접근 가능
let numbers = [1, 2, 3, 4];

console.log(numbers[0]);


조건문
조건에 따라 서로 다른 코드를 실행하는 문법
if (조건식) {
    // 조건이 참일 때 실행
}


Truthy와 Falsy
- Truthy: Boolean으로 변환했을 때 true로 취급되는 값
- Falsy: Boolean으로 변환했을 때 false로 취급되는 값
JavaScript의 대표적인 Falsy 값 6가지
- false
- 0
- ""
- null
- undefined
- NaN
그 외 대부분의 값은 Truthy로 취급됨.
연산자
1. 산술 연산자
연산자	역할
+	덧셈
-	뺄셈
*	곱셈
/	나눗셈
%	나머지

나머지 구하기
console.log(n1 % n2);


몫 구하기
console.log(Math.floor(n1 / n2));


2. 비교 연산자
- 두 값의 크기나 관계를 비교
- 결과는 true 또는 false
3. 문자열 연결 (Concatenation)

- 문자열을 + 연산자로 연결
let first = "Hello";
let second = "World";

console.log(first + " " + second);


4. 동등 연산자
10 == "10";  // true
10 === "10"; // false


- ==: 값이 같은지 비교하며 필요하면 자료형을 변환
- ===: 값과 자료형을 모두 비교
5. 논리 연산자

| 연산자 | 의미 |
|---|---|
| && | AND (그리고) |
| || | OR (또는) |
| ! | NOT (부정) |
반복문
1. for 문

- 반복 횟수나 조건을 명확하게 지정할 때 사용
for (let num = 0; num < 10; num++) {
    console.log(num);
}


구성
for (초기값; 반복 조건; 증감식) {
    // 반복 실행할 코드
}


2. while 문

- 조건이 참인 동안 반복 실행
let n = 0;

while (n < 3) {
    console.log(n);
    n++;
}


이벤트 (Event)
- 웹 페이지에서 발생하는 모든 동작이나 상태 변화

주요 이벤트
- 사용자의 클릭
- 사용자 입력
- 스크롤
- 페이지 로드
- DOM 로드 완료
- 창 크기 변경

FastAPI
FastAPI란?
- Python 기반의 웹 프레임워크
- API 서버를 빠르게 개발할 수 있도록 지원
- 비동기 프로그래밍 지원
- Type Hints를 활용한 데이터 검증 및 API 문서 자동 생성 기능 제공
FastAPI의 특징
- 실행 속도가 빠름
- 비동기 웹 프레임워크
- 개발 속도가 빠름
- Python 문법과 Type Hints를 활용하여 작성해야 하는 코드 양을 줄일 수 있음
가상환경 (Virtual Environment)
가상환경이란?
- 프로젝트마다 독립적인 Python 실행 환경을 구성하는 방법
- 프로젝트별 라이브러리와 버전을 분리하여 관리
- 라이브러리 버전 충돌을 방지할 수 있음
가상환경 생성
python -m venv .venv


가상환경 활성화
macOS
source .venv/bin/activate


Windows PowerShell
.venv\Scripts\Activate.ps1


FastAPI 설치
pip install "fastapi[standard]"


ORM (Object-Relational Mapping)
ORM이란?
- 객체 관계 매핑
- Python 객체와 데이터베이스의 데이터를 연결해 주는 기술
- SQL을 직접 작성하지 않고 객체를 활용하여 데이터베이스 작업을 수행할 수 있음
SQLAlchemy
- Python에서 사용하는 ORM 라이브러리
- 데이터베이스 연결, 데이터 조회, 추가, 수정, 삭제 등을 지원
SQLModel과 Tortoise ORM
- SQLModel: Python 타입 힌트와 Pydantic을 활용하여 SQLAlchemy 기반 데이터 모델을 작성할 수 있는 라이브러리
- Tortoise ORM: 비동기 방식으로 데이터베이스 작업을 수행할 수 있는 Python ORM
SQLAlchemy 실습
Python 실행
python -i model.py


- -i: 파일을 실행한 후 Python 대화형 모드 유지
데이터베이스 연결 및 테이블 생성
from connection import engineBase.metadata.create_all(bind=engine)



- engine: 데이터베이스 연결을 관리
- Base.metadata.create_all(): 정의된 모델을 기반으로 테이블 생성
데이터베이스 세션 생성
from connection import SessionFactorysession = SessionFactory()



- Session: 데이터베이스와 상호작용하기 위한 객체
- 데이터 조회, 추가, 수정, 삭제 등을 수행
데이터 추가
item = Item(name="apple", price=100)session.add(item)session.commit()



- session.add(): 세션에 데이터를 추가
- session.commit(): 변경 사항을 데이터베이스에 최종 반영
- commit()을 하지 않으면 일반적으로 데이터베이스에 영구 저장되지 않음
여러 데이터 추가하기
item2 = Item(name="banana", price=200)item3 = Item(name="cherry", price=300)session.add(item2)session.add(item3)session.commit()



데이터 조회
from sqlalchemy import selectstmt = select(Item)result = session.execute(stmt)result.all()



SQLAlchemy가 실행할 SQL 확인
print(stmt)



결과 예시
SELECT item.id, item.name, item.price
FROM item


조회 결과 가져오기
1. all()

- 조회 결과를 Row 객체 형태로 반환
result = session.execute(stmt)result.all()



결과 예시
[    (1, 'apple', 100),    (2, 'banana', 200),    (3, 'cherry', 300)]



2. mappings().all()

- 조회 결과를 딕셔너리와 유사한 형태로 반환
result = session.execute(stmt)result.mappings().all()



결과 예시
[    {'id': 1, 'name': 'apple', 'price': 100},    {'id': 2, 'name': 'banana', 'price': 200},    {'id': 3, 'name': 'cherry', 'price': 300}]



3. scalars().all()

- 조회 결과에서 첫 번째 컬럼 또는 ORM 객체를 추출
stmt = select(Item)result = session.execute(stmt)result.scalars().all()



결과 예시
[    <Item object>,    <Item object>,    <Item object>]



코루틴과 비동기 프로그래밍
코루틴 (Coroutine)
- 실행 중간에 멈췄다가 나중에 다시 이어서 실행할 수 있는 함수
- async def로 정의
- await를 사용하여 비동기 작업이 끝날 때까지 기다림
- I/O 작업 중 다른 작업을 처리할 수 있도록 지원
이벤트 루프 (Event Loop)
- 비동기 작업의 실행 순서를 관리하는 역할
- 실행 가능한 코루틴을 확인하고 적절한 시점에 실행