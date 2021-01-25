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
      
      def change_back_number(self, new_number): #self를 추가해야만 class 함수로 인정
          print(f"선수의 등번호를 변경합니다 : From {self.back_number} to {new_number}")
          self.back_number = new_number  #self.new_number는 init에서 설정한게 아니므로 안되고
          							   #new_number를 사용(이함수에서 받아온것)
          
      def __str__(self):
          return f"Hello, My name is {self.name}. I play in {self.position} in center"
  
  jinhyun = SoccerPlayer("Jinhyun", "MF", 10)
  print(jinhyun)             #Hello, My name is Jinhyun. I play in MF in center 
  ```

- class는 CamelCase를 사용해준다.

- __가 붙은것은 특수한 예약 함수나 변수 그리고 함수명 변경(맨들링)으로 사용

- ```python
  __main__ __add__ __str__ __eq__ 등등
  ```

- ```python
  class Notebook(object):
      def __init__(self,title):
          self.title = title
          self.page_number = 1
          self.notes = {}
          
      def add_note(self,note, page = 0):
          if self.page_number < 300:
              if page == 0:
                  self.notes[self.page_number] = note
                  self.page_number += 1
              else:
                  self.notes = {page : note}
                  self.page_number += 1
          else:
              print("Page가 모두 채워졌습니다.")
              
      def remove_note(self,page_number):
          if page_number in self.notes.keys():
              return self.notes.pop(page_number)
          else:
              print("해당페이지는 존재하지 않습니다.")
              
      def get_number_of_pages(self):
          return len(self.notes.keys())
      
  #-----------------------------------내가 잘못 이해한 것
  print([my_notebook.notes.values()[i] for i in \
         range(1,my_notebook.get_number_of_pages() + 1)])
  # note들이 페이지 1번부터 페이지 끝번까지 차례대로 출력될것으로 생각했다.(페이지가 순서대로 추가되었을 때)
  #하지만 1번 values()는 타입이 dict_values기 때문에 인덱싱이 불가 list()에 넣어서 변환해줘야 가능
  # 2번 list comoprehension은 list를 만들기 위한 것이지 for 문을 대체하는것이 아님. append 대용으로 생각해야 함
  
  for i in my_notebook.notes.values():  
      print(i)
  #이렇게 해결을 했고, 2번을 수정해본다면
  
  for i in range(my_notebook.get_number_of_pages()):
      print(list(my_notebook.notes.values())[i])
  #이렇게 할 수 있겠지만, 페이지도 확인이 안되고 길어져 좋은 코드는 아니다
  
  for i, j in my_notebook.notes.items():  
      print(i, j)
  # 페이지(key)도 같이 확인이 가능한 코드
  ```



- 객체 지향 언어는 실제 세상을 모델링 하는 특징이있다. 필요한 것 세가지

- Inheritance(상속)

- - 부모클래스로부터 속성(attribute)과 method를 물려받을 수 있다.

  - ```python
    class Employee(Person): # 부모 클래스 Person으로 부터 상속
        def __init__(self, name, age, gender, salary, hire_date):
            super().__init__(name, age, gender) # 부모객체 사용(자식 클래스의 input값이다)
            self.salary = salary
            self.hire_date = hire_date # 속성값 추가
        
        def do_work(self): # 새로운 메서드 추가
            print("열심히 일을 합니다.")
        
        def about_me(self): # 부모 클래스 함수 재정의
            super().about_me() # 부모 클래스 함수 사용
            print("제 급여는 ", self.salary, "원 이구요, 제 입사일은 ", self.hire_date,
            " 입니다.")
        #부모클래스 함수를 불러오고 밑은 추가로 더해지는것 (기존것 삭제하는게 아님)
    ```

- Polymorphism(다형성)

- - 같은 이름 메소드의 내부 로직을 다르게 작성

  - Dynamic Typing 특성으로 파이썬에서는 같은 부모클래스의 상속에서 주로 발생한다.

  - 중요한 OOP으 개념이나 너무 깊이 알 필요는 없다

  - ```python
    class Animal:
        def __init__(self, name): # Constructor of the class
            self.name = name
        def talk(self): # Abstract method, defined by convention only
            raise NotImplementedError("Subclass must implement abstract method")
        
    class Cat(Animal):         class Dog(Animal):
        def talk(self):            def talk(self):
            return 'Meow!'             return 'Woof! Woof!'
    
    animals = [Cat('Missy'), Cat('Mr. Mistoffelees'), Dog('Lassie')]
    for animal in animals:
        print(animal.name + ': ' + animal.talk())
    ```

- visibility(가시성)

- - 객체의 정보를 볼 수 있는 레벨을 조절하는 것

  - 누구나 객체 안의 모든 변수를 볼 필요가 없음.

  - - 객체를 사용하는 사용자가 임의로 정보 수정
    - 필요 없는 정보에는 접근 할 필요가 없음
    - 만약 제품으로 판매한다면? 소스의 보호

  - Encapsulation(캡슐화, 정보 은닉(Information Hiding))

  - - Class를 설계할 때, 클래스 간 간섭/정보공유의 최소화
    - 심판 클래스가 축구선수 클래스 가족 정보를 알아야 하나?
    - 캡슐을 던지듯, 인터페이스만 알아서 써야함

  - ```python
    class Product(object):
        pass
    
    class Inventory(object):
        def __init__(self):
            self.__items = []                 #__를 붙여서 숨겨줄 수 있다(정확히는 맨글링)
        def add_new_item(self, product):
            if type(product) == Product:
                self.__items.append(product)
                print("new item added")
            else:
                raise ValueError("Invalid Item")
        def get_number_of_items(self):
            return len(self.__items)
        
        
      #__가 없이 items만 적으면 외부에서 self.items에 접근이 가능해진다
    ```

  - ```python
    @property
        def items(self):
            return self.__items
    #property decorator를 사용해주면 함수를 변수처럼 불러올 수 있다
    
    items = my_inventory.items
    items.append(Product())
    print(my_inventory.get_number_of_items())
    #단 반환을 하고 안쪽에 영향을 주지 않기 위해 카피를 이용한다.
    a = [1,2,3]
    b = a
    b.append(4)
    print(a, b) #[1, 2, 3, 4] [1, 2, 3, 4,]
    a = [1,2,3]
    b = a.copy() #2차원인경우 deepcopy사용 import copy/copy.deepcopy()
    b.append(4)
    print(a, b) # [1, 2, 3] [1, 2, 3, 4]
    
    ```



- 파이썬의 함수는 일급함수(first-class objects)
- - 변수나 데이터 구조에 할당이 가능한 객체
  - 파라메터로 전달이 가능 + 리턴 값으로 사용

- - ```python
    def square(x):
    return x * x
    f = square   #변수에 함수를 할당
    f(5)
    

    def square(x):
        return x * x
    def cube(x):
        return x*x*x
    def formula(method, argument_list): 
        return [method(value) for value in argument_list] #parameter에 함수를 전달 리턴값으로 사용
    argument_list = [1,2,3]
    formula(square, argument_list) #[1, 4, 9] 
    ```

- 함수 내에 또 다른 함수가 존재(Inner function)

- - inner function을 return 값으로 반환(closures)

  - ```python
    def print_msg(msg):
        def printer():
            print(msg)
        return printer                #함수인데 왜 괄호를 적지 않을까?
    another = print_msg("Hello, Python")
    another()
    ```

- 복잡한 closure함수를 간단하게 사용하기위해 decorater를 사용

- ```python
  def generate_power(exponent):  #2가 exponent로 할당
      def wrapper(f):            #함수를 인자로 받아옴
          def inner(*args):      #raise_two의 인자를 받아오기위해서 *arg를 사용
              result = f(*args)  #raise_two의 리턴값을 받아오려고 따로 저장
              return exponent**result #inner의 기능 + raise_two의 리턴값 활용
          return inner
      return wrapper                  #결국 inner의 리턴값이 반환됨
  
  @generate_power(2)
  def raise_two(n):
      return n**2
      
  print(raise_two(2)) #2의 2의제곱 승을 구하는것 - 16
  ```

