---
layout: post
title: "[TypeScript] error handling"
excerpt: "typeScript error handling"

categories:
  - TypeScript
tags:
  - [TypeScript, JavaScript]

toc: true
toc_sticky: true

date: 2022-10-16
last_modified_at: 2022-10-16
---

### 📌VS code에서 type script 서버 재시작

cmd + shift + p → restart ts server

### 📌데코레이터는 어떻게 타입을 지정해야하나 ㅎㅎ

decorator는 class, class내부에서만 사용할 수 있다.

decorator는 class, class내부의 property,accessor,method,parameter에 사용할 수 있다

아 ㅇ\_ㅇ 이럴수가 이럴수가 이럴수가?!?!?!??!

```jsx
interface arr {
  id?: number;
  status?: string;
  "@timestamp"?: string;
}
```

그냥 문법 문제였다 ㅎㅎ..

[참고](https://bobbyhadz.com/blog/typescript-property-or-signature-expected)

### 📌Error의 type은 뭘까?

<center><img width="791" alt="스크린샷 2022-10-14 오후 2 36 33" src="https://user-images.githubusercontent.com/85756211/212241995-9ad1778f-b161-4885-b49f-47ac3dd25bf8.png"/></center>
Object라고 하는데 ㅎㅎ..
`const [error, setError] = useState<Object | null>(null)` 를 쓰니까 null에러는 없어졌다.
<center><img width="200" alt="스크린샷 2022-10-14 오후 2 39 52" src="https://user-images.githubusercontent.com/85756211/212242099-9d5324c4-f98e-4eae-ac05-4685b2c90e65.png"></center>
unknown은 에러가 나는 함수부분의 parameter에 type을 지정 안해줘서 일어난 에러였다

catch문 안에서의 parameter엔 any나 unknown type만이 들어갈 수 있다고 한다. 터미널피셜이다 ㅎ

## 📌Variable inputArguments is used before assigned

난 분명 선언을 했는데 왜 선언을 안했다고 나오는걸까? 🤷🏻‍♀️

→ null이 아님을 명시해주어야 하기 때문이다. 처음 선언부분에 `!` 하나를 붙였더니 해결됐다 😣

```
let inputArguments!: string | obj2;
```

[variable is used before being assigned even though it is assigned]('https://lightrun.com/answers/microsoft-typescript-variable-is-used-before-being-assigned-even-though-it-is-assigned')
