---
tags:
  - 컨퍼런스
  - 우아콘
  - 상태관리
  - Zustand
  - React-Query
---
![프론트엔드 상태관리 실전편](https://www.youtube.com/watch?v=nkXIpGjVxWU)

# 프론트엔드 상태 관리

> State: A Component's Memory

- 일반적으로 상태는 컴포넌트에 귀속되고 이를 타개하기 위해 **상태관리**라는 개념이 생김
- 기존 상태관리 방법론과 이에 대한 문제점은 무엇인가?

# 상태관리에 대한 고민

- 기존엔 Redux와 MobX를 사용했다.
	- Store가 너무 크고 복잡하며 상태관리보다 API 호출 코드가 더 많아진다.
	- 해당 라이브러리를 비동기 통신 데이터를 저장하는 용도로 주로 사용한다.
	- React Query로 교체하자!
- 이렇게 하니 Store는 간단해졌는데 컴포넌트가 복잡하다.
	- Client Store를 간단하게 관리해되 될 것 같았다.
	- 비즈니스 로직이 대부분 컴포넌트에 있다.
	- Zustand를 적용하자!
- 최종적으론 Zustand와 React Query
	- Client에서 소유 및 관리하며 Client에서 온전히 제어가능한 상태는 Zustand
	- Client 외부에서 소유하면 Client에서는 일종의 캐시인 상태는 React Query

# Server State 관리

- `@lukemorales/query-key-factory`
	- 쿼리키 관리 라이브러리

# 후기

- 전반적으로 이전 팀에서 상태관리 툴을 변경할 때 느꼈던 고민과 일치했던 내용인 듯.
- 우리는 Recoil을 썼는데 Zustand는 어떤지 궁금해짐