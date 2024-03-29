---
tags:
  - webpack
  - bundler
  - vite
date: 2024-01-17
---
# 모듈 번들러?

- [[#모듈]]
	- [[#모듈 시스템]]
- [[#번들러]]

## 모듈

### 개념

- **모듈**은 간단하게 **본체에서 분리된 독립된 하위 개체**라고 이해할 수 있습니다.
- 자바스크립트에서는 **모듈 단위의 스코프**를 활용하여 **의존성과 스코프 오염**에 대한 문제를 해결합니다.

### 필요성

- 자바스크립트를 효율적으로 관리하기 위해선 **모듈 단위 개발**을 해야 합니다.
- 자바스크립트 코드를 **단순히 파일로 분리하는 것은 모듈화가 아닙니다.**
	- 단순히 파일을 분리해도, 자바스크립트는 **전역 스코프**를 사용하여 **스코프 오염**을 야기합니다.
- 각 파일은 **의존성에 맞게 순서대로 로딩되어야 합니다.** 그렇지 않으면, 스크립트가 실행되지 않을 수도 있습니다.

### 모듈 시스템

> 다양한 모듈들을 쉽게 불러오고 네임스페이스를 구분하는 등의 작업을 위해 구축된 시스템

- **CommonJS**
    - **동기 방식**으로 **`require`** 함수를 통해 의존성 모듈을 가져오고 **`module.exports`** 객체로 모듈 API를 정의합니다.
    - **브라우저에서 바로 사용 불가능**합니다.
    - 번들러로 변환 과정을 거쳐야하지만, **Node는 CommonJS를 사용하기 때문에** Node 기반 개발에서는 CommonJS를 바로 사용할 수 있습니다.
- **AMD(Asynchronous Module Definition)**
    - **비동기 방식**으로 **`define`** 함수를 통해 모듈의 API와 의존성 관계를 정의합니다.
    - **브라우저에서 바로 사용 가능**하며, **동적 로딩**을 지원합니다.
- **ES6 모듈**
    - 모듈 정의를 위해 **`import`** 와 **`export`** 를 사용합니다.
    - 가장 익숙한 모듈 시스템입니다.
    - **동적으로 `import` 내지 `export` 를 할 수 없습니다.**
        - 실행 시점에서 `import` 및 `export` 할 대상을 변경할 수 없기에, **구문 분석을 진행하여 사용하지 않는 코드를 제외하는 최적화(트리 쉐이킹)를 할 수 있습니다.**

## 번들러

### 정의

> **소스 코드를 모듈별로 작성**하고 **모듈간 또는 외부 라이브러리간의 의존성 관리**를 돕는 도구입니다.

- 모듈의 중요성이 증대되고 **기능 단위 모듈화와 관리의 필요성**이 생기면서 **번들러**가 중요해졌습니다.
- 앞의 AMD를 제외하고 브라우저 환경에서는 모듈 시스템을 바로 실행할 수 없으므로, **모듈 코드의 분석과 모듈 스펙에 따른 새 코드로의 가공**이 필요합니다.
	- 한 마디로, **브라우저에서 모듈 코드가 잘 실행되도록 해주는 도구**입니다.
- 대표적인 번들러로 **[[Webpack]], Rollup, Parcel, [[Vite]]** 등이 있습니다.