---
layout: post
title: "[CSS] hover시 이미지 변경 issue"
excerpt: "CSS hover시 이미지 변경"

categories:
  - CSS
tags:
  - [CSS]

toc: true
toc_sticky: true

date: 2022-11-10
last_modified_at: 2022-11-10
---

<center><img width="70" alt="스크린샷 2022-10-14 오후 2 36 33" src="https://user-images.githubusercontent.com/85756211/212245770-bf99fe14-ab73-41ed-800d-cec7899ecc0d.png"/></center>
<center><img width="70" alt="스크린샷 2022-10-14 오후 2 36 33" src="https://user-images.githubusercontent.com/85756211/212245782-28876b94-b930-436c-90c9-07597d772664.png"/></center>
검은 history 아이콘을 hover시에 파란 history 아이콘으로 변경시키는 작업 ㅇuㅇ

평소에 자주 써보기도하고 한번도 어려움을 겪어본 적이 없는데 당황했다.

### 회색 이미지만 적용되어있던 처음 코드

```jsx
<Icon src={검정아이콘}></Icon>;

const Icon = styled.img`
  어쩌구: 저쩌구;
`;
```

이때는 width값만 주고 height값을 안주기도 했고

hover시에 src를 바꿔주면 되겠다고 생각했었다.

하지만 구글링해보니 css를 이용해서 src를 바꾸는 방법은 없었다.

### 변경한 코드

img 태그를 div로 바꾸어주고 hover될 때에는 background url을 바꾸어 주었다.

이때에도 `background-size:cover` 를 안적으면 사진이 div에 딱 맞게 꽉 들어차지가 않기 때문에

꼭 작성해 주어야 한다.

```jsx
<Icon></Icon>;

const Icon = styled.div`
  width: 25px;
  height: 25px;
  background-size: cover;
  background:url(${검정아이콘}) &:hover {
    background: url(${파란아이콘});
    background-size: cover;
    cursor: pointer;
  }
`;
```

[참고](http://daplus.net/html-css-img-hover%EC%97%90%EC%84%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-src-%EB%B3%80%EA%B2%BD/)
