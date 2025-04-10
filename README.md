# 202330215 송승헌

# 2025.04.10 6주차

#### prop를 통해 데이터 전달하기
1. React의 component architecture를 사용해서 재사용할 수 있는 component를 만들어서 지저분하고 중복된 코드 삭제
2. Board component를 만들고, square component의 내용을 복사한다.
3. square component의 button을 하나만 남기고 모두 삭제한다
4. Board component의 button을 square component로 교체한다.
5. App에서 호출하는 component를 square에서 Board로 바꿔준다.

* 여기까지 할 시에 component는 깔끔하게 정리 되었지만, 숫자출력이 1만 나오게 된다.
* 이 문제를 해결하기 위해 props를 사용하여 각 사각형이 가져야 할 값을 부모 component(Board)에서 자식 component(square)로 전달한다.
* component를 호출하는 쪽이 부모 component이다.

### state 끌어올리기
* 여러 자식 컴포넌트에서 데이터를 수집하거나 두 자식 컴포넌트가 서로 통신하도록 하려면, 부모 컴포넌트에서 공유 state를 선언해야함.
* 부모 컴포넌트는 props를 통해 해당 state를 자식 컴포넌트에 전달 할 수 있다.
* 이러면 자식 컴포넌트가 서로 동기화 되고, 부모 컴포넌트와도 동기화 되도록 할 수 있다.
* React 컴포넌트를 리팩토링할 때 부모 컴포넌트로 state를 끌어올리는 건 많이 사용되는 방법이다.

### 


# 2025.04.03 5주차

### Hook 사용하기
* use로 사직하는 함수가 Hook이다
* useState는 React에서 제공하는 내장 Hook이다
* Hook은 다른 함수보다 더 제한적이다.
  * component 또는 다른 Hook의 상단에서만 Hook을 호출할 수 있다.
  * 조건이나 반복문에서 useState를 상용하고 싶다면 새 컴포넌트를 추출하여 그곳에 넣어야한다.

#### Hook의 사용규칙
! 왜 이런 규칙이 필요한가? : React의 동작을 예측 가능하고, 안정성을 높이기 위해 필요
1. rendering 순서를 보장하기 위해

  조건문이나 반복문 안에서 Hooks를 사용하면
  매 rendering마다 Hook의 호출 순서가 달라질 수 있기 때문에
  React가 상태를 제대로 추적할 수 없다.

2. 불필요한 사이드 이펙트 방지

  component가 여러번 rendering 될 때마다
  동일한 순서로 Hook이 실행되어야 React가 의도한 동작을 수행할 수 있다.

#### component 간 데이터 공유
- 각 component 객체가 독립적으로 동작함
- component는 하나지만 count 변수도 객체로 여러 개 복사된 것이나 마찬가지이기 때문입니다.

# 2025.03.27 4주차

### Component의 생성 및 nesting(중첩)
#### component는
1. 고유한 로직과 모양을 가진 UI의 일부.
2. 버튼처럼 작을 수도, 전체 페이지처럼 클 수도 있다.
3. 마크업을 반환하는 JavaScript 함수.

#### export default와 export의 차이
* Named Exports
 - 하나의 파일안에 여러개의 component가 있을때 사용.
 - component를 사용하는 쪽에서는 component 정확한 이름을 반드시 명시.
* Default Exports
 - 하나의 파일안에서 하나의 component만 내보내는 경우 사용.
 - component를 사용하는 쪽에서는 어떤 이름을 사용해도 무관.

### JSX로 마크업 작성하기
앞에서 작성한 코드의 마크업 문법 : JSX
#### JSX
* JSX는 HTML보다 더욱 엄격한 문법을 적용
* JSX에선 싱글 태그라도 태그를 닫아야함 ex: < />
* React에선 여러개의 component를 JSX태그로 반환할 수 있다.
  다만 여러개의 component를 wrapping 해줘야 한다.

#### 스타일 추가하기
* React에서는 className으로 CSS클래스를 지정한다.
* className은 HTML의 class 속성과 동일한 방식으로 동작한다.
* React는 CSS파일을 추가하는 방법을 규정하진 않는다.
  -> 정적 페이지 작성때와 동일한 방법 지원
* 가장 간단한 방법은 HTML에 link태그 추가하는것.

#### 데이터 표시하기
  JSX를 사용하면 자바스크립트에 마크업을 넣을 수 있다.
  JSX 코드 내에서 JavaScript로 탈출하여 변수나 표현식을 사용하는 것이다.
  {}중괄호를 사용해서 변수나 표현식을 사용자에게 표시하도록 하는것 이다.
* 이 방법을 "Escape Back"이라고 한다.

# 2025.03.20 3주차

### React Project의 구조 및 역할2
* node_modules/ : 초기 node module 및 새로 설피하는 패키지가 저장됨
* public/ : 정적 파일을 저장하는 디렉토리
* src/ : React 프로젝트의 주요 코드가 위치하는 디렉토리
  * src/App.js : 메인 컴포넌트로 필요한 서브 컴포넌트를 모아서 관리
  * src/App.css : App.js에 적용되는 스타일을 정의하는 스타일 파일
  * src/index.js : React 앱의 진입 점으로 최종 렌더링의 되는 곳
  * src/index.css : 전역 스타일을 정의하는 스타일 파일

### 의존성 관리와 package.json
#### 의존성을 관리하는 이유
* 손쉬운 설치 및 업데이트
* 일관된 개발 환경 유지
* 중복 설치 방지

#### package.json을 유지해야 하는 이유
* 프로젝트의 의존성 정보 제공
* 버전 범위 설정 가능
* 스크립트와 메타데이터 저장
* 새로운 패키지 설치 및 관리

#### React
  React는 라이브러리. 
  컴포넌트를 조합할 수 있도록 돕지만, 라우팅이나 데이터를 가져오는 방법을 규정하지 않음
  React로 완전한 앱을 만드려면 Next.js 또는 Remix같은 풀스택 React 프레임워크를 추천
  React도 하나의 아키텍처

모든 플랫폼에서 최고의 성능을 발휘하는 React
* React를 사용하면 동일한 기술을 사용하여, 웹 앱과 네이티브 앱 모두 구축 가능
* 각 플랫폼의 고유한 강점을 활용하여 모든 플랫폼 잘 어울리는 인터페이스 구현 가능



#### React 컴포넌트
1. React 컴포넌트는 데이터를 받고 화면에 표시할 내용을 반환.
2. 사용자가 입력란에 입력하는 것과 같이 상호작용에 응답하여 새 데이터 전달 가능.
3. React는 새 데이터와 일치하도록 화면을 업데이트함.



# 2025.03.13 2주차

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