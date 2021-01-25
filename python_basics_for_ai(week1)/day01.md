# Hidden class - Basic computer class for newbies

> 컴퓨터에 익숙해지기위해서

> File System & Terminal Basic



### 1.컴퓨터 OS

- Operating System, 운영체제
- 우리의 프로그램이 동작할 수 있는 구동 환경
- 소프트웨어가 하드웨어와 연결될 수 있는 기반
- 어플리케이션은 운영체제에 의존적
- 어느 OS에서 개발을 실행할 것 인가 선택필요



### 2. 파일시스템

- File System
- OS에서 파일을 저장하는 트리구조 저장 체계
- 디렉토리 (Directory)

- - 폴더 or 디렉토리
  - 파일 및 다른 디렉토리 포함가능

- 파일(File) 

- - 정보를 저장하는 논리적인 단위
  - 파일명과 확장자로 식별됨(예: hello.py)
  - 실행,  쓰기, 읽기 등을 할 수 있음

- 파일시스템 root 디렉토리로부터 시작하는 트리구조로 되어있음

- 경로 : 컴퓨터 파일의 고유한 위치, 트리구조상 노드의 연결

- - 절대경로 :  루트 디렉토리부터 파일위치까지의 경로

  - ```
    C:\Users\lee yong woo\Downloads
    ```

  - 상대경로 :  현재 있는 디렉토리부터 타깃 파일까지의 경로

  - ```
    ..\..\Downloads
    ```



### 3.터미널

- 마우스가 아닌 키보드로 명령을 입력 프로그램 실행
- GUI(Graphic User Interface) 와 다르게 Text를 사용하여 컴퓨터에 명령을 입력하는 인터페이스 체계
- CLI(Command Line Interface)
- - Windows - CMD window, Window Terminal, cmder
- - Mac, Linux - Terminal
- Console = Terminal = CMD창
- 어원은 은행원들이 주로쓰던 디스플레이와 키보드가 조합된 장치고 현재는 CLI로 입력되는 화면
- - 윈도우 - 윈도우 키 + R 입력 후 CMD 입력 (Ubuntu설치도 권장Linux환경)
- - 맥 - 빠른실행 terminal 입력
- 각 터미널에서는 프로그램을 작동하는 shell이 존재
- - shell마다 다른 명령어를 사용
- core를 둘러싸고 명령어를 전달해주는 역할 종류가 상당히 많다(Powershell, cmd창, bash zshell)



#### CMD창 명령어(shell명령어)

- CD(cd) - 현재 디렉토리 이름을 보여주거나 바꾼다(change directory)
- CLS(clear) - CMD 화면에 표시된 것을 모두 지운다(clear screen)
- COPY(cp) - 하나 이상의 파일을 다른 위치로 복사
- DEL(rm) - 하나 이상의 파일을 지운다(delete)
- DIR(ls) - 디렉토리에 있는 파일과 하위 디렉토리 목록을 보여준다(directory)
- ..\은 상위디렉토리 .\은 현재 디렉토리
- tap을 잘 활용(후속을 자동 완성)
- 여러가지 shell이 다 익숙해지는게 중요





# 파이썬 개요

- 자비로운 종신 독재자? 파이썬의 개선사항(PEP)에 대한 최종 의사결정자





### 1.플랫폼 독립적 인터프리터 언어

- 플랫폼 (= OS) 에 상관없이 한번 프로그램을 작성하면 사용가능
- 인터프리터 언어 = 통역기를 사용하는 언어
- - 소스코드를 바로 실행할 수 있게 지원하는 프로그램 언어
- 컴파일러는 소스코드를 기계어로 먼저번역, 해당 플랫폼에 최적화되어 프로그램을 실행
- - 실행속도가 빠르지만 한번에 많은 기억장소 필요(C, 자바, C++, C#)
- 인터프리터는 별도의 번역과정 없이 소스코드를 실행시점에 해석하여 컴퓨터가 처리할 수 있도록 함
- - 간단히 작성가능하고 메모리가 적게 필요, 실행속도가 느리다(파이썬, 스칼라)
-  Compiler + Assembler vs Interpreter(파이썬은 처음에 C로 작성됨 실행시 Assembler와 같은 기계어 변환 과정을 거친다)



### 2.객체지향의 동적 타이핑 언어

> 객체 지향적 언어 : 실행 순서가 아닌 모듈(객체)중심으로 프로그램을 작성(≠procedure한 언어)
>
> - 하나의 객체는 어떤 목적을 달성하기 위한 행동(method)와 속성(attribute)을 가지고 있음
>
> 동적 타이핑 언어 :  프로그램이 실행하는 시점에 프로그램이 사용해야 할 데이터에 대한 타입을 결정



### 3.Why Python?

- 이해하기 쉬운 문법(사람의 시간이 기계의 시간보다 중요하다)
- 다양한 라이브러리(특히 통계, 데이터 분석)
- disposable코드 를 만들기에 파이썬만한 언어가 없다.
- Life is short, You need Python





# 개발 환경 설정

> 프로그램을 작성하고, 실행시키려는 환경 (코딩 환경)
>
> 개발 환경을 결정
>
> - 운영체제(Operating System)
> - Python Interpriter
> - 코드 편집기(editer)



### 1.운영체제

> 선호하는 운영체제르 선정

- Windows
- - 친숙함, 초기엔 쉬움
  - 모듈 설치 어려움
- Linux
- - 모듈 설치 쉬움, 공짜, 참고문서 많음
  - OS 자체 사용이 어려움(어렵지만 반드시 배워야 할 필요가 있음.)
- Mac OS
- - 모듈 설치 쉬움, 참고문서 많음
  - 비쌈..



### 2. 파이썬 인터프리터

- 2.X와 3.X가 존재, 현재 대부분 3.X 기준으로 시스템이 작동됨(2.X legacy)
- Python - 일반적인 파이썬, 기본적인 모듈을 포함
- Anaconda - 다양한 과학 계산용 모듈들을 묶어서 패키지(miniconda 사용)



### 3.코드 편집기

- 파이썬 코드도 일종의 문서 - 편집기가 필요함
- 메모장, vi editor
- Submlime Text, Atom, VS Code - 프로그래밍 특화
- PyCharm - 다양한 기능을 갖춤
- 코드 편집기의 두가지 타입
- - 설치된 어플리케이션(VS Code)
  - 웹 기반 인터랙티브 편집기(jupyter, colab)



### 4.웹기반IDE

- 사실상의 데이터 분석 Interactive Shell의 표준

- Python shell + 코드편집기

- 내가 원하는 디렉토리로 가서 실행하기

- ```python
  jupyter notebook
  ```

- (base나 다른 가상환경으로 가서conda activate base)



