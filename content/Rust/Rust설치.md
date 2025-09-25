---
tags:
  - rust
  - init
  - 설치
create: 2025-08-13 17:24:03
---


## Installing: For mac

```sh
xcode-select --install
```

https://www.rust-lang.org/tools/install

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

```sh
 rustc --version
 
rustc 1.89.0 (29483883e 2025-08-04)
```

## update rust
```sh
rustup -h

# update
rustup update

# uninstall
rustup self uninstall

# get docs
rustup doc
```


