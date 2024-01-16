---
tags:
  - 타입스크립트
  - type
  - interface
---

> [!INFO] 참고하면 좋을 링크
> - [타입스크립트 핸드북](https://www.typescriptlang.org/ko/docs/handbook/intro.html)
> - [타입스크립트 핸드북 한글 문서](https://typescript-kr.github.io/)

# 차이점

| 구분           | `type`   alias                   | `interface` |
| -------------- | --------------------------- |:----------- |
| 선언 가능 대상 | 모든 유형의 타입(원시, 객체 | 객체만 가능 |
| 선언적 확장    | 불가능                      | 가능        |
| Computed Value | 사용 가능                   | 사용 불가능 |


> [!INFO] 선언적 확장이란?
> 새로운 속성을 위해 다시 같은 이름으로 선언할 수 있다는 것을 의미한다. `interface` 의 경우 아래와 같이 새로운 속성을 추가할 때, 같은 인터페이스명으로 다시 선언할 수 있다.
> 
> ```ts
> interface Window { 
> 	title: string 
> } 
> 
> interface Window { 
> 	ts: TypeScriptAPI // 새로운 속성
> } 
> 
> // 같은 interface 명으로 Window를 다시 만든다면, 자동으로 확장이 된다. 
> const src = 'const a = "Hello World"' window.ts.transpileModule(src, {})
> 
> type Window = { 
> 	title: string 
> } 
> 
> type Window = {
> 	ts: TypeScriptAPI
> } 
> 
> // Error: Duplicate identifier 'Window'. 
> // 타입은 안된다.
> ```

> [!INFO] Computed Value?
> 연산을 통해 반환되는 값들을 의미하며, 타입에서는 `in` 을 통해 유니온 형태의 타입을 키 목록으로 나열하는 등의 방식을 활용할 수 있습니다.
> 
> ```ts
> type names = 'firstName' | 'lastName' 
> 
> type NameTypes = { 
> 	[key in names]: string 
> } 
> 
> const yc: NameTypes = { 
> 	firstName: 'hi', 
> 	lastName: 'yc' 
> } 
> 
> interface NameInterface { 
> 	// error 
> 	[key in names]: string 
> }
> ```

# 성능 측면에서의 관점


> [!NOTE] 원문
> [GitHub Wiki TypeScript : Preferring Interfaces Over Intersections](https://github.com/microsoft/TypeScript/wiki/Performance#preferring-interfaces-over-intersections)

- 객체 타입을 확장할 때, 각각 `&`(`type`의 경우) 와 `extends`(`interface`의 경우) 를 사용한다면 `type`의 경우 오류를 반환할 수 있다.
- 이는 두 확장 방식의 차이 때문인데 `interface` 는 속성 간 충돌을 방지하기 위해 단순한 객체 타입을 생성하는 반면 `type`의 경우엔 재귀적으로 순회하며 속성을 머지한다.
- `type`은 원시 타입이 올 수도 있기에 충돌이 나서 제대로 머지되지 않은 경우 `never`를 할당한다.

```ts
type type2 = { a: 1 } & { b: 2 } // 잘 머지됨 
type type3 = { a: 1; b: 2 } & { b: 3 } // resolved to `never` 

const t2: type2 = { a: 1, b: 2 } // good 
const t3: type3 = { a: 1, b: 3 } // Type 'number' is not assignable to type 'never'.(2322) 
const t3: type3 = { a: 1, b: 2 } // Type 'number' is not assignable to type 'never'.(2322)
```


# 활용 방식에 대한 의견

- 고려의 순서
	1. 우선적으로 팀 레벨 혹은 프로젝트 레벨에서 지정한 컨벤션에 따라 일관성 있게 활용한다.
	2. 타입 합성을 고려하여 `interface`를 사용한다.
		- 선언 병합을 위해 외부에 공개되는 API는 `interface` 사용을 권장한다.
- 타입스크립트 핸드북에서의 언급
	- `type`을 사용해야 할 때까지 최대한 `interface`를 활용하라.

> [!INFO] 핸드북 언급 원문
> "For the most part, you can choose based on personal preference, and TypeScript will tell you if it needs something to be the other kind of declaration. If you would like a heuristic, use `interface` until you need to use features from `type`."

> [!INFO] Heuristic의 의미
> 
> **휴리스틱**(heuristics) 또는 발견법(發見法)이란 불충분한 시간이나 정보로 인하여 합리적인 판단을 할 수 없거나, 체계적이면서 합리적인 판단이 굳이 필요하지 않은 상황에서 사람들이 빠르게 사용할 수 있게 보다 용이하게 구성된 간편추론의 방법이다.

## `type` alias를 사용해야 하는 경우

- 원시, 유니온 형태의 타입을 선언해야 하는 경우
- [조건부 타입(Conditional type)](https://www.typescriptlang.org/ko/docs/handbook/2/conditional-types.html), [타입 가드(Type guard)](https://radlohead.gitbook.io/typescript-deep-dive/type-system/typeguard), [매핑 타입(Mapped types)](https://typescript-kr.github.io/pages/advanced-types.html#%EB%A7%A4%ED%95%91-%ED%83%80%EC%9E%85-mapped-types) 등의 고급 타입 기능을 활용하는 경우

