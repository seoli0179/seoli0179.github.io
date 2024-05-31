---
layout: post
title: "[Git] Github에 잘못 올라간 파일 삭제"
category:
- CS
- Git
tags:
- Git
- Command
date: 2024-06-01 01:04 +0900
---
# Github에 잘못 올라간 파일 삭제

## 명령어

```console

// 원격 저장소와 로컬 저장소에 있는 파일을 삭제한다.
$ git rm [File Name]       // 파일 삭제
$ git rm -r [Folder Name]  // 폴더 삭제


// 원격 저장소에 있는 파일을 삭제한다. 로컬 저장소에 있는 파일은 삭제하지 않는다.
$ git rm --cached [File Name]       // 파일 삭제
$ git rm -r --cached [Folder Name]  // 폴더 삭제
$ git rm -r --cached .idea\


// 버전 관리에서 완전히 제외하기 위해서는 반드시 commit 명령어를 수행해야 한다.
$ git commit -m "Fixed untracked files"


// 원격 저장소(origin)에 push
$ git push origin master

```


