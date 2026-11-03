Python 함수 정리
1. 함수(Function)
반복되는 코드에 이름을 붙여 재사용할 수 있도록 묶은 코드 블록.
def 함수명(매개변수):    return 반환값



- 함수 정의 뒤에는 :을 붙인다.
- 함수 내부 코드는 들여쓰기를 사용한다.
2. 매개변수와 인자
매개변수(Parameter)
함수를 정의할 때 입력값을 받기 위해 설정하는 변수. 함수 내부에서 사용한다.

- 여러 개를 사용할 수 있으며 ,로 구분한다.
인자(Argument)
함수를 호출할 때 매개변수에 실제로 전달하는 값.
def add(a, b):  # a, b는 매개변수    return a + badd(3, 5)       # 3, 5는 인자



인자는 매개변수에 전달되어 함수 내부에서 사용된다.
3. return
함수의 실행 결과를 호출한 곳으로 돌려주는 키워드.
- return 이후의 코드는 실행되지 않는다.
- 함수에 return이 없거나 값 없이 return하면 None을 반환한다.
- 함수의 실행을 종료할 때도 사용한다.
def add(a, b):    return a + bresult = add(3, 5)print(result)  # 8



4. 인자의 전달 방식
위치 인자(Positional Argument)
인자가 전달될 때 매개변수의 순서에 따라 값이 매핑되는 방식.
def introduce(name, age):    print(name, age)introduce("Alex", 20)



순서를 바꾸면 다른 매개변수에 값이 전달된다.
키워드 인자(Keyword Argument)
매개변수이름=값 형식으로 인자를 지정하는 방식.
introduce(age=20, name="Alex")



매개변수 이름을 지정하므로 순서를 바꿔도 된다.
위치 인자와 키워드 인자 혼합
혼합해서 사용할 때는 위치 인자를 먼저 작성한다.
def example(a, b, c):    print(a, b, c)example(1, 2, c=3)



5. 가변 인자
인자의 개수가 정해져 있지 않을 때 사용한다.
구분	역할
*args	여러 위치 인자를 튜플로 받음
**kwargs	여러 키워드 인자를 딕셔너리로 받음

def example(*args, **kwargs):    print(args)    print(kwargs)example(1, 2, name="Alex", age=20)



결과:
(1, 2){'name': 'Alex', 'age': 20}



6. 스코프(Scope)
변수의 유효 범위.
지역 변수(Local Variable)
함수 내부에서 선언되어 해당 함수 안에서만 사용할 수 있는 변수.
전역 변수(Global Variable)
함수 밖에서 선언되어 프로그램 전체에서 사용할 수 있는 변수.

global 키워드를 사용하면 함수 내부에서 전역 변수의 값을 변경할 수 있다.
count = 0def increase():    global count    count += 1



7. 람다 함수(Lambda Function)
이름이 없는 익명 함수. def 없이 한 줄로 간단한 함수를 만들 수 있다.
lambda 매개변수: 반환값을_만드는_표현식



- return 키워드 없이 표현식의 결과를 자동으로 반환한다.
- map(), filter(), sort(), sorted() 등에서 자주 사용한다.
예시
patients.sort(key=lambda p: p["bp"])



- bp를 기준으로 환자 목록을 정렬한다.
list(filter(lambda p: p["bp"] >= 140, patients))



- 혈압이 140 이상인 환자만 필터링한다.
list(map(lambda p: p["bp"] + 10, patients))



- 모든 환자의 혈압 값에 10을 더한다.
8. 타입 힌팅(Type Hinting)
변수나 함수의 입력값, 반환값 등에 타입을 명시하는 것.

다른 개발자가 코드를 이해하기 쉽게 하고, 코드 편집기에서 타입 관련 도움을 받을 수 있다.
age: int = 20def add(a: int, b: int) -> int:    return a + b



- a: int: a는 정수형이라는 힌트
- -> int: 함수의 반환값은 정수형이라는 힌트
9. 독스트링(Docstring)
함수나 클래스가 어떤 역할을 하는지 설명하는 문서 문자열.

큰따옴표 세 개(""")를 사용한다.
def add(a, b):    """    두 숫자를 더한 값을 반환한다.    """    return a + b



10. 네이밍 규칙
snake_case
띄어쓰기 대신 언더바(_)를 사용하고, 소문자로 작성하는 방식.
def calculate_average():    pass



함수명과 변수명에 주로 사용한다.