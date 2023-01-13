---
layout: post
title: "[JavaScript] 정규표현식 test 결과 에러"
excerpt: "정규 표현식 test 에러"

categories:
  - JavaScript
tags:
  - [JavaScript]

toc: true
toc_sticky: true=
date: 2022-12-06
last_modified_at: 2022-12-06
---

나의 멘탈을 탈탈 깨부셔버리는 도저히 이해가 안되는 코드가 생겼다.. 😬

같은 코드가 forEach문 밖에서는 정규 표현식이 true가 나오는데

forEach문 안에서는 false가 나오는 기이한 현상을 발견했다.

### 문제의 코드

```
const { pathname, state } = useLocation();

  let fullPath = pathname;
  const regexExp =
    /^[0-9a-fA-F]{8}\b-[0-9a-fA-F]{4}\b-[0-9a-fA-F]{4}\b-[0-9a-fA-F]{4}\b-[0-9a-fA-F]{12}$/gi;
  let routes = [];
  let splitedPathArray = fullPath.split("/");

  let arr = [];

  splitedPathArray.forEach((el, idx) => {
    const result = regexExp.test(el);
    regexExp.lastIndex = 0;   // <- 이 부분이 꼭 필요하다!!!
    if (result) {
      console.log("돌아가는 구역", el, idx);
    } else {
      console.log("통과 못하는 구역", el, idx);
      arr.push(el);
    }
  });
```

## 원인과 해결 방법

이 문제는 정규표현식 `g` 플래그(flag)를 달았을 때 발생하는 문제다.

`g` 플래그를 빼면 해결된다.

정규 표현식의 g플래그는 표현식을 만족하는 하나 이상의 값을 찾는다. **문자열에서 일치하는 값을 갖게된 시점의 포지션(lastIndex)을 기억**하고 있고, 다음 검증 시 해당 인덱스에서부터 검색을 시작한다.

그래서 단순하게 여러 문자열을 하나씩 정규식을 통해 검증하려면 `g` 플래그를 사용하지 않아야한다.

아니면 매 과정마다 lastIndex를 0으로 초기화하면 된다.

그러면 매번 처음 문자열의 포지션부터 검색을 수행하기 때문에 원하는 결과를 얻을 수 있다.

[참고]('https://jootc.com/p/202112103833')
