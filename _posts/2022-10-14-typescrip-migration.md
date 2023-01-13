---
layout: post
title: "[TypeScript] javascript 프로젝트 typescript 마이그레이션"
excerpt: "javascript 프로젝트 typescript 마이그레이션"

categories:
  - TypeScript
tags:
  - [TypeScript, JavaScript]

toc: true
toc_sticky: true

date: 2022-10-14
last_modified_at: 2022-10-14
---

### 📌 package download

기존 js프로젝트에서 ts를 추가하는 경우 설치해주어야 한다

```jsx
npm install --save typescript @types/node @types/react @types/react-dom @types/jest
```

- typescript

타입스크립트 파일을 js파일로 컴파일할 수 있도록 만드는 컴파일러

- @types/node

node에서 typescript를 사용할 때 모든 유형 정의를 로드할 때 사용한다

typescript 2.x이상 버전에서는 필수로 사용한다

- @types/react

react에서 typescript를 사용할 때 모든 유형 정의를 로드할 때 사용한다

`types/react-dom, types/jest` 등 패키지도 같은 이유로 사용한다.

### 📌 tsconfig.json

위 명령어를 사용해서 패키지를 설치한 후에는

tsconfig.json을 만들어 주어야한다.

tsconfig.json파일이 위치한 디렉토리는 ts프로젝트의 **루트 디렉토리**가 된다.

타입스크립트는 자바스크립트로 컴파일하는 과정이 필요한데, tsconfig.json 파일을 어떻게 js로 컴파일할지 설명해주는 역할을 한다.

[Documentation - What is a tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

이제 app.js와 index.js를 ts로 바꿔주면 index.ts에서 에러가 난다

```jsx
Property 'createRoot' does not exist on type 'typeof
import("/code/my-app/node_modules/@types/react-dom/index")'. TS2339
```

이런 에러가 나는데, createRoot라는 속성이 없기 때문에 나는 에러이다.

root를

```jsx
const root = ReactDOM.createRoot(
  document.getElementById("root") as HTMLElement
);
```

이렇게 변경해주면 HTMLElement라는 type이 정해졌기 때문에 오류가 해결된다.

이제 나머지 js파일들을 ts로 바꾸어주면서 생기는 타입 에러들을 타입을 명시해주면서 하나하나 해결해나가면

ts 프로젝트로 변경시킬 수 있다! 💪

## 참고

[React 프로젝트 JS -> TS로 변환하기](https://codermun-log.tistory.com/m/599)

[JS에 TS 적용하기](https://joshua1988.github.io/ts/etc/convert-js-to-ts.html#%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%94%EB%93%9C%EC%97%90-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A5%BC-%EC%A0%81%EC%9A%A9%ED%95%A0-%EB%95%8C-%EC%A3%BC%EC%9D%98%ED%95%B4%EC%95%BC-%ED%95%A0-%EC%A0%90)
