---
layout: post
title: package.json과 package-lock.json
date: 2025-01-14 14:02 +0900
description: package.json과 package-lock.json
category: [Study, Node.js]
tags: []
pin: false
math: true
mermaid: true
---
## package.json
- `Node.js` 프로젝트에서 사용되는 파일
- 프로젝트 이름, 버전, 설명, 작성자, 라이센스, 의존성 목록이 포함
- `npm install` 명령어를 통해서 `package.json`에 포함된 의존성이 자동으로 설치
- 의존성 선언 시 `version range`가 사용된다
    - `version range` : 특정 버전을 명확하게 지정하는 것이 아니라 특정 버전 이상을 사용함을 표시

## package-lock.json
- 의존성 트리에 대한 정보
- 파일이 작성된 시점의 의존성 트리가 재생성 될 수 있다

## package-lock.json이 필요한 이유
- 대부분의 경우 `package.json` 만으로도 문제가 발생하지 않지만 협업 시에 간혹 버전 문제가 발생할 수 있다
- `package-lock.json`은 정확한 버전 정보를 가지고 있어 설치 당시 의존성을 재현하므로 협업시 일관성 유지에 필요하다
- 따라서 `.gitignore`에 포함시키지 않는다
- `package.json`에 정확한 버전명을 명시하지 않는 이유는 프로젝트에 사용된 패키지의 크고 작은 버그 수정이 이루어 질때마다 `package.json`의 버전을 수정해야하는 번거로움이 생길 수 있기 때문

## 참고자료
- https://dev-ellachoi.tistory.com/65
- https://docs.npmjs.com/cli/v9/configuring-npm/package-json
- https://docs.npmjs.com/cli/v9/configuring-npm/package-lock-json