---
title: 시작하기
description: >-
    Chirpy의 기본 사항을 다루는 포괄적인 개요로 시작하세요.
    이 문서를 통해 Chirpy 기반 웹사이트를 설치하고 구성하며 사용하는 방법과 이를 웹 서버에 배포하는 방법을 배우게 됩니다.
author: cotes
date: 2019-08-09 20:55:00 +0800
categories: [Blogging, Tutorial]
tags: [getting started]
pin: true
media_subpath: '/posts/20180809'
---

  

## 사전 준비

  

[Jekyll Docs](https://jekyllrb.com/docs/installation/)의 지침에 따라 기본 환경 설치를 완료하세요. 또한 [Git](https://git-scm.com/)도 설치되어 있어야 합니다.

  

## 설치

  

### 새 사이트 생성

  

이 테마를 위한 새로운 저장소를 만드는 방법은 두 가지가 있습니다:

  

- [**Chirpy Starter 사용**](#옵션-1.-Chirpy-Starter-사용) — 업그레이드가 쉽고, 관련 없는 프로젝트 파일을 격리하여 작성에 집중할 수 있습니다.

- [**GitHub Fork**](#옵션-2.-GitHub-Fork) — 커스텀 개발에 편리하지만 업그레이드가 어렵습니다. Jekyll에 익숙하고 이 프로젝트에 기여하거나 수정하려는 의지가 없으면 이 방법은 권장되지 않습니다.

  

#### 옵션 1. Chirpy Starter 사용

  

GitHub에 로그인하여 [**Chirpy Starter**](https://github.com/cotes2020/chirpy-starter)로 이동하여 <kbd>Use this template</kbd> > <kbd>Create a new repository</kbd> 버튼을 클릭하고, 새로운 저장소 이름을 `USERNAME.github.io`로 지정합니다. 여기서 `USERNAME`은 GitHub 사용자 이름을 나타냅니다.

  

#### 옵션 2. GitHub Fork

  

GitHub에 로그인하여 [**Chirpy Fork**](https://github.com/cotes2020/jekyll-theme-chirpy/fork)를 하고, 이를 `USERNAME.github.io`로 이름을 변경합니다 (`USERNAME`은 사용자 이름을 의미합니다).

  

그런 다음, 저장소를 로컬 머신으로 클론하고 [Node.js](https://nodejs.org/)가 설치되어 있는지 확인한 후, 저장소의 루트 디렉토리로 이동하여 다음 명령을 실행합니다:

  

```console

$ bash tools/init

```

  

> GitHub Pages에 사이트를 배포하지 않으려면 위 명령의 끝에 옵션 `--no-gh`를 추가하세요. {: .prompt-info }


  

위 명령은 다음을 수행합니다:

  

1. [최신 태그](https://github.com/cotes2020/jekyll-theme-chirpy/tags)로 코드를 체크아웃하여 사이트의 안정성을 보장합니다 (기본 브랜치의 코드는 개발 중입니다).
2.  필수적이지 않은 샘플 파일을 제거하고 GitHub 관련 파일을 처리합니다.
3. CSS/JS assets 파일을 빌드한 후 이를 Git에서 추적하게 만듭니다.
4. 위 변경 사항을 저장하는 새로운 커밋을 자동으로 생성합니다.

  

### 의존성 설치

  

로컬 서버를 처음 실행하기 전에 사이트의 Root 디렉토리로 이동하여 다음 명령을 실행하세요:

  

```console

$ bundle

```

  

## 사용법

  

### 구성

  


필요에 따라 `_config.yml`{: .filepath}의 변수를 수정하세요. 일반적인 옵션은 다음과 같습니다:

-   `url`
-   `avatar`
-   `timezone`
-   `lang`

  

### SNS 연락처 옵션

  

SNS 연락처 옵션은 사이드바 하단에 표시됩니다. `_data/contact.yml`{: .filepath } 파일에서 지정된 연락처를 켜거나 끌 수 있습니다.

  

### 스타일시트 커스텀

  

스타일시트를 커스텀해야 하는 경우 테마의 `assets/css/jekyll-theme-chirpy.scss`{: .filepath} 파일을 Jekyll 사이트의 동일한 경로에 복사한 후, 파일 끝에 사용자 정의 스타일을 추가하세요.

  

버전 `6.2.0`부터 `_sass/addon/variables.scss`{: .filepath}에 정의된 SASS 변수를 덮어쓰려면, 메인 sass 파일 `_sass/main.scss`{: .filepath}을 사이트 소스의 `_sass`{: .filepath} 디렉토리에 복사한 후, 새로운 파일 `_sass/variables-hook.scss`{: .filepath}을 생성하고 새 값을 할당하세요.

  

### 정적 Assets 커스

  

정적 자산 구성은 버전 `5.1.0`에 도입되었습니다. 정적 자산의 CDN은 `_data/origin/cors.yml`{: .filepath } 파일에 정의되어 있으며, 사이트가 게시되는 지역의 네트워크 조건에 따라 일부를 교체할 수 있습니다.

  

또한, 정적 Assets을 자체 호스팅하려면 [_chirpy-static-assets_](https://github.com/cotes2020/chirpy-static-assets#readme)를 참조하세요.

  

### 로컬 서버 실행

  

게시하기 전에 사이트 내용을 미리 보려면 다음 명령을 실행하세요:

  

```console

$ bundle exec jekyll s

```

  

잠시 후, 로컬 서비스는 _[http://127.0.0.1:4000](http://127.0.0.1:4000)_에서 게시될 것입니다.

  

## 배포

  

배포를 시작하기 전에 `_config.yml`{: .filepath} 파일을 확인하여 `url`이 올바르게 구성되었는지 확인하세요. 또한, [**프로젝트 사이트**](https://help.github.com/en/github/working-with-github-pages/about-github-pages#types-of-github-pages-sites)를 선호하고 사용자 지정 도메인을 사용하지 않거나, GitHub Pages 이외의 웹 서버에서 기본 URL을 사용하여 사이트에 접속하려는 경우 `baseurl`을 프로젝트 이름으로 변경하세요. 예: `/project-name`.

  

Now you can choose _ONE_ of the following methods to deploy your Jekyll site.

  

### GitHub Actions 배포

  

준비할 사항이 몇 가지 있습니다.

  

- GitHub 무료 플랜을 사용하는 경우, 사이트 저장소를 공개로 유지하세요.

- `Gemfile.lock`{: .filepath} 파일을 저장소에 커밋했으며 로컬 머신이 Linux가 아닌 경우, 사이트의 루트로 이동하여 lock 파일의 플랫폼 목록을 업데이트하세요:

  

```console

$ bundle lock --add-platform x86_64-linux

```

  

다음, _Pages_ 서비스를 구성하세요.

  

1. GitHub에서 저장소로 이동합니다. _Settings_ 탭을 선택한 후 왼쪽 네비게이션 바에서 _Pages_를 클릭합니다. 그런 다음, **Source** 섹션(빌드 및 배포 아래)에서 드롭다운 메뉴에서 [**GitHub Actions**](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow)를 선택합니다. 

2. 커밋을 GitHub에 푸시하여 _Actions_ 워크플로우를 트리거합니다. 저장소의 _Actions_ 탭에서 _Build and Deploy_ 워크플로우가 실행 중인 것을 볼 수 있습니다. 빌드가 완료되고 성공하면, 사이트는 자동으로 배포됩니다.

  

이 시점에서, GitHub에서 표시하는 URL로 이동하여 사이트에 접속할 수 있습니다.

  

### 수동 빌드 & 배포

  

자체 호스팅 서버에서는 **GitHub Actions**의 편리함을 누릴 수 없습니다. 따라서, 로컬 머신에서 사이트를 빌드한 후 사이트 파일을 서버에 업로드해야 합니다.

  

프로젝트의 소스 루트로 이동하여 다음과 같이 사이트를 빌드하세요:

  

```console

$ JEKYLL_ENV=production bundle exec jekyll b

```

  

출력 경로를 지정하지 않는 한, 생성된 사이트 파일은 프로젝트 루트 디렉토리의 `_site`{: .filepath} 폴더에 배치됩니다. 이제 해당 파일들을 대상 서버에 업로드해야 합니다.

  

[nodejs]: https://nodejs.org/

[starter]: https://github.com/cotes2020/chirpy-starter

[pages-workflow-src]: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow

[latest-tag]: https://github.com/cotes2020/jekyll-theme-chirpy/tags