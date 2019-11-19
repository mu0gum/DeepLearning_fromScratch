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
 - 인자 값 여러 개를 하나의 변수에 담아서 전달하고자 한다면 별표 기호를 활용하면 가능
 - 별표 한 개는 튜플 타입, 두 개는 딕셔너리 타입 데이터를 의미
```python3
 def introduce_your_family(name, *family_names, **family_info):
  for family_name in family_names:
   print(family_name)
  
  for key in family_info.keys():
   print(key, ':', family_info[key])

# 인자 값의 개수나 키워드 없이도 나열한 값이 알아서 각 변수에 패킹되어 대입 -> var-positional
>>> introduce_your_family('Chris', 'Jihee', 'Anna', 'Shinhoo', 집='용인', 가훈='행복하게 살자')
```
 - 열거형 데이터를 집어 넣을 때 튜플을 사용하는 이유는 튜플은 값을 변경할 수 없는(immutable) 데이터 타입이기 때문
 - 개발 시 발생할 수 있는 혼돈을 줄이는 데 기여
 
### 언패킹 인자 리스트 활용

```python3
# 일반적으로 값을 2개 따로 대입
>>> list(range(3, 6))
[3, 4, 5]

# 리스트 타입 데이터를 언패킹하여 대입
>>> args = [3, 6]
list(range(*args))
[3, 4, 5]
```
 -	&#42;args를 통해 하나의 리스트 타입 데이터가 두 개의 숫자인 3과 6으로 나눠짐
 - **파이썬에서의 별표 기호는 데이터를 패킹할지, 언패킹 할지를 결정해 주는 역할을 함**
 - 매개 변수에 있는 별표 기호는 인자값으로 들어오는 항목들을 패킹하겠다는 의미, 인자 값에 있는 별표는 인자 값을 언패킹 하여 대입 하겠다는 의미
 - 딕셔너리 타입을 위한 언패킹은 별표 기호 두개(&#42;&#42;)를 사용
 
### 변수의 유효 범위(scope)
 - 대부분 프로그래밍 언어에는 **변수를 사용할 때 해당 변수가 영향을 미치는 영역**이 존재
 - 이 영역을 변수의 유효 범위(scope)라고 함
 - 함수에 선언한 변수는 일반적으로 함수 내에서만 사용이 가능하며 함수 밖에서는 사용에 제약이 있음
 
```python3
 def my_func(param):
  param = 'Modified by my_func'
  print(param)
  print(id(param))

>>> param = 'Create from outside'
>>> my_func(param)

Modified by my_func
60492296

>>> print(param)

Create from outside
60492368
```
 
 - 위 코드의 2번째 줄에서 param 매개 변수의 값을 변경하는 것이 아니라 함수 내애서만 사용이 가능한 param 변수를 새로 생성
 - 함수 내에서만 활용이 가능한 변수를 지역 변수(Local Variable)이라고 함
 - 함수 밖에서 선언한 변수를 함수 내에서 활용하고 싶을 때는 global 예약어를 사용

### 함수 설명을 위한 문자열 활용
```python3
 def my_function():
  """아무 것도 하지 않지만, 문서만 기술한 함수
  
  
  """
  pass

# __doc__ : 파이썬의 함수에서 docstring을 기술하면 자동으로 해당 내용을 호출할 수 있게 해주는 내장 변수
>>> prnit(my_function.__doc__)

아무 것도 하지 않지만, 문서만 기술한 함수 
```

### 클래스
 - 파이썬의 모든 것은 객체로 이루어져 있으며 클래스는 이객체를 만들기 위한 일종의 명세

```python3
>>> var = '파이썬 객체 지향 이야기'
>>> id(var)
6070164
>>> type(var)
<class 'str'>

# str 확인
>>> str 
<class 'str'>
# str의 타입 확인
>>> type(str)
<class 'type'>
# str의 식별자 확인
>>> id(str)
1741994512
```
 - 클래스 역시 파이썬에서는 하나의 객체
 - 'str'이라는 클래스는 파이썬의 'type'이라는 클래스의 객체
 - 'type'클래스 역시 'type'이라는 클래스의 객체
 - 클래스에서 생성된 객체를 인스턴스라고 함
 - 클래스에는 객체의 상태 및 행동을 정의하는 지역 변수인 속성과 내장 함수인 메소드가 존재

```python3
# 어떤 클래스(타입)에 의해 생성이 되었는지를 담고 있는 지역 변수
>>> var.__class__ 
<class 'str'>
# 문자열 타입 클래스에 내장되어 있는 함수
>>> var.replace('파이썬', 'Python')
'Python 객체 지향 이야기'
```
 - 클래스에 속해 있는 지역 변수를 속성이라고 함
 - 클래스에 속해 있는 내장 함수는 메소드라고 함

### 클래스 정의 및 불러 오기
```python3
 class BookReader:
  name = str()
  
  # self -> 본인의 객체를 인자 값으로 넘김으로써 함수 내에서 클래스의 속성 및 메소드에 접근할 수 있게 해 줌
  def read_book(self):
   print(self.name  + ' is reading Book!')
 
```

### 클래스 초기화 함수 __init()__ 재정의
 - 위의 소스 코드에서 이름이 없는 사람을 만들 필요는 없어 보여 인스턴스 생성시에 반드시 이름을 인자 값으로 집어넣게 하고 싶음
 - 이럴 때를 위해 객체 인스턴스화를 위한 특수 함수가 존재 -> __init()__

```python3
 class BookReader:
 
  # 초기화 함수 재정의(Overriding)
  def __init__(self, name):
   self.name = name
  
  def read_book(self):
   print(self.name  + ' is reading Book!')
   
# 아래와 같이 인자값이 없는 경우 에러 발생
>>> reader = BookReader()

# 객체 생성
>>> reader = BookReader('Chris')
>>> reader.read_book()
Chris is reading Book!
```

### 클래스 변수와 인스턴스 변수
 - 변수 선언 위치에 따라 유효 범위가 달라짐
 
```python3
class BookReader:
 country = 'South Korea'
 def __init__(self, name):
  self.name = name
 def read_book():
  print(self.name  + ' is reading Book!')
  
  
>>> reader1 = BookReader('Chris')
>>> reader2 = BookReader('Anna')
>>> reader1.country
'South Korea'
>>> reader2.country
'South Korea'
>>> reader1.read_book()
'Chris is reading Book!'
>>> reader2.read_book()
'Anna is reading Book!'
```
 - country 처럼 클래스에 선언된 속성은 클래스 변수라고 하며 이 클래스에 의해 생성된 모든 객체가 인스턴스화되는 시점에 같은 값을 조회할 때 사용 가능
 - 반면 name은 클래스의 변수 형태로 선언한 것이 아니고, 객체가 인스턴스화 될 때마다 새로운 값이 할당되어 서로 다른 객체 간에는 값을 공유할 수 없음. 이런 변수를 인스턴스 변수라고 함 => 객체 단위로 변경이 되는 변수는 반드시 인스턴스 변수로 선언하여 사용
 - 클래스 변수에 변할 수 없는(immutable) 데이터 타입(예: 문자열 타입)을 쓰는 경우에도 새로 변경한 값을 다른 객체가 공유할 수 있을까? => 없다(변할 수 없는 데이터 타입은 변경을 시도하는 순간 새로운 객체가 생성되고 이 객체는 변수를 가지고 있는 객체 내에서만 접근 가능)
 - 변수의 선언 위치에 따라 값을 변경할 수 있는 유효 범위가 다르기 때문에 신중하게 코드를 작성해야 함

### 데이터 은닉(Data Hiding)과 이름 장식(Name Mangling)
```python3
# BookReader 클래스 선언
class BookReader:
 # 클래스 변수 country 선언
 country = 'South Korea'
 
# BookReader 클래스 내부 확인
>>> dir(BookReader)
['__class__', '__delattr__', '__dict__', ...  , 'country'] # 맨 마지막에 country 확인 가능
```
 - 위와 같은 country 변수는 너무 쉽게 접근하거나 수정할 수 있음
 - 심지어 해당 클래스의 인스턴스를 생성하지 않더라도 수정할 수 있음 (예, BookReader.country = 'USA' )
 - 큰 문제가 아니라고 생각할수도 있지만 클래스 변수로 쉽게 변경할 수 없는 값을 집어 넣었는데 아무나 이 값을 쉽게 변경할 수 있다면 이 변수에 대한 신뢰도는 떨어지기 마련
 - 이런 사유로 객체 지향 언어에서는 은닉과 캡슐화라는 개념을 사용(이런 데이터는 외부에 노출하지 말고 숨기자는 의도)
 - 하지만 **파이썬에서는 이를 위한 강력한 도구를 제공하고 있지는 않음** (예, 자바의 private)
 - 대신 **파이썬에서는 변수명 앞에 언더스코어 두 개(__)가 있는 것에 한하여 이름을 변경해 버리는 이름 장식 기법을 제공**
 
```python3
# BookReader 클래스 선언
class BookReader:
 # 클래스 변수 country 선언(이름 장식)
 __country = 'South Korea'
  
# BookReader 클래스 내부 확인
>>> dir(BookReader)
['_BookReader__country', '__class__', ...  , '__weakref__'] # 첫 번째 항목에 변형된 변수명을 확인할 수 있음
```
 - 이렇게 변형된 변수는 기존 변수명으로 값을 확인할 수 없게 됨
 - 물론 다른 언어와 같이 아예 접근이 불가한 것은 아님 ( '_BookReader__country' 로 접근 가능 )
 - 하지만 의도적으로 접근하는 경우는 극히 드뭄
 - 이런 클래스 변수는 수정하기 위해서 클래스 안에 이 변수를 수정하기 위한 메소드를 선언하여 호출하는 방식을 활용하는 것이 좋음
 
```python3
# BookRader 클래스 선언
class BookReader:
 # 클래스 변수 country 선언(이름 장식)
 __country = 'South Korea'
 
 def update_country(self, country):
  self.__country = country
 
 def get_country(self):
  return self.__country
```
 - 위와 같이 필요한 메소드를 명확하게 선언하고, 메소드명에 하고자 하는 행위를 표기하고 나면 실제로 해당 메소드가 호출이 되었을 때 개발자의 의도를 더욱 명확하게 확인 가능
 
### 상속(Inheritance)
 - 객체 지향 언어에서의 상속은 말 그대로 부모 클래스가 자식 클래스에게 무언가를 물려 주는 것
 - 파이썬에서는 부모 클래스를 베이스 클래스(Base Class), 자식 클래스는 파생 클래스(Derived Class)라고 부름
 - **상속은 중복 코드를 최소화 함과 동시에 클래스 간의 계층 관계를 형성하여, 현실 세계와의 괴리를 줄이기 위해서 나온 개념이라고 볼 수 있음**
 
 
 
 
 
 
