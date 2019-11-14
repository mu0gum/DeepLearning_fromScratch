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

 id(var1)     # 56627560 (객체 식별자 확인)
 type(var1)   # <class 'str'> (클래스 확인)
 
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
 >>> hello = '안녕'   # hello 문자열 타입 변수 선언
 >>> hello
 '안녕'
 >>> id(hello)       # hello 객체 식별자 확인
 59263440
 >>> hello = '반가워' # hello 변수 값 변경
 >>> hello
 '반가워'
 >>> id(hello)       # hello 객체 식별자 확인(변경)
 59263328
```
 
 - hello 라는 변수에 새로운 값을 할당했을 때, 같은 객체에 값만 변경할 것이라고 생각할 수 있지만, 파이썬에서는 변할 수 없는(Immutable) 데이터 타입에 새로운 값을 대입하면 **새로운 객체를 생성하여 그 객체를 연결**
 - 변할 수 있는(Mutable) 데이터 타입의 예는 리스트 타입이 있음
 
```python3
 >>> hello_list = ['안녕!']    # 리스트 타입 선언
 >>> hello_list
 ['안녕!']
 >>> id(hello_list)            # 리스트 객체 식별자 확인
 59201736
 >>> hello_list[0] = '반가워!' # 리스트 첫 번째 항목 값 변경하기
 >>> hello_list
 ['반가워!']
 >>> id(hello_list)            # 리스트 객체 식별자 확인(동일)
```

## 데이터 구조
 - 데이터를 활용 방식에 따라 조금 더 효율적으로 이용할 수 있도록 컴퓨터에 저장하는 여러 방법

### 리스트 타입
 - 리스트 타입 데이터는 자동으로 색인(index)가 생김(0부터 시작해서 정수 형태로 증가)
 - 리스트 타입은 값을 변경할 수 있는(Mutable) 데이터 타입
 - append(), remove(), insert(), pop() 함수 등 존재
 - 변수명[start:end] 로 슬라이싱 : 리스트 타입 변수의 start 색인부터 end-1 색인까지 자름
 - 변수명[:]처럼 양쪽 모두에 숫자가 없는 경우 => '복사' 용도
 - 리스트를 +, extend()로 합칠 수 있음(+는 새로 객체 생성, extend()는 기존 객체에 추가) => **객채를 새로 생성할 필요가 없는 상황이라면 리스트를 확장(extend)하는 것이 메모리를 효율적으로 사용**하는 방법 중 하나
 - https://docs.python.org/3.7/tutorial/datastructures.html#more-on-lists
 - 동일 리스트에 서로 다른 데이터 타입을 넣을 수 있음
 - 중첩 리스트 가능 => 행렬 등 표현 가능
 - 파이썬의 문자열 타입 데이터는 자동으로 각 글자에 색인이 매겨짐 => 문자열은 Immutable이기 때문에 글자[0] = 'a' 처럼 변경 불가
 
### 튜플 타입
 - **변경할 수 없는(Immutable) 리스트 타입'
 - 리스트 타입은 일반적으로 동일한 데이터 타입으로 이루어진 항목을 리스트 내에서 순차적으로 추출하는 용도로 사용
 - 튜플 타입은 서로 다른 종류의 데이터 타입으로 이루어진 항목들을 변수에 바로 풀어 쓰는 언패킹 혹은 색인을 매기는 용도로 사용
```python3
  >>> movie = '슈퍼맨', 1980, '배트맨', 1989 # 튜플 생성, 소괄호 생략 가능
  >>> movie
  ('슈퍼맨', 1980, '배틑맨', 1989)
  >>> movie[1] = 1982                       # 형 오류 발생, Immutable
```
 - 빈 튜플 혹은 항목이 하나 있는 튜플 생성 시 주의 사항
```python3
 empty = ()            # 빈 튜플 생성
 empty = tuple()       # 빈 튜플 생성
 singleton = ('안녕',) # 항목이 하나 있는 튜플 생성, 쉼표(,) 필수 입력


 movie = '슈퍼맨', 1980, '배트맨', 1989 # 패킹
 a, b, c, d = movie                    # 언패킹
```
 - 튜플 타입은 리스트 타입에 비해 제공하는 메소드나 기능에 제약이 많음. 이런 단순함은 성능에 이점을 가져옴
 - **열거형 데이터에 대해 변경할 필요가 없다고 판단이 되면 튜플 타입을 사용하는 것이 리스트를 사용하는 것보다 더 성능이 좋은 프로그래밍을 하는 방법**

### 세트 타입
 - **색인에 의한 순서가 없으며 중복이 허용되지 않는 데이터들의 집합**
 - 빈 세트 타입은 반드시 set() 함수로만 가능 => 중괄호({})는 딕셔너리 문법과 중복되기 때문
 - 수학 집합에서의 합집합, 교집합, 차집합, 여집합 등을 구하는 데도 유용하게 사용

### 딕셔너리 타입
 - **전체 항목이 정렬되지 않은 키와 값의 쌍으로 구성된 집합**
 - keys(), sorted(), values() 등 함수 존재

### 제어문과 자료구조의 조합(Comprehensions)
 - 파이썬은 문법들간의 조합을 통해 다소 복잡할 수 있는 소스 코드를 쉽고 간결하게 만들어 줌

```python3
 squares = []
 for x in range(10):
  squares.appned(x**2)
 
 # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
 # 위 내용을 간단히 표현하면
 
 new_squares = [ y**2 for y in range(10) ]
 # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
 
 # 위의 예시에서 x는 마지막 루프의 값이었던 9를 보유한 채 변수가 프로그램 내에 남아있음
 # 임시로 사용했던 변수임에도 메모리 내에 상주
 # 반면에 y는 메모리를 반환
```
 
 - 아래와 같이 조금 더 복잡한 표현도 가능
 
 ```python3
  pairs = []
  A = ['blue', 'yellow', 'red']
  B = ['red', 'green', 'blue']
  
  for a in A:
   for b in B:
    if a != b:
     pairs.append( (a, b) )
 
  # 위 for문을 아래와 같이 표현 가능
  new_pairs = [ (a, b) for a in A for b in B if a != b ]
 ```

### 함수 정의하기
 - 함수를 만들기 위해 사용하는 예약어는 def
 - 함수명에는 파이썬의 예약어를 사용할 수 없음
 - 함수 종료 시에 반환 값이 있는 경우 return 예약어 사용

```python3
# 기본 인자 값 활용
# 함수 호출 시에 매개 변수를 넘기지 않으면 error 발생
def daily_sleeping_hours(hours):
 return hours

# 매개 변수를 표기할 때 아래와 같이 기본값을 줄 수 있음
def daily_sleeping_hours(hours=7):
 return hours

# 여러 개의 인자 값 및 키워드 인자 활용
# 함수 호출 시 반드시 대입해야 하는 필수 인자 값이 있고, 값을 대입하지 않는 경우 기본값을 할당하는 옵션 인자 값이 있음
# 두 타입의 인자 값이 공존하는 형태의 함수를 정희할 수 있고 이를 'positional-or-keyword'라고 부름
# 아래 함수는 첫 번째 인자 값은 필수, 나머지는 옵션으로 입력하지 않을 경우 기본값이 할당
def introduce_my_car(manufacture, seats=4, type='sedan'):
 print('내 차는', manufacture, '의', seats, '인승', type, '이다.')

# 키워드 인자 값 뒤에 키워드 없는 인자 값 사용 불가
>>> introduce_my_car(manufacture='현대',2) # SyntaxError

# 동일 매개 변수에 중복 인자 값 대입
>>> introduce_my_car('기아', manufacture='현대') # TypeError

# 알지 못하는 키워드
>>> introduce_my_car(color='회색') # TypeError
```
 
### 가변 인자 리스트 활용(Arbitary Argument Lists) 
 
 
