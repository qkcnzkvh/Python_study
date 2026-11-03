Python 파일 입출력 & 예외 처리
1. 파일 입출력(File I/O)
파일 입출력은 파일을 읽거나 데이터를 저장하는 작업이다.
파일 열기
open() 함수로 파일을 열고, 작업이 끝나면 close()로 닫는다.
open("파일명.txt", "모드", encoding="utf-8")



모드	기능
r	읽기
w	쓰기. 기존 내용 덮어쓰기
a	추가 쓰기. 기존 내용 유지
r+	읽기와 쓰기
rb	바이너리(이진 데이터) 읽기

- 한글이 포함된 텍스트 파일은 encoding="utf-8"을 지정하면 올바르게 읽고 쓸 수 있다.
- 인코딩(Encoding)은 문자를 컴퓨터가 저장하고 해석하는 방식이다.
파일 자동으로 닫기
with문을 사용하면 작업이 끝났을 때 파일이 자동으로 닫힌다.
with open("파일명.txt", "r", encoding="utf-8") as f:    content = f.read()



2. 파일 읽기
메서드	기능
.read()	파일 전체 내용을 문자열로 읽음
.readline()	한 줄씩 읽음
.readlines()	모든 줄을 리스트로 읽음

with open("data.txt", "r", encoding="utf-8") as f:    content = f.read()



대용량 파일 읽기
with open("data.txt", "r", encoding="utf-8") as f:    for line in f:        print(line)



파일을 한 번에 메모리에 불러오지 않고 한 줄씩 처리할 수 있어 대용량 파일에 효율적이다.
3. 파일 쓰기 및 추가하기
쓰기(w)
기존 파일이 있으면 내용을 모두 덮어쓰고, 파일이 없으면 새로 만든다.
with open("data.txt", "w", encoding="utf-8") as f:    f.write("안녕하세요")



추가 쓰기(a)
기존 내용을 유지하면서 파일 끝에 새로운 내용을 추가한다.
with open("data.txt", "a", encoding="utf-8") as f:    f.write("새로운 내용\n")



- write()는 문자열을 파일에 기록한다.
- writelines()는 여러 문자열을 기록한다. 줄바꿈을 자동으로 추가하지 않으므로 \n을 직접 넣어야 한다.
4. 파일 경로 지정
파일 경로는 파일이 위치한 폴더를 나타낸다.
"data/example.txt"



- /를 사용하여 상위 폴더와 하위 폴더를 구분한다.
- 상대 경로는 현재 작업 디렉터리를 기준으로 한다.
- 절대 경로는 파일의 전체 경로를 나타낸다.
5. CSV 파일 처리
CSV(Comma-Separated Values)는 행과 열로 이루어진 표 형식의 데이터를 쉼표로 구분하여 저장하는 파일 형식이다.

파이썬의 csv 모듈을 사용하면 CSV 파일을 읽고 쓸 수 있다.
CSV 읽기
import csvwith open("patients.csv", "r", encoding="utf-8-sig") as f:    reader = csv.DictReader(f)    for row in reader:        print(row)



- DictReader는 첫 번째 행을 헤더로 인식한다.
- 각 행을 딕셔너리 형태로 읽는다.
- utf-8-sig는 UTF-8 인코딩에 BOM을 포함한 파일을 읽을 때 사용할 수 있다. 엑셀에서 저장한 CSV 파일의 한글 깨짐을 방지하는 데 유용하다.
CSV 쓰기
import csvwith open("patients.csv", "w", encoding="utf-8-sig", newline="") as f:    writer = csv.DictWriter(        f,        fieldnames=["name", "age"]    )    writer.writeheader()    writer.writerows([        {"name": "Alex", "age": 20},        {"name": "Bob", "age": 30}    ])



메서드	기능
writeheader()	열 이름을 헤더 행에 기록
writerows()	여러 행의 데이터를 기록

- DictReader와 DictWriter는 딕셔너리 형태의 데이터를 처리한다.
- newline=""은 CSV 파일을 쓸 때 불필요한 빈 줄이 생기는 것을 방지한다.
6. 예외 처리(Exception Handling)
예외 처리는 예상치 못한 오류가 발생했을 때 프로그램이 안전하게 처리하도록 하는 방법이다.
기본 구조
try:    # 오류가 발생할 수 있는 코드    passexcept ValueError:    # 오류 처리    passfinally:    # 항상 실행되는 코드    pass



구문	역할
try	오류가 발생할 수 있는 코드 실행
except	특정 예외가 발생했을 때 처리
finally	예외 발생 여부와 관계없이 실행

예외 발생시키기: raise
raise는 의도적으로 예외를 발생시킬 때 사용한다.
age = -1if age < 0:    raise ValueError("나이는 음수가 될 수 없습니다.")



finally 블록
예외 발생 여부와 관계없이 반드시 실행해야 하는 작업에 사용한다.

파일 닫기나 자원 정리 등에 활용할 수 있다. 다만 파일 작업에서는 with문을 사용하는 것이 일반적이다.
7. 주요 예외 타입
예외	발생하는 경우
ValueError	올바르지 않은 값이 전달됨
TypeError	지원하지 않는 타입의 연산이나 함수 호출
KeyError	딕셔너리에 없는 키에 접근
IndexError	리스트 등의 범위를 벗어난 인덱스에 접근
FileNotFoundError	존재하지 않는 파일을 열려고 함
ZeroDivisionError	0으로 나누려고 함

예외의 계층 구조
BaseException
    └── Exception
          ├── ValueError
          ├── TypeError
          ├── KeyError
          ├── IndexError
          └── FileNotFoundError


- Exception은 일반적인 프로그램 오류의 상위 클래스이다.
- BaseException은 Exception보다 더 넓은 범위의 예외를 포함한다.
- except Exception:처럼 상위 클래스로 처리하면 하위 예외도 함께 잡을 수 있다.
- 일반적인 오류 처리는 except Exception:을 사용하고, BaseException은 특별한 이유가 없다면 직접 잡지 않는다.