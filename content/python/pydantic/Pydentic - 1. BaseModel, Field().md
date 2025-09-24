---
tags:
  - pydantic
  - python
  - validation
  - BaseModel
  - Field
create: 2025-09-24 13:29:24
---
# 1. BaseModel 

## BaseModel 생성

```python
from pydantic import BaseModel, ValidationError

# 모델 생성 (BaseModel 상속)
class Person(BaseModel):
    name: str
    age: int

# 객체 생성
person = Person(name="홍길동", age=25)
print(type(person), person)
# <class '__main__.Person'> name='홍길동' age=25
```
### 자동 타입 변환
```python
product = Product(name="노트북", price="1500.99", quantity="15")
print(product)
print(f"price 타입: {type(product.price)}")  # <class 'float'>
print(f"quantity 타입: {type(product.quantity)}")  # <class 'int'>
```
- `"숫자"` 형태의 값은 자동으로 타입변환(*int*, *decimal*, *float*)
- `"문자열"` 형태의 값은 ValidationError 발생
### 딕셔너리 언패킹 사용
```python
# 딕셔너리 형태로 전달 가능
data = {"name": "노트북", "price": "1500.99", "quantity": "10"}
product = Product(**data)
print(product)
# name='노트북' price=1500.99 quantity=10
```

# 2. Field 정의와 조건

```python
from pydantic import BaseModel, Field

class Employee(BaseModel):

    name: str = Field(min_length=2, max_length=50) # 길이 제한

    age: int = Field(gt=0, le=120)

    salary: float = Field(gt=0, description="월 급여") # 양수, 설명 

    email: str = Field(pattern=r'^[^@]+@[^@]+\.[^@]+$') # 이메일 패턴

employee = Employee(

    name="김흥달",

    age=30,

    salary=50000000.0,

    email="Kim@email.com"

)

print(employee) # name='김흥달' age=30 salary=50000000.0 email='Kim@email.com'

try:

    bad_employee = Employee(

        name="김",           # 너무 짧음 (min_length=2)

        age=0,              # 0은 안됨 (gt=0)

        salary=-1000,       # 음수 안됨

        email="invalid"     # 이메일 형식 아님

    )

except ValidationError as e:

    for error in e.errors():

        print(f"❌ {error['loc'][0]}: {error['msg']}")

# ❌ name: String should have at least 2 characters

# ❌ age: Input should be greater than 0

# ❌ salary: Input should be greater than 0

# ❌ email: String should match pattern '^[^@]+@[^@]+\.[^@]+$'
```
- `Field()` 함수를 통해 길이, 숫자 등의 제약 조건과 설명 설정 가능

| 제약조건          | 설명                 | 예시                        |
| ------------- | ------------------ | ------------------------- |
| `min_length`  | 최소 길이              | `Field(min_length=2)`     |
| `max_length`  | 최대 길이              | `Field(max_length=50)`    |
| `gt`          | 초과 (greater than)  | `Field(gt=0)`             |
| `ge`          | 이상 (greater equal) | `Field(ge=0)`             |
| `lt`          | 미만 (less than)     | `Field(lt=100)`           |
| `le`          | 이하 (less equal)    | `Field(le=120)`           |
| `pattern`     | 정규식 패턴             | `Field(pattern=r'^\d+$')` |
| `description` | 설명 추가              | `Field(description="설명")` |


# 에러 구조 자세히 보기

```python
try:

    bad_employee = Employee(name="김", age=0, salary=-1000, email="invalid")

except ValidationError as e:

    for error in e.errors():

        print(f"위치: {error['loc']}")      # ('name',) 같은 튜플

        print(f"타입: {error['type']}")     # 에러 타입

        print(f"메시지: {error['msg']}")    # 사용자용 메시지

        print(f"입력값: {error['input']}")   # 실제 입력된 값

        print("---")
```
  
>[!error]
>```python
>위치: ('name',)
>타입: string_too_short
>메시지: String should have at least 2 characters
>입력값: 김
>```

>[!error]
>```python
>위치: ('age',)
>타입: greater_than
>메시지: Input should be greater than 0
>입력값: 0
>```

...


## 참고 자료

- [Pydantic 공식 문서](https://docs.pydantic.dev/)
