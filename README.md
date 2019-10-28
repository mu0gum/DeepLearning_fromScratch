# DeepLearning_fromScratch

## 파이썬 기초 정리
 - 입문부터 실무까지 한 방에 끝내는 파이썬 프로그래밍(http://www.yes24.com/Product/Goods/74312880?Acode=101) 참고

### 함수(Function)
 - 함수명(Function name), 인자 값(Argument value), 반환 값(Return value)
 
### 변수(Variable)
 - 변수는 메모리상의 주소를 사람이 읽을 수 있는 쉬운 언어로 표한하기 위한 용도로 사용
 - 첫 글자는 반드시 영문 대소문자 혹은 언더바로 시작
 - 나머지 글자들은 영문자, 숫자 혹은 언더바로 구성
 - 대소문자 구분
 - 길이 제약 없음
 - 예약어 사용 불가
 - 좋은 변수명은?
 ```
 1. 짧게 축약하는 것보다는 의미가 담겨 있게 ex) rn > room_no
 2. 변수명의 길이를 불필요하게 길게 X
 3. 변수명 형식을 일관성있게
 4. 언더바로 시작하는 변수명은 특수한 경우
 ```

### 클래스(Class)와 객체(Object)
```python3

 var1 = '파이썬'
 var2 = '파이썬'
 
 var1 == var2 # True (변수의 데이터 값 비교)
 var1 is var2 # False (객체 비교)

 id(var1) # 56627560 (객체 식별자 확인)
 type(var1) # <class 'str'> (클래스 확인)
 
 # id(), type()은 파이썬 기본 내장 함수
```
 - replace() 등과 같이 클래스에 속한 함수는 id(), type()처럼 단독으로 사용 불가 (생성된 객체를 통해서만 실행 가능)
 - 위와 같은 함수를 파이썬에서는 메소드(method)라고 함
 - **파이썬의 모든 것은 클래스로 이루어져 있음**
 

## 데이터 타입
 - 데이터의 공통된 특징과 용도에 따라 분류하여 정의한 것


### 숫자 타입(Numeric Type)
 - 데이터를 더하고 빼고 곱하고, 나눌 수 있는 데이터 타입
 - 파이썬에서는 정수 타입인 int, 실수 타입인 float, 복소수를 위한 Complex 등을 제공
 (https://docs.python.org/3/library/stdtypes.html#typesnumeric)
 
 
### 논리 타입(Boolean Type)
 - 데이터 중 참과 거짓을 통하여 표한할 수 있는 데이터 타입
 - and, or, not 논리 연산자 제공
 - True : 1, False : 0

```python3
 int(True)  # 1
 int(False) # 0
```
 
### 문자열 타입(String Type)
 - 문자열 타입은 데이터가 여러 문자로 구성되어 있고 다른 문자와 연결될 수 있으며 데이터에 포함된 문자열의 길이를 확인할 수 있는 데이터 타입
 - 홑따옴표(')나 쌍따옴표(")로 감싸서 표현(https://docs.python.org/3/library/stdtypes.html#string-methods)

### 데이터 타입 에러
```python3
 '350' + 350 # TypeError : Can't convert 'int' object to str implicitly
```

### 데이터 타입 변환
 - 파이썬에서는 변수를 선언할 때 이 변수의 데이터 타입이 무엇인지 표기하지 않음
 - C++ 나 자바와 같은 언어를 사용했다면 반드시 변수명 앞에 데이터 타입을 표기해야 함
 - 이와 같이 데이터 타입을 표기하지 않고 **프로그램이 실행될 때 해당 변수에 대한 데이터 타입이 결정되는 것을 동적 타이핑(Dynamic Typing)** 이라고 함

### 변할 수 없는(Immutable) vs 변할 수 있는(Mutable)
 - 파이썬의 데이터 타입에는 **변할 수 없는 데이터 타입**과 **변할 수 있는 데이터 타입**이 존재
 - 전자를 영어로 Immutable, 후자는 Mutable로 표현

```python3
 >>> hello = '안녕' # hello 문자열 타입 변수 선언
 >>> hello
 '안녕'
 >>> id(hello) # hello 객체 식별자 확인
 59263440
 >>> hello = '반가워' # hello 변수 값 변경
 >>> hello
 '반가워'
 >>> id(hello) # hello 객체 식별자 확인(변경)
 59263328
```
 
 - hello 라는 변수에 새로운 값을 할당했을 때, 같은 객체에 값만 변경할 것이라고 생각할 수 있지만, 파이썬에서는 변할 수 없는(Immutable) 데이터 타입에 새로운 값을 대입하면 **새로운 객체를 생성하여 그 객체를 연결**
 - 변할 수 있는(Mutable) 데이터 타입의 예는 리스트 타입이 있음
 
```python3
 >>> hello_list = ['안녕!'] # 리스트 타입 선언
 >>> hello_list
 ['안녕!']
 >>> id(hello_list) # 리스트 객체 식별자 확인
 59201736
 >>> hello_list[0] = '반가워!' # 리스트 첫 번째 항목 값 변경하기
 >>> hello_list
 ['반가워!']
 >>> id(hello_list) # 리스트 객체 식별자 확인(동일)
```
