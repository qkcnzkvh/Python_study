Python 객체지향 프로그래밍(OOP)
1. 클래스와 객체
객체지향 프로그래밍(Object-Oriented Programming)은 데이터와 데이터를 처리하는 기능을 객체 단위로 묶어 관리하는 프로그래밍 방식이다.
- 클래스(Class): 환자 차트의 양식
- 객체(Object): 실제 환자의 차트
클래스(Class)
데이터와 기능을 하나로 묶어 새로운 객체를 만들기 위한 템플릿.
class 클래스명(부모클래스):    pass



- 클래스명은 파스칼 케이스(PascalCase)를 사용한다.
- 각 단어의 첫 글자는 대문자로 작성하며, 띄어쓰기나 언더바를 사용하지 않는다.
객체(Instance)
클래스를 이용해 만든 실제 값.
class Patient:    passpatient1 = Patient()patient2 = Patient()



patient1과 patient2는 Patient 클래스로 만든 서로 다른 객체이다.
__init__
객체가 생성될 때 자동으로 호출되는 초기화 메서드.
class Patient:    def __init__(self, name):        self.name = namepatient = Patient("Alex")



self
인스턴스 자신을 가리키는 매개변수.

self.name은 해당 객체의 name 속성을 의미한다.
인스턴스 속성과 클래스 속성
구분	접근 방식	특징
인스턴스 속성	객체명.변수	객체마다 별도로 가짐
클래스 속성	클래스명.변수	클래스에 속하며 인스턴스들이 공유

2. 주요 메서드
메서드는 클래스 내부에 정의한 함수이다.
종류	첫 번째 매개변수	특징
인스턴스 메서드	self	객체의 속성에 접근하고 객체별 동작을 수행
클래스 메서드	cls	클래스 자체에 접근하고 클래스 단위 동작을 수행
정적 메서드	없음	클래스나 객체의 상태에 직접 의존하지 않는 기능

class Patient:    count = 0    def instance_method(self):        pass    @classmethod    def class_method(cls):        pass    @staticmethod    def static_method():        pass



3. 매직 메서드(Magic Method)
__이름__ 형태로 작성하는 특별한 메서드.

파이썬의 내장 동작을 객체에 맞게 정의하거나 변경할 수 있다.
메서드	역할
__init__	객체 초기화
__str__	객체를 사람이 읽기 쉬운 문자열로 표현
__repr__	객체의 개발자용 문자열 표현
__len__	len() 호출 시 반환할 길이 정의
__eq__	== 비교 동작 정의
__iter__	객체를 반복 가능한 형태로 만듦

4. 캡슐화(Encapsulation)
데이터(속성)와 메서드를 하나로 묶고, 외부에서 데이터에 직접 접근하는 것을 제한하는 개념.

파이썬에서는 이름 앞에 언더바를 붙여 접근 수준을 표현한다.
표기	관례	설명
name	Public	일반 속성. 외부에서 자유롭게 접근 가능
_name	Protected	외부에서 직접 접근하지 않는 것을 권장하는 관례
__name	Private	이름 맹글링(Name Mangling)을 통해 직접 접근을 어렵게 함

_name과 __name 모두 완전한 접근 차단을 의미하지는 않는다.
5. 상속(Inheritance)
부모 클래스의 속성과 메서드를 자식 클래스가 물려받아 확장하는 개념.
- 부모 클래스: 공통 기능을 정의
- 자식 클래스: 부모의 기능을 물려받고 고유 기능을 추가
class MedicalStaff:    def __init__(self, name):        self.name = nameclass Doctor(MedicalStaff):    def diagnose(self):        print("진료")class Nurse(MedicalStaff):    def care(self):        print("간호")



super()
부모 클래스의 메서드에 접근할 때 사용한다.
class Doctor(MedicalStaff):    def __init__(self, name, department):        super().__init__(name)        self.department = department



super().__init__(name)은 부모 클래스의 초기화 메서드를 호출한다.
다단계 상속
상속을 여러 단계로 이어서 구성할 수 있다.
class MedicalStaff:    passclass Doctor(MedicalStaff):    passclass Surgeon(Doctor):    pass



Surgeon은 Doctor를 거쳐 MedicalStaff의 기능도 물려받는다.
MRO(Method Resolution Order)
메서드 탐색 순서. 객체에서 메서드를 호출할 때 어떤 클래스부터 찾아볼지 나타낸다.
print(Surgeon.__mro__)



__mro__를 통해 해당 클래스의 상속 순서를 확인할 수 있다.
메서드 오버라이딩(Overriding)
부모 클래스의 메서드를 자식 클래스에서 다시 정의하여 다른 동작을 수행하게 하는 것.
class MedicalStaff:    def work(self):        print("의료 업무")class Doctor(MedicalStaff):    def work(self):        print("진료")



Doctor의 work()를 호출하면 자식 클래스에서 정의한 동작이 실행된다.
6. 다형성(Polymorphism)
같은 메서드 호출이라도 객체의 종류에 따라 서로 다른 동작을 수행하는 개념.
메서드 오버라이딩
자식 클래스에서 부모의 메서드를 재정의하여 서로 다른 동작을 수행한다.
덕 타이핑(Duck Typing)
상속 관계가 없어도 필요한 메서드를 가지고 있다면 동일한 방식으로 사용할 수 있는 개념.
class Doctor:    def work(self):        print("진료")class Nurse:    def work(self):        print("간호")def start_work(staff):    staff.work()start_work(Doctor())start_work(Nurse())



Doctor와 Nurse는 상속 관계가 없지만, 둘 다 work() 메서드를 가지고 있으므로 같은 방식으로 사용할 수 있다.