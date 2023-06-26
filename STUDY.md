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
