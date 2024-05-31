---
layout: post
title: "[React] npm error enoent ENOENT: no such file or directory 에러"
category:
- CS
- React
tags:
- React
- Debug
date: 2024-06-01 00:36 +0900
---
# npm error enoent ENOENT: no such file or directory, lstat 'C:\Users\yeoub\AppData\Roaming\npm'

## 콘솔 내용
```console
"C:\Program Files\nodejs\npx.cmd" --yes create-react-app@latest .
npm error code ENOENT
npm error syscall lstat
npm error path C:\Users\yeoub\AppData\Roaming\npm
npm error errno -4058
npm error enoent ENOENT: no such file or directory, lstat 'C:\Users\yeoub\AppData\Roaming\npm'
npm error enoent This is related to npm not being able to find a file.
npm error enoent

npm error A complete log of this run can be found in: C:\Users\yeoub\AppData\Local\npm-cache\_logs\2024-05-31T14_31_02_115Z-debug-0.log
Done
```

## 에러 원인
node.js를 처음 설치했을 때 발생할 수 있다.

## 해결 방법
문제가 발생한 폴더 위치 `C:\Users\yeoub\AppData\Roaming`에 가서 `npm`폴더를 생성하면 된다.
