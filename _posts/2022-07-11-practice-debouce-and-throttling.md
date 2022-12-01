---
title: "[JavaScript] debounce,throttling"
excerpt: "debounce와 throttling을 연습해보자!"

categories:
  - JavaScript
tags:
  - [React, CSS, javascript, Github, Git]

toc: true
toc_sticky: true

date: 2022-07-11
last_modified_at: 2022-12-01
---

# 0711 Git commit 계정 바꾸기

git log로 보니 내가 남긴 커밋이 다른 분 계정으로 설정되어 있었다

커밋만 했을 경우에 author를 바꾸는 방법과

push까지 한 후에 author를 바꾸는 방법이 다른데, 다행히 나는 커밋 직후에 바꾸었다

```jsx
git commit --amend --author="이름 <이메일>" 	//사용자 계정변경
```

이러고 나면 vim으로 무슨 창이 뜨는데 vim을 안써봐서 굉장히 당황했다 ㅎ..

esc를 누르고나면 명령모드로 들어가는데 이 상태에서 :를 누르고 w를 눌러 저장을해 다행히 작성자 계정을 나로 바꾸었다.

## 참고

[왕초보를 위한 vim 사용법](https://zeddios.tistory.com/122)
[Git commit 계정 바꾸기](https://raon0229.tistory.com/87)

## Debounce & Throttling

DOM이벤트를 기반으로 실행하는 이벤트를 제어하는 방법

(시간이 지남에 따라 함수를 몇번이나 실행할지 제어하는 기술)

- **Debounce**

이벤트를 그룹화하여 특정 시간이 지난 후 하나의 이벤트만 발생하도록 하는 기술

(연이어 호출되는 함수중 마지막 또는 처음만 호출하는 것)

- **Throttle**

이벤트를 일정한 주기마다 발생하도록 하는 기술

(마지막 함수가 호출된 후 일정 시간이 지나기 전에 다시 호출되지 않는 것)

# 📌 Intersection observer를 이용한 무한 스크롤 구현

Intersection observer는 웹API이다.

기본적으로 브라우저 뷰포트와 설정한 요소(element)의 교차점을 관찰하며, 요소가 뷰포트에 포함되는지 포함되지 않는지, 사용자 화면에 지금 보이는 요소인지 아닌지를 구별하는 기능을 제공한다.

## 학습 **목적**

이 기능은 비동기적으로 실행되기 때문에 scroll같은 이벤트 기반의 요소 관찰에서 발생하는 렌더링 성능이나 이벤트의 연속 호출같은 문제 없이 사용할 수 있다.

## 왜 사용할까?

### 1. debounce,throttle 사용을 하지 않아도 된다!!

### 2. reflow를 하지 않는다.

    스크롤 이벤트에서는 현재의 높이 값을 알기 위해 **offsetTop**을 사용하는데 정확한 값을 가져오기 위해 매번 layout을 새로 그리게 된다고 한다.

### 갑자기 생긴 의문점

→ offsetTop이 뭐람..🙄🙄🙄🙄🙄

### 무엇이 reflow를 유발시킬까?

- window resizing
- font 변화
- 스타일 추가, 제거 / css 가상class
- 내용 변화(input 박스에 텍스트 입력 등)
- js를 통한 DOM 동적 변화
- element에 대한 offsetWidth,offsetHeight(화면에서 보이는 좌표) 계산시
- 스타일 attribute 동적 변화

화면 전체와 요소가 상쇄되는 영역 = offset 영역 = 요소의 전체 영역

offsetParent - 위치 계산에 사용되는 가장 가까운 조상 요소

offsetTop - offsetParent 기준으로 바닥에서 얼마나 떨어져 있는지를 나타내는 값

### 참고

[Offset, Client, Scroll 개념](https://serzhul.io/JavaScript/offset,-client,-scroll-%EA%B0%9C%EB%85%90-%EC%A0%95%EB%A6%AC/)
