# Python Data Structure

> stack & queue, tuple & set, dictionary, collections



- stack : LIFO
- - 입력을 Push 출력을 Pop
  - list에서 append()와 pop()로 구현가능
- list(string)을하면 한글자씩 나눠서 리스트로 저장



- queue : FIFO
- - 입력을 put 출력을 get
  - list에서 append()와 pop(0)으로 구현가능 pop(0)는 왼쪽부터 꺼내온다
  - pop()은 return값도 있지만 list자체도 변화시켜주는 함수 저장할필요x



- tuple : 값의 변경이 불가능한 리스트

- - ()로 선언, 리스트의 연산, 인덱싱, 슬라이싱 등을 동일하게 사용

  - 프로그램을 작동하는동안 변경되지 않는 데이터의 저장할 때, 사용자의 실수에 의한 에러를 방지할 때

  - ```
    t = (1)    # 일반 정수로 인식
    t2 = (1, ) # ','를 붙여줌으로서 tuple로 인식
    ```



- set : 값을 순서없이 저장, 중복 불허하는 자료형(집합)

- - ```
    s = set([1, 2, 3]) # 선언방식
    s = {1,2,3}
    s.update([4, 5, 6]) #셋다 가능
    s.update({7, 8, 9})
    s.update((10, 11, 12))
    ```

  - 집합 연산이 가능하다

  - ```python
    s1.union(s2)  # s1 | s2
    s1.intersection(s2) # s1 & s2
    s1.difference(s2) # s1 - s2
    ```



- dictionary(dict) : 구분 지을 수 있는 값을 함께 저장 Key 와 Value

- - 다른언어에서는 Hash Table이라는 용어를 사용

  - ```
    {Key1:Value1, Key2:Value2, Key3:Value3} #형태
    dict.items() #key, Value값을 튜플로 묶어 리스트형태로 반환(타입은 dict_items언패킹가능)
    ```



- colletions : list tuple dict 에 대한 Python Built-in 확장 자료 구조(모듈)

- - deque : stack과 queue를 지원하는 모듈 list에 비해 효율적인(=빠른) 자료 저장 방식을 지원함

  - Linked List의 특성을 지원함

  - ```\
    deque_list = deque()
    deque_list.rotate
    deque_list.extend
    ```



- - OrderdDict : 데이터를 입력한 순서대로 dict를 반환해주는데, python 3.6부터는 dict도 마찬가지다.



- - defaultdict : Dict type의 값에 기본 값을 지정, 신규값 생성시 사용하는 방법



- - Counter : 