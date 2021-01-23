# Python Object Oriented Programming

> 클래스와 객체를 이해해보자



- 수강신청 프로그램을 만든다면 주체들(교수, 학생, 관리자)의 행동(수강신청, 과목 입력)과 데이터(수강과목, 강의 과목)들을 중심으로 프로그램 작성 후 <u>**연결**</u>

- 객체는 속성(attribute)와 행동(action)을 가진다

- 속성은 변수(variable) 행동은 함수(method)로 표현

- class는 설계도라고 볼 수 있고 실제 구현체인 인스턴스(instance)가 있다

- ```python
  class SoccerPlayer(object):  #object는 3.x에서는 상속안해도 되지만 2.x 와의 호환성을 위해 적어							주는것이 좋다.
      def __init__(self, name, position, back_number): #__init__은 객체 초기화 예약 함수
          self.name = name                    #self는 후에 생성된 인스턴스의 이름이라고 생각
          self.position = position
          self.back_number = back_number
      
      def change_back_number(self, new_number):
          print("선수의 등번호를 변경합니다 : From %d to %d" % (self.back_number, new_number))
          self.back_number = new_number 
  ```

- class는 CamelCase를 사용해준다.

- __가 붙은것은 특수한 예약 함수나 변수 그리고 함수명 변경(맨들링)으로 사용

- ```
  __main__ __add__ __str__ __eq__ 등등
  ```

- 

