---
tags:
  - math
  - 수학
  - 집합론
  - 직문수
create: 2025-09-04 23:05:45
dg-publish: false
"":
---
[직문수](https://youtube.com/playlist?list=PL4m4z_pFWq2pHnFFpE25LT4kR6_3jv5CY&si=5_LF9s1w9xH0t1UM)
#  1. 집합과 명제, 공리
- 수학에서 주장은 참과 거짓을 취급한다.
	- 참, 거짓을 판별 = 특정 `집합` 에 속하냐 아니냐를 판단

>[!example]
>강아지는 고양이가 아니다
$\iff$ 강아지는 고양이의 집합에 속하지 않는다.
강아지 $\notin$ {고양이 집합}



추상화: $강아지 \to x$, $고양이 집합 \to S$, $\iff$ $x \notin S$ 
>  추상화:  구체적인 사례에서 공통적인 특성을 이용하여 포괄적이고 일반적인 형태로 바꾸는것

>[!definition]
>- **x**: 특정 집합에 속한 원소(element)
>- **S**: 특정 조건을 만족하는 원소들의 모임(Set)
>
>##### 집합표기법
>- { }: 구체적인 원소를 나열할때 사용한다. ex) $S = {1, 2, 3}$ or $S = \{x \mid x > 0 \text{ and } x \leq 1\}$
>- $() []$: 구간표기,  **"연속된 숫자 범위"**를 표현할 때 사용한다. ex) $(0,1]은 \text{0보다 크고 1 이하인 모든 실수}$





![[Drawing 2025-09-04 23.40.28.excalidraw]]


>[!question]
>1) 정수의 집합은 자연수 집합보다 크다?
>2) 유리수의 집합은 정수의 집합보다 크다?

>[!missing]
>전부 거짓

1) 질문에 대한 답: 자연수 집합과 정수의 집합의 일대일 대응을 통해 증명


자연수 자체를 조작해서 정수로 만드는거라기 보다는, 특정 규칙에 따라 모든 자연수를 모든 정수에 매핑가능함을 보여 증명

**짝수 자연수들의 대응:**
- $2 = 2 \times 1 \longrightarrow 1-1 = 0$
- $4 = 2 \times 2 \longrightarrow 2-1 = 1$
- $6 = 2 \times 3 \longrightarrow 3-1 = 2$
- $8 = 2 \times 4 \longrightarrow 4-1 = 3$

**일반화:** $2n = 2 \times n \longrightarrow n-1$
**홀수 자연수들의 대응:**
- $1 = 2 \times 1 - 1 \longrightarrow -1$
- $3 = 2 \times 2 - 1 \longrightarrow -2$
- $5 = 2 \times 3 - 1 \longrightarrow -3$
- $7 = 2 \times 4 - 1 \longrightarrow -4$
**일반화:** $2n-1 = 2 \times n - 1 \longrightarrow -n$
- 여기서 n은 순서 매개변수로 이해


: 정수와 자연수는 전부 하나씩 대응시킬 수 있다$\implies$갯수로 대소관계를 정의할 수 없다.

| | b=1 | b=2 | b=3 | ... |
|---|---|---|---|---|
| **a=1** | 1/1 | 1/2 | 1/3 | ... |
| **a=2** | 2/1 | 2/2 | 2/3 | ... |
| **a=3** | 3/1 | 3/2 | 3/3 | ... |
| **...** | ... | ... | ... | ... |


