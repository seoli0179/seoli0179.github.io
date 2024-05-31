---
layout: post
title: "[React] react-scripts는 실행할 수 있는 배치파일이 아닙니다 오류"
category:
- CS
- React
tags:
- React
- Debug
date: 2024-06-01 00:32 +0900
---
# 'react-scripts'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는 배치 파일이 아닙니다.

## 콘솔 내용
```console
"C:\Program Files\nodejs\npm.cmd" start

> untitled@0.1.0 start
> react-scripts start

'react-scripts'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는
배치 파일이 아닙니다.

Process finished with exit code 1
```

## 원인

주로 Git에서 Clone 했을 때 발생하는 에러인데,  
.gitignore 파일에 node_modules 폴더가 제외되어 다운로드 받지 못하기 때문에 발생한다.

## 해결 방법

`npm install` 을 다시 해주면 된다.

```console
npm install
npm start
```

이때 Run Configurations 도 지워져 있을 수 있는데 다시 설정하면 된다.
- package.json
- command -> run
- Scripts -> start
- Node interpreter -> node.exe
- Package manger -> npm.cmd
