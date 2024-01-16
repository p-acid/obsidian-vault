---
tags:
  - PWA
  - App
---
# PWA?
---
## 정의

- 웹과 네이티브 앱 모두의 이점을 갖도록 특정 기술 및 표준 패턴을 사용해 개발된 웹 앱

## 특징

- 새로운 기술이 아니라 일부 특정 패턴과 API 및 다른 기능들을 포함하는 웹 앱 구축 방식을 의미합니다.
- 웹의 접근성과 네이티브 앱의 모바일에서의 좋은 사용성을 동시에 활용할 수 있는 유형입니다.
- PWA는 오프라인에서 동작하고, 설치가 가능하며, 쉬운 동기화와 푸시 알림 등을 지원합니다.

## 원칙

- 검색 엔진을 통해 접근이 가능합니다.
- 모바일 기기 홈 화면에서 사용할 수 있습니다.
- URL을 통해 공유할 수 있습니다.
- 오프라인이나 불안한 네트워크 연결에서 동작합니다.
	- 캐시된 데이터를 사용하여 렌더링
- 최신 브라우저의 모든 기능을 사용할 순 없지만 기본 기능은 사용 가능합니다.
- 알림을 보낼 수 있습니다.
- 반응형을 지원합니다.
- 유저와 앱 간의 연결이 민감 데이터에 접근하려는 것에 안전합니다.

## 이점

- [[서비스 워커(Service Worker)]]를 사용한 캐싱 덕분에 앱 설치 후 로딩 시간이 줄어들어 데이터와 시간 절약
- 앱 업데이트가 있을 때 변경된 컨텐츠만 업데이트 할 수 있습니다.
	- 네이티브 앱의 경우엔 전체 앱을 다시 다운로드 받아야합니다.
- 네이티브 플랫폼에 더 통합된 느낌 (홈 화면 추가 및 전체 화면 실행 등)
- 시스템 알림 및 푸시 메시지를 활용하여 사용자 재참여 유도 가능

## 브라우저 호환성

- [[서비스 워커(Service Worker)]] 지원이 핵심입니다.
	- 감사하게도 현재 데스크탑 및 모바일의 모든 주요 브라우저에서 지원되기에 상관 없습니다.
- [웹 앱 Manifest](https://developer.mozilla.org/ko/docs/Web/Manifest), [푸시](https://developer.mozilla.org/ko/docs/Web/API/Push_API), [알림](https://developer.mozilla.org/ko/docs/Web/API/Notifications_API), [홈 화면에 추가 (en-US)](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable "Currently only available in English (US)") 등이 지원됩니다.
	- Safari에서는 푸시 알림은 지원하지 않으며 웹 앱 Manifest, 홈 화면 추가 등을 제한적으로 지원합니다.


# 학습 가이드
---
## [Google : Learn PWA](https://web.dev/learn/pwa)


# 구현하기

[[PWA 구현하기(with Next.js)]] 참조



# 참조

- [x] [MDN Web Docs : 프로그레시브 웹 앱 소개](https://developer.mozilla.org/ko/docs/Web/Progressive_web_apps/Tutorials/js13kGames) ✅ 2023-11-22
- [x] [요즘 IT : 프론트엔드 개발자가 PWA 알아야 하는 이유](https://yozm.wishket.com/magazine/detail/1969/) ✅ 2023-11-22

