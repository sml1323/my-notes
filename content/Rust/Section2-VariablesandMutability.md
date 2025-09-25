---
tags:
  - rust
  - 러스트
create: 2025-09-16 15:28:13
---
## Intro to Variables
1. 식별자 역할
2. 재사용
```rust
fn main() {

    let apples: i32 = 50; // 변수는 snake_case_formatting

    // : i32 -> 변수 타입 지정,이 경우 32bit integer type

    let oranges: i32 = 14 + 6;

    let fruits: i32 = apples + oranges;
    
    println!("This year, my garden has {} apples.", apples); 

}
```

>[!note] 변수출력
>- `println!("This year, my garden has {} apples.", apples);` 
> 	- 매크로에서, 문자열 속 curly braces 선언 후 다음 인수에 변수를 선언하면 curly brace가 변수를 참조하여 결과를 반환
> *OR* 
> - `println!("This year, my garden has {apples} apples.");` 
력

## Positional Arguments to println!

![[Pasted image 20250922233225.png]]

```rust
println!("This year, my garden has {0} apples and {1} oranges.

I can't believe I have {2} fruits

{0}, {1}, {2}",

apples, oranges, fruits);
```
- **인수(arguments)** 의 **index(0부터 시작)** 를 이용해 같은 변수를 여러번 사용할 수도 있다.

