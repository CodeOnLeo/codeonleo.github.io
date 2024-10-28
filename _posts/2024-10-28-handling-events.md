---
layout: post
title: Handling Events
date: 2024-10-28 14:35 +0900
description: 리액트의 이벤트 처리
category: [React]
tags: []
pin: false
math: true
mermaid: true
---
# Handling Events

## Event 다루기
- DOM 의 Event
  ```js
  <button onclick="activate()">
    Activate
  </button>
  ```

- React의 Event
  ```jsx
  <button onClick={activate}>
    Activate
  </button>
  ```

## Event Handler
- 어떤 사건이 발생하면 사건을 처리하는 역할
- Event Listener라고도 한다


```jsx
class Toggle extends React.Component {
  constructor(props){
    super(props);

    this.state = { isToggleOn : true };

    // callback에서 'this'를 사용하기 위해서는 바인딩을 필수적으로 해줘야 합니다.
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick(){
    this.setState(prevState => ({
      isToggleOn: !prevState.isToggleOn
    }));
  }

  render(){
    return(
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? '켜짐' : '꺼짐'}
      </button>
    );
  }
}
```