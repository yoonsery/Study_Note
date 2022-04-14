## Semantic Tags (Semantic Markup)

중요한 이유

1. SEO
2. Accessibility (웹접근성)
3. Maintainability

## <article> vs <section>

- article

  - 블로그 포스트에서 포스트 하나, 신문기사에서 기사 하나에 해당
  - 아티클 자체를 `독립적`으로 보여줬을 때 문제가 없을 때 사용

- section
  - 아티클 안에 있는 내용들 중에 `서로 연관있는 내용들을 묶어줄 때`
  - 메인 안에 섹션이 있을 수 있고 섹션 안에 아티클들이 모여있을 수도 있음

## <i> vs <em>

둘다 이탤릭체로 쓰이지만
i 는 시각적으로만 이탤릭체
em 은 강조하는 이탤릭체

## <b> vs <strong>

둘다 볼드체로 쓰이지만
b는 시각적으로만 볼드
strong은 정말 중요한 볼드체

## <ol> vs <ul> vs <dl>

- ol: 순서가 중요할 때 쓰는 목록
- ul: 순서가 없는 목록
- dl: description list, 정의, 설명 목록
  어떤 단어에 대해서 설명이 묶여있을 때 그 목록을 나타낼 때 사용
  - dt (description term) 단어
  - dd (description detail) 해당하는 설명

## <img> vs `background-image`

이미지가 웹페이지 안에서 하나의 중요한 요소로 자리잡고 있으면 <img>
문서의 내용과는 별개로 스타일링 목적을 위해 배경이미지로 사용되고
문서의 일부분이 아니라면 `background-image`

## <button> vs <a>

- button : 사용자의 특정한 액션을 위해 사용

  - review, vote, login, sign up, take quiz

- a tag : 사용자가 클릭했을 때 다른 페이지나 페이지 내 어딘가로 이동할 때 사용
  - 링크

## <table> vs CSS

( 행 + 열 ) 을 이용한 데이터를 표현할 때는 <table>
그리드형식으로 표현하기 위해서는 사용하지 말자
스타일링을 위해서는 flex, grid로 사용할 수 있음
