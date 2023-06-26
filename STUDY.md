## 1.0 Library vs Framework

- nextjs는 framework에 속함
- nextjs가 우리의 코드를 사용해서 실행
  - 우리가 수정하는 부분은 nextjs의 일부 기능임
  - pages 밑에 파일을 생성하면 그 파일이 /, /about 의 위치에 해당하는 html 페이지가 됨
  - about.js에 이렇게 해두면 /about으로 이동했을 때 `about us`라는 글자가 나옴
    ```
        export default function Potato() {
            return "about us";
        }
    ```
