---
layout: post
title: "[React] 렌더링 최적화"
excerpt: "0706~ 0708 첫 렌더링 최적화"

categories:
  - React
tags:
  - [React, javascript, Github, Git]

toc: true
toc_sticky: true

date: 2022-07-08
last_modified_at: 2022-12-01
---

# 0706 (수)

컴포넌트가 렌더링 된다는 것은 누군가 그 함수(컴포넌트)를 호출해서 실행하는 것을 말한다.

컴포넌트가 리렌더링되는 경우

- 자신의 state가 변경될 떄
- 부모에게서 받는 props가 변경될 때
- 부모 컴포넌트가 변경될 때
- forceUpdate()가 호출될 때

# 0707 (목)

**React.memo**는 state의 변화는 알아차리지 못함, **Props**의 변화를 감지한다

→ state변화에 따른 렌더링 부분은 useCallback이나 useMemo를 사용해서 최적화를 해주어야한다.

컴포넌트 자체를 React.memo로 최적화를 해도 props값에 변화가 없는데 또 렌더링이 되는 경우가 있다

→ javascript 언어 특성상 객체 타입은 객체나 함수를 변수에 직접 저장하지 않고 주소값을 저장한다. props가 객체타입이면 React.Memo를 사용해도, 부모컴포넌트가 렌더링될때 객체props가 달라졌다고 인식하기 때문에 리렌더링이 일어난다.

→ 이럴 때 객체Props에 useMemo를 사용해준다

React Profiler를 이용해 **시간이 오래걸리는 컴포넌트**를 기준으로 메모이제이션을 시도함

### 참고

[useCallback,useMemo](https://velog.io/@syc765/useMemo-useCallback)
