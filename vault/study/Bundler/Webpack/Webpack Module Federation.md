---
tags:
  - webpack
  - Micro-Frontend
date: 2024-01-19
---
# Module Federation

> [[Webpack Module Federation]] 참조

## Motivation

>여러 개의 개별 빌드가 단일 애플리케이션을 형성해야 합니다. 이러한 개별 빌드는 컨테이너처럼 작동하며, 빌드 간에 코드를 노출하고 소비하여 단일 통합 애플리케이션을 생성할 수 있습니다.
>
>이것은 종종 [[Micro-Frontends]]라고 알려져 있지만, 그것에만 국한되지는 않습니다.

- 개별적으로 빌드되는 결과물이 하나의 애플리케이션으로 완성된다는 것
- 마이크로 프론트엔드로 유명하지만 이것만으로 귀결되지 않는다는 것

## Low-level concepts

- 로컬 모듈과 원격 모듈을 분리한다.
- 로컬 모듈은 현재 빌드의 일부인 일반 모듈이다.
- 원격 모들은 현재 빌드의 일부가 아니며 원격 컨테이너에서 런타임에 로드되는 모듈이다.

> **원격 모듈 로드에 대하여**
> 
> 로드는 비동기 작업으로 간주되며 청크 로드 작업에 배치되기에 청크 로드 없이는 원격 모듈을 이용할 수 없다.그리고 청크 로드 작업은 일반적으로 `import()`를 호출하는 것이지만, `require.ensure` 또는 `require([...])` 같은 이전 구조도 지원됩니다.

