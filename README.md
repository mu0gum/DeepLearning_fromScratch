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
 - **변경할 수 없는(Immutable) 리스트 타입**
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

```python3
# Human 클래스 선언
class Human:
 
 # 클래스 변수 country 선언
 country = 'South  Korea'
 
 # 초기화 함수 재정의
 def __init__(self, name):
  self.name = name
  
# Human의 자식 클래스인 BookReader 클래스 선언
class BookReader(Human):
 def read_book(self):
  print(self.name + ' is reading book.'
  
# Human의 자식 클래스인 DrumPlayer 클래스 선언
class DrumPlay(Human):
 def play_drum(self):
  print(self.name + ' is playing drum.'
  

>>> br = BookReader('Chris')
>>> br.country
'South korea'

>>> br.read_book()
'Chris is reading book.'

>>> dp = DrumPlayer('Sean')
>>> dp.country
'South Korea'

>>> dp.play_drum()
'Sean is playing drum.'
```
 
 - 자식 클래스는 생성할 때 부모 클래스를 선언해 줘야 함 > 클래스 명 뒤에 중괄호 기호를 활용하여 부모 클래스 명을 넣음
 - BookReader 내부에서는 __init__() 함수가 재정의되지 않았지만 부모 캘르시인 Human으로부터 재정의 된 __init()__ 함수를 물려받아 사용
 - 상속은 코드의 재사용성을 높이고 중복되는 소스 코드를 줄이는 데 크게 기여
 - 클래스인지 인스턴스인지를 확인하려면 __class__ 속성 값을 확인. 부모 클래스인 베이스 클래스를 확인하기 위해서는 __bases__ 속성 값 확인
 - 모든 클래스의 부모 클래스는 object 클래스
 
```python3
>>> Human.__bases__
(<class 'object'>,)
```
 
 - 부모 클래스 호출시 base의 복수형인 bases를 사용하고 있고, 결과 값에는 튜플 타입에 마지막에 쉼표가 붙어 있음 > 이는 부모 클래스가 한 개가 아닌 여러 개가 될 수도 있는 것임을 암시

```python3
# Developer 부모 클래스 선언
class Developer:
 # coding 메소드 선언
 def coding():
  print(self.name + ' is developer.')

class ProgramBookWriter(Human, Developer):
 def write_book(self):
  print(self.name + ' is writing book')
```
 
 - 위 처럼 여러 클래스를 하나의 자식 클래스가 상속 받는 것을 다중 상속이라고 함 > 다중 상속은 모든 프로그래밍 언어가 제공하는 것은 아님 ( C++은 가능, 자바는 불가능 등)


### 다형성(polymorphism)
 - 부모 클래스와 동일한 이름의 메소드를 그대로 자식 클래스에서 구현하여 재정의(Overriding)하는 것을 다형성(polymorphism)의 구현이라고 함
 
```python3
# Developer 부모 클래스 선언
class Developer:
 # 초기화 시 name을 받기 위한 재정의
 def __init__(self, name):
  self.name = name
 
 # coding 메소드 선언
 def coding(self):
  print(self.name + ' is developer')

class PythonDeveloper(Developer):
 def coding(self):
  print(self.name + ' is Python Developer.')

class JavaDeveloper(Developer):
 def coding(self):
  print(self.name + ' is Java Developer')
```
 
 - 다형성 역시 객체 지향의 중요한 특성 중 하나
 - 다형성의 구현을 위하여 부모 클래스에 있는 메소드를 재정의하고 나면 부모 클래스의 메소드는 실행이 되지 않음
 - 하지만 어떤 경우에는 부모 클래스의 메소드에 덧붙여서 소스 코드를 확장하고 싶은 경우도 분명 생김
 - 이 때, 부모 클래스 내용을 Copy & Paste 하는 것은 또 다른 소스 코드 중복을 야기할 수 있음
 - 이런 경우를 위하여 파이썬은 부모 클래스 호출을 위해 super()라는 함수를 제공

```python3
# CPPDeveloper 부모 클래스 선언
class CPPDeveloper(Developer):
 def coding(self):
  super().coding()
  print(self.name + ' is C++ Developer.')
```

 - 이런 식의 super() 클래스 호출은 초기화 함수 호출시에도 많이 사용

### 모듈(module)
 - 모듈은 재사용을 하고자 하는 변수나 함수의 정의문들을 파일로 저장하여 특정 파이썬 파일이나 파이썬 쉘 환경에서 호출하여 사용할 수 있는 방법을 제공
 - 그리고 이러한 모듈들을 기준에 따라 모아 놓은 단위를 패키지(package)라고 부름
 - print(), input(), range() 등은 모두 파이썬 기본 내장 함수로 특별한 모듈을 호출할 필요 없이 언제든지 호출하여 사용 가능
 - 이런 기본 내장 함수를 제외한 함수들은 파이썬 표준 라이브러리 안의 모듈에 구현이 되어 있으며 사용하기 위해 모듈을 미리 호출하여 해당 모듈을 파이썬 실행 환경에 탑재(import) 해야 함

### 모듈 정의 및 불러 오기
 - 모듈은 파이썬으로 정의한 소스 코드를 담고 있는 파일
 - py 확장자로 끝나야 하고 파일명은 곧 모듈명
 - 피보나치 수를 구하는 두 개의 함수를 작성하여 모듈용 파일러 만들어 보면 아래와 같음
 
```python3
# fibo.py

# n까지의 피보나치 수열을 출력하는 함수
def fb(n):
 a, b = 0, 1
 while b < n:
  print(b, end= ' ')
  a, b = b, a + b
  print()

def fb2(n):
 result = []
 a, b = 0, 1
 while b < n:
  result.append(b)
  a, b = b, a + b

# IDLE
>>> import fibo
>>> fibo.fb(20)

1 1 2 3 5 8 13

# 함수가 번번히 호출되어 매번 모듈명을 적는 것이 번거롭다면 fibo.fib 함수 자체를 변수에 할당하여 호출 하는 것도 가능
>>> fib = fibo.fib
>>> fib(50)

1 1 2 3 5 8 13 21 34
```
 - 함수 자체도 객체이기 때문에 변수에 할당이 가능
 - type() 함수로 확인해보면 > <class 'function'>
 - 모듈 안의 함수를 함수명으로만 활용하고 싶다면 매번 변수에 할당하지 않고 import 문을 아래와 같이 사용하면 함수를 바로 import 할 수 있음
 
```python3
# from 뒤에 모듈명을 명시하고, import 뒤에 함수명을 명시
>>> from fibo import fib, fib2
>>> fib(500)

1 1 2 3 5 8 13 21 34 55 89 144 233 377

# 모듈을 호출할 때 별칭(alias) 사용 가능
>>> from fibo import fib as f1, fib2 as f2

# 별표(*) 기호를 활용하면 모듈 안의 모든 함수 import 가능
# 사용은 가능하지만 좋은 방법은 아님 > 모듈내의 어떤 함수를 호출할지 모르기 때문에 가독성을 떨어뜨리고 간혹 함수명의 중복으로 인해 원하는 않는 동작을 할 가능성이 높아짐
>>> from fibo import *
```

### 모듈들의 집합 패키지(package)
 - 위에서 만든 fibo 라는 모듈을 chris 라는 폴더 아래에 옮긴다고 가정
 - fibo.py 라는 모듈은 chris 아래 패키지에 위치하게 된 것 호출 방법은 점 기호(.)를 활용
 
```python3
>>> from chris.fibo import fib
>>> fib(100)
```
 - 패키지는 관련 깊은 소스코들을 모아서 알아보기 쉽게 하고, 관리 및 유지보수 역시 쉽게 하기 위함
 - 일반적으로 패키지를 나눌 때에는 소스 코드의 사용 목적에 따라서 나누는 것이 현명
 - from 문과 import 문이 함께 사용하는 경우 import 문은 뒤의 항목은 패키지의 서브 모듈이나 서브 패키지, 패키지 내에 구현되어 있는 함수나 클래스, 변수 등이 올 수 있음. 또한 from 문 없이 사용하는 경우에는 마지막 항목이 모듈이나 패키지가 되어야 


### 포맷을 위한 문자열 타입 메소드 format()
 - 표준 출력문의 형태는 무척이나 다양하고, 출력되는 내용들은 소스 코드를 작성하는 개발자나 사용자에게 친숙하면서도 보기 좋아야 할 것
 - format()의 활용
 
```python3
# 문자열 중간의 중괄호 기호({})는 문자열 타입 메소드인 format() 함수와 함께 사용
>>> print('Hello, {}!'.format('Chris')) # str.format() 사용 예제
Hello, Chris!

>>> name = input('이름을 입력하세요! ')
이름을 입력하세요! Chris
>>> job = input('직업을 입력하세요! ')
직업을 입력하세요! Programmer
>>> print('{} is a {}.'.format(name, job))
Chris is a Programmer.

# 중괄호 안에 인자 값의 인덱스(순서)가 들어 갈 수 있음
>>> print({0} is a {1}.'.format(name, job))
Chris is a Programmer.

# 인자 값의 순서를 바꿔서 출력하고 싶은 경우에는 아래와 같이 바꾸는 것도 가능
>>> print('Good {1}. {0}.'.format(name, job))
Good Programmer. Chris.

# 정수 타입 인덱스뿐만 아니라 변수명을 활용하여 표현하는 방법도 있음
>>> print('Good {j}. {n}.'.format(n=name, j=job))
Good Programmer. Chris.

# 인덱스 형과 변수명을 함께 사용할 수도 있음
>>> print({0} is a {lang} {1}.'.format(name, job, lang='Python')
Chris is a Python Programmer.
```
 
### 다양한 포맷에 대한 예제
 - 문자열이나 튜플, 리스트 형 데이터들을 자동으로 언패킹하여 값을 출력할 수 있음
 - format()의 인자 값으로 대입할 때 별표 기호를 앞에 붙여 주면 됨

```python3
>>> '{0}-{1}-{2}'.format(*'ABC')
'A-B-C'
>>> '{0}-{1}-{2}'.format(*['A', 'B', 'C'])
'A-B-C'

# 인자 값의 색인과 중괄호 기호([])를 활용하여 튜플이나 리스트, 사전 형의 항목을 추출할 수 있음
>>> '{0[0]}-{0[1]}-{0[2]}'.format(['A', 'B', 'C']) # 리스트 타입 예제
'A-B-C'
>>> '{0[name]}'.format({'name':'Chris', 'family-name':'Cho'}) # 사전 타입 예제
'Chris'
```
 - 메소드 format()에는 좌측, 우측, 중앙 정렬을 위한 기능도 제공

```python3
>>> '{:<20}'.format('좌측 정렬')
'좌측 정렬               '
>>> '{:>20}'.format('우측 정렬')
'               좌측 정렬'
>>> '{:^20}'.format('중앙 정렬')
'       중앙 정렬        '
>>> '{:%^20}'.format('중앙 정렬') # 중앙 정렬 후 빈칸은 %로 채움
'%%%%%%%중앙 정렬%%%%%%%%'
```
 - 콜론 기호(:)는 글자 포맷을 명시하겠다는 의미
 - 중괄호 안의 숫자는 출력 결과의 전체 길이

```python3
>>> import path #math 모듈 호출
>>> print('원주율의 크기는 대략 {:f} 입니다.'.format(math.pi))
원주율의 크기는 대략 3.141593 입니다.
>>> print('원주율의 크기는 대략 {:.2f} 입니다.'.format(math.pi)) # 소수점 둘째자리까지만 출력
원주율의 크기는 대략 3.14 입니다.

>>> '{:+f}; {:+f}'.format(3.14, -3.14) # +, - 기호 항상 출력
'+3.140000; -3.140000'
>>> '{: f}; {: f}'.format(3.14, -3.14) # + 기호는 공백으로, - 기호만 출력
' 3.140000; -3.140000'
>>> '{:-f}; {:-f}'.format(3.14, -3.14) # - 기호만 출력, {:f}; {:f}와 같음
'3.140000; -3.140000'

>>> '정수: {0:d}; 16진수: {0:x}; 8진수: {0:o}; 2진수: {0:b}'.format(50)
'정수: 50; 16진수: 32; 8진수: 62; 2진수: 110010'

>>> '정수: {0:d}; 16진수: {0:#x}; 8진수: {0:#o}; 2진수: {0:#b}'.format(50) # 접두사 사용하기
'정수: 50; 16진수: 0x32; 8진수: 0o62; 2진수: 0b110010'

>>> '{:,}'.format(10000000) # 숫자 구분자 표기 하기
'10,000,000'

>>> '{:%}'.format(5/12) # 백분율 사용
'41.666667%'
>>> '{:.2%}'.format(5/12) # 백분율에 소수점 제약
'41.67%'
```
 - printf-style 문자열 포맷은 더 이상 사용하지 말 것 (반드시 str.format() 함수를 사용하기를 권장)
 - 파이썬 3.6에서 등장한 f-string이 인기를 끌고 있음
 - 기존 방식 : 'Hello, { }'.format(name)
 - f-string 방식 : f'Hello, {name}' 
 
### 로깅(logging)의 이해
 - 로깅이란 소프트웨어가 실행될 때 일어나는 이벤트들을 추적하기 위한 용도로 소스 코드에 집어 넣는 출력문을 작성하는 행위
 - 이러한 출력문을 로그라고 부르고 일반적으로 별도의 파일에 저장되어 체계적으로 관리
 - 로그 레벨 DEBUG > INFO > WARNING > ERROR > CRITICAL

### 로깅 라이브러리 사용법
 - 파이썬의 기본 라이브러리는 로깅을 하기 위한 모듈인 logging 모듈을 제공
 
```python3
>>> import logging # logging 모듈 탑재
>>> logging.warning('조심하세요!') # WARNING 메세지 출력
WARNING:root:조심하세요!
>>> logging.info('정보 확인 하세요!') # INFO 메세지 출력 되지 않음

```

 - 첫 번째는 로그 레벨인 WARNING 이 출력, 두 번째는 로거의 정보가 출력 > 로거란 logging 모듈 안에 탑재되어 있는 객체로 로깅을 하는 주체
 - 파이썬의 기본 로거가 'root'
 - 위에서 info가 출력되지 않은 이유는 파이썬의 기본 로거인 root의 로그 레벨이 WARNING 이기 때문
 
```python3
>>> logging.root.setLevel(logging.DEBUG) # 로그 레벨 변경 WARNING > DEBUG
>>> logging.info('정보 확인 하세요!') # INFO 메세지 출력
INFO:root:정보 확인 하세요!
```
 - 로깅 모듈을 사용하면 로그 레벨에 따라서 수준에 맞는 로그가 출력
 - 로깅 모듈에는 서로 역할이 다른 객체들을 제공하여 로깅의 역할을 수행
 - 로거(logger) : 소스 코드에 바로 호출하여 사용할 수 있는 인터페이스 제공. 일반적으로 파이썬 모듈 단위로 로거를 생성하며 최상단에 root 로거 밑으로 부모 자식 관계를 형성. 모든 로거는 root 로거의 자식
 - 핸들러(handler) : 로거에 의해 생성된 로그 레코드(LogRecord)를 적절한 곳에 출력. 로그는 콘솔이나 파일, 데이터베이스 등에 저장할 수 있음. 로거는 여러 개의 핸들러를 보유할 수 있고, 핸들러는 반드시 특정 로거에 귀속
 - 포매터(formatter) : 로그의 출력 포맷을 결정
 - 로그 레코드 역시 또 하나의 객체이며, 로그 한 줄이 생길 때마다 생기는 객체(로거의 이름, 로그 레벨, 로그를 발생시킨 소스코드의 위치 등 정보를 가지고 있음)
 - 로거는 아래와 같이 생성 혹은 획득할 수 있음
 
```python3
>>> logger = logging.getLogger(__name__) # 로거 획득
>>> logger.warn('곧 문제가 생길 가능성이 높습니다.') # WARNING 로그 출력
WARNING:__main__:곧 문제가 생길 가능성이 높습니다.
```
 - 로거는 자체적으로 인스턴스를 생성할 수 없음
 - 인자 값으로는 로거의 이름을 결정하는 어떠한 문자열을 집어 넣어도 상관 없으나, 파이썬 커뮤니티에서는 모듈 단위의 로거를 생성하여 사용하기를 권고 > 따라서 인자 값에 모듈의 이름을 담고 있는 변수인 '__name__' 을 넣어 줌

```python3
# 로깅 모듈 탑재
import logging

# 콘솔 출력용 핸들러 생성
handler = logging.StreamHandler()

# 포매터 생성
formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')

# 핸들러에 포매터 설정
handler.setFormatter(formatter)

# 로거 생성 및 로그 레벨 설정, 핸들러 추가
logger = logging.getLogger(__name__)
logger.setLevel(logging.INFO)
logger.addHandler(handler)

# 로그 메세지 출력
logger.debug('이 메세지는 개발자만 이해해요.') # DEBUG 로그 출력
logger.info('생각대로 동작하고 있어요.') # INFO 로그 출력
logger.warn('곧 문제가 생길 가능성이 있습니다.') # WARNING 로그 출력
logger.error('문제가 생겼어요. 기능이 동작 안해요.') # ERROR 로그 출력
logger.critical('시스템이 다운됩니다!!') # CRITICAL 로그 출력
```
 
 - 퍼센트 기호(%)로 시작하여 괄호 안에 특정 항목 값이 보이고, 괄호 뒤에 소문자 s가 보이는 문자들로 이루어져 있음
 - 퍼센트 기호는 일종의 특수 기호로 로그 레코드의 속성들을 호출하겠다는 의미
 
### 로그 레벨 설정에 관한 팁
 - 로그 레벨은 root 로거나 특정 로거, 핸들러 등에 모두 설정이 가능하여 다소 혼란스러움. 아래와 같은 방법 권유
 1) root 로거의 로그 레벨은 기본 값을 DEBUG나 NOTEST로 세팅하여 모든 로그를 출력할 수 있게 설정
 2) 로그 레벨을 제어하고 싶은 단위로 로거를 생성. 대부분 모듈이나 패키지 단위로 작성. 로그 레벨은 로거에 직접 설정
 3) 핸들러는 콘솔이나 파일에 로그를 출력하고, 로거들이 공유할 수 있기 때문에 핸들러에는 로그 레벨 설정을 하지 않음. 이는 곧 기본값인 NOTEST로 세팅을 한다는 의미. 그리고 원하는 로거에 추가하여 로거에 세팅되어 있는 로그 레벨을 따라 가게 함.
 
### 설정 파일을 활용한 로깅
 - 파이썬에서 자체적으로 정의한 '파일 설정(FileConfig)' 파일을 생성 > 소스코드와 동일한 위치에 저장
 - 확장자는 보통 conf, ini, properties 등으로 설정
 
```python3
# logging.conf
[loggers]
key=root, infoLogger

[handlers]
keys=simpleHandler

[formatter]
keys=simpleFormatter

[logger_root]
level=NOTEST
handlers=

[logger_infoLogger]
level=INFO
handlers=simpleHandler
qualname=__name__
propagate=1

[handler_simpleHandler]
class=StreamHandler
formatter=simpleFormatter
args=(sys.stdout,)

[formatter_simpleFormatter]
format=%(asctime)s - %(name)s - %(levelname)-8s - %(message)s
datefmt=
```
 - 1~8번째 라인까지는 파일에서 설정할 로거와 핸들러, 포매터의 이름을 설정
 - 대괄호 기호, keys라는 용어는 약속된 양식이기 때문에 지켜야 함
 - root는 모든 로거의 부모이므로 반드시 기술되어야 함

```python3
import logging # 로깅 모듈 탑재
import logging.config # 로깅 설정 모듈 탑재

# 설정 파일 읽어 오기
logging.config.fileConfig('logging.conf')

# 로거 생성
logger = logging.getLogger(__name__) # 로거 생성

# 로그 메세지 출력
logger.debug('이 메세지는 개발자만 이해해요.') # DEBUG 로그 출력
logger.info('생각대로 동작하고 있어요.') # INFO 로그 출력
logger.warn('곧 문제가 생길 가능성이 있습니다.') # WARNING 로그 출력
logger.error('문제가 생겼어요. 기능이 동작 안해요.') # ERROR 로그 출력
logger.critical('시스템이 다운됩니다!!') # CRITICAL 로그 출력
```
 - 위 처럼 설정할 경우 소스 코드가 변경될 가능성을 줄이고, 설정 부분이 변경되면 소스 코드 수정 없이 설정 파일의 값만 수정하면 됨
 - 위의 예제는 콘솔 화면에 출력하는 예제이고, 파일에 저장하기 위해서는 아래와 같이 파일 핸들러(FileHandler)
 
```python3
[handlers]
keys=simpleHandler,fileHandler

[handler_fileHandler]
class=FileHandler
formatter=simpleFormatter
args=('python.log', 'w')
```
 
### 구문 에러(Syntax Error)
 - 문법 오류로 인해 소스 코드를 실행 하기 전에 발생하는 에러
 
```python3
>>> print 'Hello, world!' # print() 함수의 괄호 누락 예시
SyntaxError: Missing parentheses in call to 'print'

>>> if 1 > 0 # : 누락 예시
SyntaxError: Invalid syntax
```

### 예외(Exception)
 - 소스 코드 실행 중에 에러가 발생하는 경우 이를 통칭해서 예외라고 함
 - 파이썬은 다양한 유형의 에러를 미리 정해놓고, 데이터 타입과 같이 에러 타입을 정희함
 - 파이썬에서 미리 정해 놓은 예외들을 Built-in Excceptions 라고 부름
   (https://docs.python.org/3/library/exceptions.html#exception-hierarchy)
 
### try-except 구문으로 예외 상황 제어하기
```python3
>>> def exception_test():
     print("[1] Can you add 2 and '2' in python?")
     print("[2] Try it~!", 2 + '2') # 예외 발생
     print("[3] It's not possible to add integer and string together.")
    
>>> exception_test()
[1] Can you add 2 and '2' in python?
Traceback (most recent call last): # 에러 메세지
...
...
```
 - 파이썬에서는 에러 발생 시 추적이 가능한 정보들을 표기한에러 메세지를 트레이스백 메세지 라고 부름
 - 소스 코드 실행 중 에러가 발생하면 프로그램은 중단되기 마련이고, 심각한 시스템 장애로 이어질 수 있음
 - 파이썬에서는 이런 예외 상황에 대한 처리를 위하여 try ~ except문을 제공

```python3
>>> def exception_test():
     print("[1] Can you add 2 and '2' in python?")
     try: # try문
      print("[2] Try it~!", 2 + '2') 
     except TypeError as err: # 예외 처리 > TypeError가 발생하면 해당 인스턴스를 err 변수에 넣으라는 뜻
      print('[2] TypeError : {}'.format(err)) 
     print("[3] It's not possible to add integer and string together.")
```
 - 트레이스백 메세지를 출력하고 싶을 때는 traceback 모듈을 호출해야 함

```python3
>>> import traceback
>>> def exception_test():
     print("[1] Can you add 2 and '2' in python?")
     try: # try문
      print("[2] Try it~!", 2 + '2') 
     except TypeError as err: # 예외 처리 > TypeError가 발생하면 해당 인스턴스를 err 변수에 넣으라는 뜻
      print('[2] TypeError : {}'.format(err)) 
      tracceback.print_exc() # 트레이스백 메세지 출력
     print("[3] It's not possible to add integer and string together.")
```
 - 만약 동일한 블록문에서 여러 개의 에러가 발생할 가능성이 있다면 해당 에러들을 튜플에 넣어서 except 구문에 넣을 수 있음
 - 어떤 에러가 발생할지 명확하지 않은 경우에는 에러명을 생략할 수도 있음

```
except (TypeError, NameError):
except:
```

### else와 finally 사용하기
 - 파이썬의 예외처리 방식에는 else라는 옵션 구문을 제공
 - 예외 상황이 발생하면 except 구문을 실행하고, 발생하지 않으면 else 구문을 실행

```python3
>>> def exception_test_2(file_path):
     try:
      f = open(file_path, 'r')
     except IOError:
      print('cannot open', file_path)
     else:
      print('File has', len(f.readlines()), 'lines') # 파일 라인 수
      f.close()
     finally:
      print('I just tried to read this file.', file_path)
```
 - 또 다른 예외처리 방식의 옵션 구문은 finally 구문
 - 예외 상황이 발생하든 발생하지 않든 간에 반드시 실행이 되어야 하는 소스 코드를 finally 블록문에 위치
 
### raise문과 사용자 정의 예외 
 - 파이썬에서는 다양한 Builts-in Exception을 정의해 놓았지만 이러한 에러들은 대부분 일반적인 용도로 사용
 - 의도적으로 본인이 만든 예외를 만들어야 한다면 예외 클래스를 새로 만들면 됨
 
```python3
class TooBigNumberError(Exception): # 예외 클래스 선언
 def __init__(self, val): # 초기화 메소드 재정의
  self.val = val # 인스턴스 변수 선언
 def __str__(self): # 에러 메세지 함수 재정의
  return 'too big number {}. Use 1~10!'.format(self.val)
```
 - 예외 클래스를 선언할 때, 인자값으로 반드시 'Exception'을 넣어야 함(상속)
 - 예외 클래스의 실행은 일반 클래스와는 다름
 - 예외 클래스의 실행을 위해 파이썬에서는 raise 구믄을 제공

```python3
>>> raise TooBigNumberError(15)
Traceback (most recent call last):
...
...
...
TooBigNumberError: too big number 15. Use 1~10!
```
