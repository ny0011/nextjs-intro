## 1.0 Library vs Framework

- nextjs는 framework에 속함
- nextjs가 우리의 코드를 사용해서 실행
  - 우리가 수정하는 부분은 nextjs의 일부 기능임

## 1.1 Pages

- pages 밑에 파일을 생성하면 그 파일이 /, /about 의 위치에 해당하는 html 페이지가 됨
- `about.js`에 이렇게 해두면 /about으로 이동했을 때 `about us`라는 글자가 나옴
  - 함수의 이름은 상관없고 파일 이름이 실제로 page URL 이름이 됨
  - 화면으로 보여주는 부분의 함수 앞에 항상 `export default` 붙여주기
  ```
      export default function Potato() {
          return "about us";
      }
  ```
- 예외로 `index.js`는 /으로 이동함
  - /index 라는 URL은 없음
- useState 같은 React 기능을 사용하고 싶을 때만 import React 하면 됨

## 1.2 Static Pre Rendering

- Client-Side Rendering : 브라우저가 내 코드와 react를 다운 받고 react가 내 코드를 렌더링 함
  - create-react-app으로 만들어진 웹 페이지의 태그에는 보통 `<div id=root>` 만 있음
- Server-Side Rendering : 서버에서 웹 페이지를 렌더링해서 태그를 전송함
  - 웹 페이지의 태그에 내용이 있음
  - 사용자가 느린 인터넷 환경에 있어도 흰 화면이 아니라 내용을 확인할 수 있음

## 1.3 Routing

- 링크를 할 때 `a` 태그로 하면 경고 메시지가 나옴
  - https://nextjs.org/docs/messages/no-html-link-for-pages
  - a 태그를 사용해서 페이지를 이동하면 전체 페이지 새로 고침이 발생함
  - 내부 페이지 이동은 next/link의 `Link` 태그를 사용해서 페이지 이동을 빠르게하고 렌더링을 또 하지 않아도 됨
  - `Link` 태그 안에 `a` 태그를 넣으면 에러 메시지가 나옴
    - https://nextjs.org/docs/messages/invalid-new-link-with-extra-anchor
    - `npx @next/codemod new-link .` 이걸 실행해서 지금 폴더에 있는 new-link를 업그레이드하면 `Link` 태그에도 스타일 적용을 할 수 있다

## 1.4 CSS Modules

- CSS module 패턴을 사용하면 일반적인 CSS를 사용할 수 있게 됨
- 태그에 className을 추가할 때 이름을 `""`로 쓰는게 아니라 object의 property에 접근하는 방식으로 사용함
  - ex) `className={style.nav}`
  - next.js가 임의로 클래스 이름을 생성해줌
- className이 여러 개면? 두 가지 방식이 있음
  - 1. ``과 ${} 을 쓰는 방법
    ```
      className={`${styles.link} ${
          router.pathname === "/" ? styles.active : ""
        }`}
    ```
  - 2. 리스트에 넣고 .join() 사용하는 방법
    ```
      className={[
          styles.link,
          router.pathname === "/about" ? styles.active : "",
        ].join(" ")}
    ```
- 어쨌든 불편함
  - 파일을 하나 새로 만들어야하고 className을 기억해야 됨
