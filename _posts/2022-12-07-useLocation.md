---
layout: post
title: "[React] useLocation, useParams의 차이"
excerpt: "useLocation, useParams의 차이"

categories:
  - React
tags:
  - [React]

toc: true
toc_sticky: true
date: 2022-12-07
last_modified_at: 2022-12-07
---

react router dom의 hook useLocation만 써봤는데, useParams도 비슷한 역할을 하는 것 같다.

### useParams

useParams 훅의 리턴값은 path parameter 정보를 담고있는 객체이다.

```
{*: "monsteroffice/dashboard"}
```

<center><img width="80%" alt="스크린샷 2022-10-14 오후 2 36 33" src="https://user-images.githubusercontent.com/85756211/212584726-0e01458a-81d3-4416-a02f-76b751fc294a.png"/></center>

왜 main/monsteroffice/dashboard가 아니고 monsteroffice/dashboard가 나오는거지?

→ `<Route path>`에 작성해둔 url params가 나온다

### useLocation

useLocation 훅의 리턴값은 경로의 정보를 갖고있는 객체이다.

```jsx
{
pathname:'/main/monsteroffice/dashboard',
search:'',
hash:'',
state:null,
key:"pi4l2ra5"
}
```

location 객체 내에 담긴 pathname: 현재 경로 값

search: 현재 경로의 query parameter 값

### 참고

[useNavigate]('https://reactrouter.com/en/main/hooks/use-navigate') <br/>
[useParams]('https://reactrouter.com/en/main/hooks/use-params')
