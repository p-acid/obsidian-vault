---
tags:
  - Web
  - Worker
---
# 정의

- 이벤트 기반 [[워커(Web Worker)]]로 자바스크립트 파일의 형태를 갖춘다.

# 기능

- 연관된 웹 페이지/사이즈를 통제하여 탐색과 리소스 요청을 가로채 수정하고, 리소스를 굉장히 세부적으로 캐싱할 수 있다.

# 특징

- 워커 맥락에서 실행되기 때문에 **DOM에 접근할 수 없습니다.**
- 앱의 주 자바스크립트와 다른 스레드에서 동작하기 때문에, **연산을 가로막지 않습니다. (논 블로킹)**
- 온전히 **비동기적으로 설계**되어 [XHR](https://developer.mozilla.org/ko/docs/Web/API/XMLHttpRequest)이나 [Web Storage](https://developer.mozilla.org/ko/docs/Web/API/Web_Storage_API) 등의 API를 사용할 수 없다.
- 보안 상의 이유로 HTTPS에서만 동작합니다.
	- 네트워크 요청을 수정할 수 있다는 점에서 중간자 공격에 굉장히 취약하기 때문.

# 활용

- 





# 참조

- [MDN Web Docs : 서비스 워커](https://developer.mozilla.org/ko/docs/Web/API/Service_Worker_API)
- [카카오 엔터테인먼트 FE 기술 블로그 : 서비스 워커에 대해 알아보고 Mock Response 만들기](https://fe-developers.kakaoent.com/2022/221208-service-worker/)