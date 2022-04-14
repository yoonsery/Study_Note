# PWA

Progressive Web Application
새롭고 강력한 소프트웨어 앱을 만드는 방식

html, css, js로 만든 웹앱을 모던한 웹 브라우저 APIs와 결합해서
크로스 플랫폼에서 동작하는 어플리케이션을 쉽게 만들 수 있다

- 접근성이 높은 웹앱의 장점
- 플랫폼 API를 사용할 수 있는 네이티브 앱의 장점

### powerful web applications 에 대한 컨셉의 등장

- 아이폰 출시 때 스티브잡스에 의해

- `Speed Simplicity` 웹코드로 어플리케이션을 만드는 장점

  - [x] 별도의 SDK가 필요하지 않음
  - [x] Release, Upgrade 때 복잡한 절차를 거치지 않아도 됨
  - [x] cross-platform 다양한 플랫폼에서 동시에 출시가능

- new class of web apps (크롬의 개발자가 새로운 클래스의 웹어플리케이션 언급)

- [x] responsive web design 컨텐츠가 유동적으로 반응할것
- [x] service workers 사용
- [x] app manifest 사용할 것
- [x] push notification 사용할 수 있을 것
- [x] native app-like capabilities
- [x] **사용자들의 디바이스에 설치가 가능하도록 만들 것**

---

### Project Fugu

google, microsoft, intel 의 web capabilities project

어떻게 하면 브라우저 API를 통해서 플랫폼에서 필요한

- 파일접근
- 카메라 제어
- 클립보드 접근
- 연락처 자동으로 런칭 등

다양한 기능을 할 수 있도록 할 건지 개발중

### 제약사항

- 새롭게 추가되는 브라우저 API들은 특정 브라우저나, 예전 버전에서는 사용할 수 없다
- 파이어폭스는 데스크탑용 브라우저에서는 pwa 지원하지 않음, 안드로이드에서만 지원
- 애플스토어에서는 pwa를 거부중이나 사파리를 통해서 설치할 수 있다
- 네이티브 앱처럼 모든 플랫폼에서 pwa를 사용할 수 없다 (네이티브 앱처럼 만들기엔 제약)

## Tools

### PWA builder

마이크로 소프트사에서 만든 오픈소스 프로젝트
웹사이트를 pwa로 전환할 때 어떤지 검토해주고 빠진 부분들을 자동으로 채워줌

### Workbox

구글이 pwa를 위한 서비스 워커를 자동으로 만들어주는 라이브러리를 만듦

### Maskable.app

더 나은 pwa 사용성을 위한 어댑티브 아이콘을 디자인할 수 있는 툴

---

# PWA를 만드는 법 (4)

1. 웹코드로 만든 웹사이트 or 웹어플리케이션이 필요

2. https를 이용해서 서비스가 제공이 되어야 함(보안이 중요한 이슈)

3. Application Manifest가 있어야 함
   :JSON 포맷으로 된 텍스트 파일, 웹어플리케이션에 대한 여러가지 정보들이 담겨있는 파일들이 있어야 함
   이 매니페스트를 이용해서 다양한 기기들에 pwa어플리케이션을 설치할 수 있도록 도와줌

4. Service Worker가 있어야 함
   :JS로 작성할 수 있는 스크립트, 어플리케이션에서 서버와 데이터를 주고 받을 때
   중간에서 그 모든 요청들을 통제하고 관리할 수 있다 So, '어떤 특정한 네트워크 요청과
   반응에 한해서 특정부분을 따로 저장을 해놨다가 오프라인 상태일 때 저장해둔 데이터를
   보여주자', '이런 최신 뉴스들은 미리미리 패칭을 해와서 저장을 미리 해놓으면 사용자가
   어플리케이션을 켜자마자 우리의 데이터를 보여줄 수 있도록 하자'
   ⟶ 성능이 좋은 어플을 만들기 위해서 서비스 워커를 사용할 수 있다

PWA builder로 빠진 부분 확인 ⟶ 필요한 부분 채워넣기 ⟶ 다시 빌더로 적합한지 확인

## [TestSite](https://competent-curran-66e516.netlify.app/)

[web.dev](https://web.dev/install-criteria/)
pwa를 만들기 위해 manifest에 어떤 내용이 들어가야하는지 설명된 글

1. PWA builder에서 https로 시작하는 사이트 넣고 검사 시작

2. 검사 결과 후 Manifest Option 탭에가서 필요한 정보 추가함

- icon 업로드, display: standalone으로 설정 후 Done 버튼 클릭

3. Service Worker 탭으로 이동

- 오프라인 페이지 추가 후 Done 클릭
- 그 다음 Next 클릭
- Generate 클릭

4. 시키는 대로 파일 옮기고 이미지폴더 옮기고 offline.html 만들고, 다시 저장, 배포

- 새로 저장된 사이트 다시 빌더에 돌려보기, 적합점수 받으면 next 버튼 클릭

---

## PWA

- [x] Responsive
- [x] Installable
- [x] Safe
- [x] App-like Interactions
- [x] Linkable
- [x] Discoverable
- [x] Fresh
- [x] Re-engageable
- [x] Connectivity Independent
