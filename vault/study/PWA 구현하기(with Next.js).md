---
tags:
  - nextjs
  - PWA
date: 2024-01-16
---
> [레포지토리 링크](https://github.com/p-acid/pwa-tutorial)

> [!INFO] 도움이 되는 링크 목록
> - [PWA Builder](https://www.pwabuilder.com/)
> 	- 마이크로소프트에서 진행하는 오픈 소스 프로젝트.
> 	- PWA 구현을 위한 조건을 체크하고 충족할 수 있도록 가이드를 제공.
> 	- 외부 접근 URL 필요함(정적 배포 필요).
> - [Google Workbox](https://developer.chrome.com/docs/workbox?hl=ko)
> 	- 구글에서 제공하는 라이브러리.
> 	-  다양한 PWA를 위한 서비스 워커를 만들어줌.
> - [Maskable](https://maskable.app/)
> 	- 어댑터블 아이콘을 디자인 할 수 있는 서비스.

- 프로젝트에 적용된 프레임워크 내지 라이브러리 별로 상세 구현 프로세스는 다르지만 큰 맥락에서 다음 흐름을 일반적으로 가진다.
- 프레임워크라면 프레임워크 별로 커뮤니티를 기반으로 하는 패키지들이 존재하고, 이러한 라이브러리들이 아래의 프로세스를 보다 더 쉽게 처리할 수 있도록 해준다.

1. `manifest` 파일 설정
2. PWA Icon 추가
3. 서비스 워커 추가
