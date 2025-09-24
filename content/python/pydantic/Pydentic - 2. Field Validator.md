---
tags:
  - pydantic
  - python
  - validator
create: 2025-09-24 17:11:56
---
# 1. field_validator
```python
from pydantic import field_validator, BaseModel

class UserAccount(BaseModel):

    username: str

    password: str
    @field_validator('username')
    @classmethod
    def validate_username(cls, v): # cls: 필드(속성)명, v: 값 - UserAccount(username='kim', password='12345678') 에서 'kim', '12345678'
        if len(v) < 3:
            raise ValueError(f'{cls}는 3글자 이상이여야 함')
        return v.lower() # 소문자 변환 후 반환
        
    @field_validator('password')
    @classmethod
    def validate_password(cls, v):
        if len(v) < 8:
            raise ValueError('비밀번호는 8자 이상이여야 함')
        return v

UserAccount(username='kim', password='12345678') # Value error, <class '__main__.UserAccount'>는 3글자 이상이여야 함 [type=value_error, input_value='ab', input_type=str]

UserAccount(username='ab', password='123')# Value error, 비밀번호는 8자 이상이여야 함 [type=value_error, input_value='123', input_type=str]
```
- `field_validator()` 매개변수에 클래스의 속성(필드)명 입력
- 객체 생성시 자동 실행

>[!warning] ❌ 잘못된 방법 - 에러남
>```python
  >@field_validator('username') 
  >def check_username(self, v):  # self 쓰면 안됨!
    >  return v

> [!done]  ✅ 올바른 방법
  >```python
>
  >@field_validator('username')
  >@classmethod 
  >def check_username(cls, v):   # cls 써야 함!
    >  return v
    >  ```  

- `field_validator()` + `classmethod` 데코레이터 둘다 사용해야함
### classmethod
- 클래스 메서드 - 인스턴스 없어도 호출 가능
- 객체 생성 전에 검증이 일어나기 때문에, self 인스턴스 사용 불가하므로 클래스 매서드를 사용해야한다.

