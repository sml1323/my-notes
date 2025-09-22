---
tags:
  - rust
  - 러스트
create: 2025-09-07 19:42:59
---
udemy 
```txt
Master the Rust programming language from A-Z. Includes projects, quizzes, and more. Beginners welcome!

강의 정리
```
[learn_to_code_with_rust](https://www.udemy.com/course/learn-to-code-with-rust/)
## Intro to Rust
- rust: system programming language
	- system programming language: resources가 제한된 상황에 최적화된 언어
## The Rust Compiler
- rust compiler는 source code를 컴퓨터가 실행할 수 있도록 번역하는 프로그램
### Syntax
- rust is strictest language.
- 모든 detail들은 중요하다.
	- case sensitivity, spaces, symbols, ...

## Installing Rust
[[Rust 설치]]

## Create rust project with cargo
>[!note]
>**cargo**는 rust project 관리를 위한 cli tool
- cargo는 rust project를 위한 starter template을 제공한다.
```sh
cargo new hello_world
```

![[Pasted image 20250914184033.png]]

## Hello world
- rust code는 `.rs` 확장자
- rust code는 function으로 이루어짐
	- function은 프로그램이 실행되기 위한 단계 또는 순차적 지침  - 요리 레시피

>[!note]
>모든 Rust function은 function keyword, "fn" 으로 시작한다.
- 모든 rust program은 lowercase `main` 으로 시작한다.(case sensitive)
- `main` 은 프로그램의 진입점
>[!info]
>```rust
>
>fn main(// parameters) { // code block
>    .... // 4 block indent
>    println!("Hello world"); // semicolon은 코드 라인의 끝
>
>}
>```
- macro - 미리 작성된 recipe
	- `println!("Hello world")`: 문자열 출력

코드는 **compile** 하여 실행 가능한 프로그램으로 번역 후 실행 - rust 가 설치되지 않은 환경에서도 실행 가능
![[Pasted image 20250914184153.png]]
- vscode rust extension 의 하위 종속성인 rust analyzer의 기능인 run 버튼을 통해 컴파일 후 실행 가능
또는 `rustc` 명령어를 통해 컴파일 후 실행
![[Pasted image 20250914184851.png]]
>[!flow]
>1. `rustc main.rs` 로 작성한 소스코드 컴파일
>   - `main.rs` 소스코드의 이름과 동일하지만 확장자가 없는 **main** 파일 생성
>2. `./main` 명령어를 통해 실행

- mac os에서는 `file` 명령어를 통해 컴파일되거나 구축된 아키텍처의 종류 확인 가능
❯ file main
main: Mach-O 64-bit executable arm64


## Formatting with rustfmt and cargo fmt
```rust
rustfmt main.rs
```
- 가독성 좋게 **코드를 바꾸지 않고** 위치 변경
- `rustfmt`는 단일 파일 대상
```rust
cargo fmt
```
- 프로젝트 전체에 적용

## The cargo build Command
- cargo build 명령어를 통해 프로젝트 전체를 컴파일 할 수 있다
```rust
cargo build
// 프로젝트 루트에서
```
- **defug mode**: 빠르고, 최적화되지 않은 빌드
	- 컴파일 후 오류를 찾는데 도움이 되는 추가적인 **메타데이터**가 포함
- `cargo build` 명령어는 `target` 폴더에서 최종 실행 파일을 생성
![[Pasted image 20250914215357.png]]

```rust
❯ ./target/debug/hello_world
Hello world! 러스트 프로그램 첫 실행
```
- `target/debug/project_name` 디렉토리에서 실행 가능

```rust
cargo build --release
```
![[Pasted image 20250914215900.png]]
- `cargo build --release` 명령어를 통해 릴리스 모드로 컴파일 
- `cargo clean` 명령어로 컴파일 된 산출물 - `target` 폴더에 있는 - 전부 삭제

## The Cargo run command
```rust
cargo run
```
- debug mode로 컴파일 후 실행
- `cargo run --quiet`: 실행결과만 표시

## The Cargo check command
```rust
cargo check 
```
>[!error]
>```zsh
>
>cargo check
>    Checking hello_world v0.1.0 (/Users/imseungmin/work/ruststudy/hello_world)
>error[E0423]: expected function, found macro `println`
> --> src/main.rs:2:5
>  |
>2 |     println("Hello world! 러스트 프로그램 첫 실행");
>  |     ^^^^^^^ not a function
>  |
>help: use `!` to invoke the macro
>  |
>2 |     println!("Hello world! 러스트 프로그램 첫 실행");
>  |            +
>
>For more information about this error, try `rustc --explain E0423`.
>error: could not compile `hello_world` (bin "hello_world") due to 1 previous error
>```

## Comments
- 주석
```rust
fn main() {

// 더블 슬래시를 이용해서 주석 달기

println!("Hello world! 러스트 프로그램 첫 실행"); // comments

}
```
- multi line comments
```rust
fn main() {

// 더블 슬래시를 이용해서 주석 달기

println!("Hello world! 러스트 프로그램 첫 실행");

/*

주석 1

주석 2

주석 3

주석 4

*/

  
}
```
- `/**/` 을 사용해 multiline comments 가능


