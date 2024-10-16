---
layout: post
title: Rendering Elements
date: 2024-09-29 16:17 +0900
description: Elements 소개
category: [React]
tags: []
pin: false
math: true
mermaid: true
---
# Rendering Elements

## Elements란?
- 리액트 앱을 구성하는 가장 작은 블록들
- 실제 브라우저 DOM에 존재하는 것은 DOM Elements
- 리액트의 virtual DOM에 존재하는 것은 리액트 Elements

## Elements의 생김새
- 자바스크립트 객체 형태로 존재
- 컴포넌트 유형과 속성 내부의 모든 자식에 대한 정보를 포함하고 있는 일반적인 자바스크립트 객체
- Rendering 전
  ```js
  {
    // type에 html 태그 이름이 문자열로 들어가는 경우
    // elements는 해당 태그 이름을 가진 DOM 노드
    // type에 리액트 컴포넌트가 들어가면
    // 컴포넌트의 elements를 먼저 생성해서 합친다
    type: 'button',
    // 속성
    props:{
      className: 'bg-green',
      children:{
        type: 'b',
        props: {
          children: 'Hello, element!'
        }
      }
    }
  }
  ```
- Rendering 된 후
  ```html
  <!-- 모든 리액트 컴포넌트는 최종적으로 HTML의 형태가 된다-->
  <button class='bg-green'>
    <b>
      Hello, element!
    </b>
  </button>
  ```

## Elements의 특징
- 불변성 : Elements 생성 후에는 children이나 attributes를 바꿀 수 없다
- 화면에 변경된 Elements를 보여주는 것은 기존 Elements를 변경하는 것이 아니라 새로운 Elements를 만들어서 기존의 Elements와 바꿔치기 하는 것

## Elements 렌더링하기
- Root DOM Node
  ```html
  <div id="root"></div>
  ```

- Root DIV에 렌더링하기
  ```jsx
  const element = <h1>안녕, 리액트!</h1>;
  // virtual DOM에서 실제 DOM으로 이동
  ReactDOM.render(element, document.getElementById('root'));
  ```

- 렌더링된 Elements를 업데이트 하기
  ```jsx
  function tick(){
    const element = (
      <div>
        <h1>안녕, 리액트!</h1>
        <h2>현재 시간: {new Date().toLocaleTimeString()}</h2>
      </div>
    );

    ReactDOM.render(element, document.getElementById('root'));
  }

  setInterval(tick, 1000);
  ```

### ERROR

> Uncaught TypeError: react_dom_clientWEBPACK_IMPORTED_MODULE_1.render is not a function   


- 원인 : React 18 부터는 `ReactDOM.render()` 사용 불가 [React 17까지만 가능]

```jsx
  - setInterval(() => {
    ReactDOM.render(
      <React.StrictMode>
        <Clock/>
      </React.StrictMode>,
      document.getElementById('root')
    );
  }, 1000);
```

- 해결 : `ReactDOM.createRoot()` 사용

```jsx
const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(
  <React.StrictMode>
    <Clock />
  </React.StrictMode>
);
```