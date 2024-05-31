---
layout: post
title: "[React] @babel/plugin-proposal-private-property-in-object 의존성 경고"
category:
- CS
- React
tags:
- React
- Debug
date: 2024-05-31 20:44 +0900
---
# [React] @babel/plugin-proposal-private-property-in-object 의존성 에러
babel-preset-react-app이라는 패키지가 @babel/plugin-proposal-private-property-in-object라는 패키지를 의존성으로 선언하지 않고 사용하고 있다는 경고 메시지 발생

```console
One of your dependencies, babel-preset-react-app, is importing the "@babel/plugin-proposal-private-property-in-object" package without declaring it in its dependencies. This is currently working because "@babel/plugin-proposal-private-property-in-object" is already in your node_modules folder for unrelated reasons, but it may break at any time.

babel-preset-react-app is part of the create-react-app project, which is not maintianed anymore. It is thus unlikely that this bug will
ever be fixed. Add "@babel/plugin-proposal-private-property-in-object" to your devDependencies to work around this error. This will make this message go away.
```

package.json에 의존성 추가 후, npm install

```
"devDependencies": {
  "@babel/plugin-proposal-private-property-in-object": "^7.14.5",
  // 다른 devDependencies
}
```
{: file='/package.json'}

```console
npm install @babel/plugin-proposal-private-property-in-object --save-dev
```

***

이번에는 @babel/plugin-proposal-private-property-in-object 패키지가 ECMAScript 표준에 병합되어 deprecated 되었다는 경고 메시지 발생

```console
C:\Users\yeoub\AppData\Roaming\JetBrains\IntelliJIdea2023.3\node\node-v18.15.0-win-x64\npm.cmd install
npm WARN deprecated @babel/plugin-proposal-private-property-in-object@7.21.11: This proposal has been merged to the ECMAScript standard and thus this plugin is no longer maintained. Please use @babel/plugin-transform-private-property-in-object instead.

added 1 package, changed 1 package, and audited 1557 packages in 3s

262 packages are looking for funding
  run `npm fund` for details

8 vulnerabilities (2 moderate, 6 high)

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.

Process finished with exit code 0
```

@babel/plugin-proposal-private-property-in-object 패키지 삭제하고,  
@babel/plugin-transform-private-property-in-object 패키지 설치

```
"dependencies": {
    // "@babel/plugin-proposal-private-property-in-object": "^7.14.5", // 삭제
    "@babel/plugin-transform-private-property-in-object": "^7.24.6",
    // 다른 devDependencies
  },
```
{: file='/package.json'}

```console
npm install @babel/plugin-transform-private-property-in-object --save-dev
npm uninstall @babel/plugin-proposal-private-property-in-object
```
