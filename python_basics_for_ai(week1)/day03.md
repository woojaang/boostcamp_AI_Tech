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



- - Counter :  Sequence type의 data element들의  갯수를 dict형태로 반환(key가 성분 value가 갯수)

  - set의 연산들을 지원함

  - ```python
    c = Counter(a=4, b=2, c=0, d=-2)
    d = Counter(a=1, b=2, c=3, d=4)
    c.subtract(d) #c - d
    c + d # a=5 b=4 c=3 d=2 중복이 허용되기 때문에 | 와 다르다.
    c & d # b=2 a=1
    c | d # a=4 b=2 c=3 d=4
    ```



- - namedtuple :  Tuple 형태로 Data 구조체를 저장하는 방법





# Pythonic code

> 파이썬 스타일의 코딩 기법
>
> 파이썬 특유의 문법을 활용하여 효율적으로 코드를 표현
>
> 고급 코드를 작성 할 수록 더 많이 필요해짐



- split :  string type의 값을 기준값으로 나눠서 List형태로 변환
- join : sting으로 구성된 list를 합쳐 하나의 string으로 반환(join앞에 연결을 무엇으로 할것인지 지정 ''는 이어서)



- list comprehension : 기존 List를 사용하여 다른 List를 만드는 기법 일반적인 방법보다 빠름

- ```python
  result = [i for i in range(10)]
  word_1 , word_2 = "a", "b"
  result = [i+j for i in word_1 for j in word_2] # for i~ 밑에 for j~ 가 도는것과 같다
  result = [i+j for i in word_1 for j in word_2 if not(i==j)]
  # [i+j if not(i==j) else i for i in case_1 for j in case_2] if else를 앞에 보낼 수도 있음. 다만 else없이 if만 보낼수는 없음
  stuff = [[w.upper(), w.lower(), len(w)] for w in words] #list words 의 각 elelment들을 대문자 소문자 길이로 변환하여 2 dimensional list로 변환. words는 스플릿돼어있는 list
  
  
  ```



- enurmerate : list의 element를 추출할 때 번호를 붙여서 추출

- ```python
  mylist = ['a', 'b', 'c', 'd']
  list(enumerate(mylist)) # list의 있는 index와 값이 tuple로 묶여 unpacking하여 list로 저장
  ```

- zip : 두개의 list의 값을 병렬적으로 추출함

- ```python
  a,b,c =zip((1,2,3),(10,20,30),(100,200,300)) # tuple도 가능 (1,10,100)...
  [sum(x) for x in zip((1,2,3), (10,20,30), (100,200,300))] # 각 튜플의 합을 추출
  ```



- lambda : 함수 이름 없이, 함수처럼 쓸 수 있는 익명함수

- map : 함수를 시퀀스형 데이터에 맵핑을해줘서 순서대로 값을 받아준다.

- ```python
  ex = [1,2,3,4,5]
  ex2 = [1,2,3,4,5,6,7,8]
  f = lambda x, y: x + y
  
  list(map(f,ex)) #[1, 4, 9, 16, 25]
  print(list(map(f, ex, ex2))) #[2, 4, 6, 8, 10]
  
  #if filter도 사용 가능
  list(map(lambda x: x** 2 if x % 2 == 0 else x, ex)) #[1, 4, 3, 16, 5]
  ```

- - python3는 iteration을 생성 -> list를 붙여줘야 list 사용가능
  - 실행시점의 값을 생성, 메모리 효율적

- reduce : list에 똑같은 함수를 적용해서 통합

- ```python
  from functools import reduce
  print(reduce(lambda x, y: x+y, [1, 2, 3, 4, 5])) #15
  ```

- python3에서 사용을 권장하지 않지만 Lagacy library나 많은 머신러닝 코드에서 사용중 알고있어야함



- iterable object : Sequence형 자료형에서 데이터를순서대로 추출하는 object

- ```python
  for city in ["Seoul", "Busan", "Pohang"]:
  print(city, end="\t")
  #내부적 구현으로 __iter__와 __next__가 사용됨
  #iter(), next()함수로 iterable 객체를 iterator object로 사용
  
  cities = ["Seoul", "Busan", "Jeju"]
  iter_obj = iter(cities)
  print(next(iter_obj))
  print(next(iter_obj))
  print(next(iter_obj))
  next(iter_obj) # Stopiteration
  ```



- generator : iterable object를 특수한 형태로 사용해주는 함수

- - element가 사용되는 시점에 값을 메모리에 반환 - yield를 사용해 element 하나씩 반환함

  - ```python
    def geneartor_list(value):
        result = []
        for i in range(value):
            yield i
    ```

  - list comprehension과 유사한 형태로 generator형태의 list 생성 ()사용

  - ```python
    gen_ex = (n*n for n in range(500))
    print(type(gen_ex)) # 타입은 generator로 나온다.
    from sys import getsizeof #메모리가 일반적인 iterator보다 적은걸 알 수 있다.
    ```

  - list타입의 데이터를 반환해주는 함수는 generator로 만드는것이 좋다.(읽기 쉽운 장점이 있고, loop이 중간에 중단될 수 있을떄)

  - 큰데이터를 처리할 때 역시 generator expression(comprehension)을 사용하는 것이 좋음



- function passing arguments

- - keyword arguments : 함수에 입력되는 parameter의 변수명을 사용 arguments를 넘김(순서상관x)

  - ```python
    def print_somthing(my_name, your_name):
    	print("Hello {0}, My name is {1}".format(your_name, my_name))
    
    print_somthing(your_name="TEAMLAB", my_name="Sungchul")
    ```

  - default arguments : default 값을 미리 지정 입력이 없을경우 기본값 출력

  - ```
    def print_somthing_2(my_name, your_name="TEAMLAB"):
    	print("Hello {0}, My name is {1}".format(your_name, my_name))
    
    print_somthing_2("Sungchul")
    ```

  - variable-length asterisk : 개수가 정해지지 않은 변수를 parameter로 사용하는 법

  - 입력된 값은 tuple type으로 사용할 수 있음.

  - 가변인자는 한 개만 마지막 parameter 위치에 사용가능

  - 일반적으로 *args를 변수명으로 사용 / 기존 parameter 이후에 나오는 값을 tuple로 저장함

  - ```python
    def asterisk_test(a, b, *args):
        return a+b+sum(args)
    print(asterisk_test(1, 2, 3, 4, 5))
    ```

  - keyword 가변인자 : parameter 이름을 따로 지정하지 않고 입력하는 방법

  - asterisk 두개를 사용하고 입력된 값은 dict type으로 사용할 수 있음

  - ```python
    def kwargs_test_3(one,two, *args, **kwargs):
        print(one+two+sum(args))
        print(kwargs)
       
    kwargs_test_3(3,4,5,6,7,8,9, first=3, second=4, third=5) #'first'가 아닌 이유?
    ```

  - asterisk-unpacking a container : tuple, dict등 자료형

  - 함수의 입력값, zip등에 유용하게 사용가능

  - ```python
    def asterisk_test(a, *args): #2.가변이자로 받음
        print(a, args)           #3.args에 tuple로 저장
        print(type(args))        #4. tuple
    asterisk_test(1, *(2,3,4,5,6)) #1.풀려서 들어감
    
    def asterisk_test(a, args):  #2. 튜플로 받음(값은 하나)
        print(a, *args)          #3. 튜플을 풀어서 출력
        print(type(args))        #4. 타입은 tuple(3에서 출력만 했으므로)
    asterisk_test(1, (2,3,4,5,6)) #1.tuple로 들어감
    ```

  - ```python
    a, b, c = ([1, 2], [3, 4], [5, 6]) #같은 출력
    print(a, b, c)
    data = ([1, 2], [3, 4], [5, 6])
    print(*data)
    
    def asterisk_test(a, b, c, d,):
        print(a, b, c, d)
    data = {"b":1 , "c":2, "d":3}
    asterisk_test(10, **data)
    
    for data in zip(*([1, 2], [3, 4], [5, 6])):  #언패킹해서 값이 들어감 list가 여러개
        print(data)
    ```