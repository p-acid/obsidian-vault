---
tags:
  - 우아콘
  - 컨퍼런스
---
# 마이크로 프론트엔드 유래

- BE 파트에서 프로덕트 규모가 커짐에 따라 마이크로 아키텍쳐를 구현
- FE, BE의 분리와 각 분야의 고도화
- FE도 프로덕트의 거대화를 피할 수 없었고 이에 따라 마이크로 아키텍쳐 적용

# 배민의 현 상황

- 전시 영역 관리 어드민
	- 여러 개의 어드민으로 나뉘어서 관리
	- 관리 측면에서 각각의 어드민으로 접속
	- 인증/인가의 개별 관리
	- 개발 시 각각의 프로덕트 변경
- 사업 영역이 확장된다면? N개의 도메인 확장
	- N개의 어드민 추가  
	- N개의 어드민 별로 인증/인가관리 - N개의 어드민 별로 개발/피쳐 관리
	- 운영, 관리, 개발의 부담 증가

> 결론적으로 운영, 관리, 개발의 부담 증가 발생

# 마이크로 프론트엔드는 항상 좋은가?

- 마이크로 프론트엔드의 유무에 따라 개발 비용의 시작점이 다르다.
	- 마이크로 프론트엔드의 기본적인 비용(코드베이스 학습 등)이 출발점을 다르게 한다.
	- 적절한 시기에 적용하는 것이 중요

# 어플리케이션 간 커뮤니케이션

## Props 이용

- 익숙하고, 허용 가능한 패턴
- 하지만 커플링을 통한 의존성, 불필요한 리렌더링, 프레임워크 통일 조건의 문제 발생

## Web Storage API 이용

- 의존성이 적고, 다양한 브라우저 지원
- 하지만 확장 가능한 솔루션은 아니며, 보안에 취약

## CustomEvent 이용

> [MDN Docs : CustomEvent](https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent/CustomEvent)

```ts
const addToCart = (item) => {
	const addEvt = new CustomEvent('ADD_TO_CART', { item })
	window.dispatchEvent(addEvt)
}
```

- 비동기 이벤트 기반, 확장에 용이

## Custom MessageBus 이용

```ts
class MessageBus {
	publishEvent(eventName, data) { ... }
	subscribe(eventName, handler) { ... }
	unsubscribe(eventName, handler) { ... }
}
```

- 비동기 이벤트 기반, 확장에 용이, 구조에 맞는 설계
- 구현하는데 노력, 모든 팀에 알맞은 구조설계 필요

# 프론트엔드 상태 구현은?

> Redux, Recoil과 같이 프론트엔드에서 활용하는 상태 값은 어떻게 구현할까?

- 기존에 이런 상태 공유에 대한 논의들을 꾸준히 해왔었기에 이를 활용하여 원만히 해결했다.

# 리액트의 페이지 렌더링

- CSR/SSR 모두
	- Rendering React components 단계가 존재
	- 프로젝트 내 Component module `import` 하여 rendering
- 프로젝트 외부의 Component module rendering?
	- Rendering React components 단계에서 외부의 컴포넌트를 `import`
	- 이것이 마이크로 프론트엔드 개념의 시작


# Module Federation?

> “웹 애플리케이션 개발에서의 코드 공유”

- 코드를 배포 가능한 작은 모듈 단위로 분리 분리된 모듈을 동적으로 로드  
	- Webpack의 Module Federation을 이용
- `expose` option  
	- 특정 모듈을 다른 애플리케이션에 노출
- `remote` option
	- 특정 모듈을 다른 애플리케이션에서 로드

## 장점

- 유연성의 향상
	- 애플리케이션을 작고 관리하기 쉬운 모듈로 분할    
	- 필요에 따라 모듈을 교체 
- 확장성 향상
	- 개별 애플리케이션의 크기와 복잡성 감소
	- 유지관리 및 확장의 용이
- 협업 향상  
	- 팀간의코드베이스공유
	- 효율적 작업 가능

## 단점

- 복잡성 증가
	- dependency, versioning 관리 필요
	- 개발하고 운영하는데 난이도
- 보안 위험  
	- 애플리케이션 간 코드 공유시 취약점 발생 가능
	- 이에 따른 보안조치 필요
- 잠재적 성능 문제
