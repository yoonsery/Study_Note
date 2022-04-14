## 코딩 잘하는 팁 3가지 클린코드

## `DRY` ( Don't Repeat Yourself )

<-> WET: Write Every Time, write everything twice, waste everyone's time

: DRY is about the duplication of knowledge, onf intent.
It's about expressing the same thing in two different places,
possiblly in two totally different ways

Every piece of knowledge must have a single, unambiguous,
authoritative representation within a system

로직, 지식, 의도, 비즈니스로직 이 모든 것들이 중복되지 않도록 하는 것 (광범위하다)
(단순히 코드 반복을 의미하지 않음)

## `KISS` ( Keep It Simple, Stupid )

: Most systems work best if they are kept simple rather than made
complicated; therefore, simplicity should be a key goal in design
and unnecessary complexity should be avoided

10줄짜리 코드를 가독성을 떨어뜨려 1줄짜리로 바꾸기보다
누구나 이해할 수 있도록 심플하고 간결하게 작성하는 것이 좋다
code, function, class, view(UI), service, system 모두
하나의(심플한) 기능을 가지게 만든다

```
function getFirst(arr, isEven) {
  return arr.find(x => (isEven ? x % 2 === 0 : x % 2 !== 0));
}
```

를 KISS로 바꾸면?

```
function getFirstOdd(arr) {
  return arr.find(x => x % 2 === 0);
}

function getFirstEven(arr) {
  return arr.find(x => x % 2 !==0);
}
```

UI에 대한 함수면 그것만 해당하는 로직이 있어야함
-> 비즈니스 로직을 담당하는 클래스를 따로 만들어서 관리

## YAGNI ( You Ain't Gonna Need It )

1. cost of carry, cost of delay
2. cost of repair
3. cost of building

- right feature, built right -> need 1
- right feature, built wrong -> need 1, 2
- wrong feature -> need 1, (2), 3

필요하지 않는 기능 x
사용하지 않는 기능 x
지나치게 미래지향적 x

깨끗하게 ✅
변경이 쉽게 ✅
유지보수 용이하게 ✅

system -> YAGNI 불필요한 코드 제거 -> KISS로 심플함 추가

---

## 서버사이드 렌더링

- Static site (90년대 중반)
  : 페이지내에서 다른 링크 클릭 -> 다시 서버에서 해당 페이지 HTML받아와서 페이지전체 업데이트

- iframe: 문서내에서 또 다른 문서를 담을 수 있는 아이프레임태그, 부분적으로 업데이트

- XMLHttpRequest (aka fetch): JSON이용해서 필요한 데이터만 가져옴

- AJAX (2005): json을 js를 이용해 동적으로 html요소 생성해서 페이지 업데이트,
  공식적으로 AJAX라는 이름을 가지게 됨 -> SPA (single page application)

## CSR ( Client Side Rendering )

: 클라이언트측에서 다 한다,

- 서버에서 인덱스라는 HTML파일을 클라이언트에 보냄 -> body안에 id=root만 있음
  -> 자바스크립트 링크를 서버로부터 다운받아 동적으로 html 생성

🚨

1. initial Loading may take too long
   (사용자가 첫 화면을 보기까지 시간이 오래 걸릴 수 있다)

2. Low SEO ( Search Engine Optimization )

---

## SSR ( Server Side Rendering )

: 웹사이트에 접속하면 서버에서 필요한 데이터를 모두 가져와서 HTML 파일을 만들고
-> 동적으로 제어할 수 있는 소스코드와 함께 클라이언트에게 보내줌

👍

1. initial page load is faster
   (CSR사용할 때 보다 첫번째 페이지로딩이 빨라짐)

2. Great(효율적인) SEO , (모든 컨텐츠가 HTML에 담겨있기 때문)

🚨

1. Blinking issue, Non-rich site interactions
   (사용자가 클릭-> 웹사이트를 서버에서 다시 전체적으로 받아오는 것과 동일하므로
   좋지않은 User experience겪을 수 있다)

2. Server side overhead ( 서버 과부하 ) - 사용자가 많을 수록

3. Need to wait before interacting
   (JS가 다운로드중이라 클릭해도 반응하지 않을 경우가 있다)

**TTV ( Time To View )**
**TTI ( Time To Interact )**

> CSR은 TTV : 사용자가 웹사이트를 볼 수 있음과 동시에 TTI 가 가능

> SSR은 TTV와 TTI의 공백기간이 긴 편이다

- CSR: 최종적으로 번들링해서 보내는준 JS파일을 어떻게 하면 효율적으로 많이 분할해서
  첫번째로 사용자가 보기위해서 필요한, 필수적인 아이만 보낼 수 있을지 고민해야함

- SSR: TTV, TTI의 단차를 줄이기 위해 어떤 노력을 할 수 있을지,
  매끄러운 UI, UX를 제공할 수 있을지 고민

---

> SSG ( Static Site Generation )

클라이언트 사이드렌더링에 특화된 라이브러리인 `React + Gatsby`:
리액트로 만든 웹어플리케이션을 정적으로 웹페이지를 미리 생성해서 서버에 배포해 놓을 수 있다

> SSR `React + Next.js`

: next.js는 서버사이드 렌더링을 지원하는 라이브러리였는데
요즘은 SSG도 지원하고 ( static generation ) ssr, csr을 잘 섞어서 지원함
no pre-rendering, pre-rendering
