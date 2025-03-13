# 2025.01.13 2주차

깃허브와 vsCode를 연동하여 커밋하는 방법을 배웠다.

### Node.js란?

#### 장단점
* 장점
> 비동기 논 블로킹 I/O로 높은 성능
  JavaScript 풀스택 개발이 가능
  npm의 방대한 생태계를 활용 가능
  경량 서버 개발에 적합(Express.js)
  실시간 데이터 처리가 강력
* 단점
> CPU 집약적인 작업에 부적합 : 멀티스레딩 성능 부족
  콜백 지공 문제
  보안 취약

### React Project의 구조 및 역할
* public/ : 정적 파일을 저장하는 폴더, 빌드 시 그대로 유지
  * index.html : React 앱이 마운트 되는 HTML파일.
* src/ : React 앱의 주요 코드가 위치하는 폴더
  * App.css : App.js에 적용되는 스타일
  * App.js : 메인 컴포넌트
  * index.css : 전역 스타일
  * index.js : React 앱의 진입점. ReactDOM.createRoot를 사용하여 App.js를 렌더링
* .gitignore : Git에 추가하지 않을 파일 목록을 정의.
* package-lock.json : 설치된 패키지의 정확한 버전이 기록된 파일
* package.json : 프로젝트의 의존성 목록과 실행 스크립트가 포함된 파일.
* README.md : 프로젝트 설명 문서.