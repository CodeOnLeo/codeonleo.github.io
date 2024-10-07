---
layout: post
title: State and Lifecycle
date: 2024-10-07 22:09 +0900
description: 리액트 state와 생명주기
category: [React]
tags: []
pin: false
math: true
mermaid: true
---
# State and Lifecycle

## State와 Lifecycle의 정이
### State
- 리액트 컴포넌트의 변경 가능한 데이터
- 사전에 정의 된 것이 아니라 리액트 컴포넌트를 개발하는 개발자가 직접 정의하여 사용
- 렌더링이나 데이터 흐름에 사용되는 값만 State에 포함 시켜야 한다
  - State가 변경될 경우 컴포넌터가 재렌더링 된다
  - 불필요하게 재랜더링 되는 경우를 방지
  - State에 포함되지 않아야 하는 것들은 컴포넌트의 인스턴스 필드로 정의하면 된다
- State는 자바스크립트 객체이다
- State는 직접 수정하면 안된다
  - setState 함수 사용

### Lifecycle
![리액트 클래스 컴포넌트 생명주기](/assets/img/lifecycle.png)

- 리액트 컴포넌트가 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라진다
