---
title: 게시물 작성
author: cotes
date: 2019-08-08 14:10:00 +0800
categories: [Blogging, Tutorial]
tags: [writing]
render_with_liquid: false
---

이 튜토리얼에서는 _Chirpy_ 템플릿에 게시물을 작성하는 방법을 안내하며, 많은 기능이 특정 변수를 설정해야 하므로 Jekyll을 사용한 적이 있어도 읽을 가치가 있습니다.

## 이름과 경로

`YYYY-MM-DD-TITLE.EXTENSION`{: .filepath}라는 이름의 새 파일을 생성하여 `_posts` 폴더에 저장합니다. EXTENSION는 md와 markdown 중 하나여야 합니다. 파일 생성 시간을 절약하려면 `ekyll-Compose`플러그인 사용을 고려하십시오.

## Front Matter

기본적으로, 게시물 상단에 아래와 같이 [Front Matter](https://jekyllrb.com/docs/front-matter/) 를 작성해야 합니다:

```yaml
---
title: TITLE
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [TAG]     # TAG names should always be lowercase
---
```

> post 레이아웃은 기본적으로 `post`로 설정되어있으므로, Front Matter 블록에 _layout_을 추가할 필요는 없습니다. 
{: .prompt-tip }

### 타임존

게시물의 `작성일`을 정확히 기록하기 위해서는 `_config.yml`의 시간대를 설정할 뿐만 아니라 게시물의 시간을 Front Matter 블록의 그리나치 평균시(GMT)로 제공해야 합니다. 형식: `+/-TTTT,` 예: `+0900`.

### Categories and Tags

각 게시물의 `카테고리`는 최대 2개의 요소를 포함하도록 설계되었으며, `태그`의 요소 개수는 0 ~ 무한대까지 가능합니다. 예로 들어 다음과 같습니다:

```yaml
---
categories: [Animal, Insect]
tags: [bee]
---
```

### 작성자 정보

게시물의 작성자 정보는 일반적으로 _Front Matter_에 입력할 필요가 없으며, 기본적으로 구성 파일의 변수 `social.name` 과 `social.links`의 첫 번째 항목에서 얻을 수 있습니다. 그러나 다음과 같이 재정의 할 수도 있습니다:

`_data/authors.yml`에 작성자 정보 추가 (만약 사이트에 이 파일이 없는 경우 생성하세요).

```yaml
<author_id>:
  name: <full name>
  twitter: <twitter_of_author>
  url: <homepage_of_author>
```
{: file="_data/authors.yml" }

그런 다음 `author`를 사용하여 한 명만 지정하거나 `authors`를 사용하여 여러 명을 지정합니다:

```yaml
---
author: <author_id>                     # for single entry
# or
authors: [<author1_id>, <author2_id>]   # for multiple entries
---
```

그러나 `author`도 여러 명을 지정할 수 있습니다.

> `_data/authors.yml`{: .filepath } 파일에서 작성자 정보를 읽을 수 있는 장점은 페이지에 메타 태그 `twitter:creator`가 있어서, [Twitter Cards](https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started#card-and-content-attribution)를 풍부하게 하고 SEO에 적합하다는 것 입니다.
{: .prompt-info }

### 게시물 설명

기본적으로 게시물의 첫 단어는 게시물 목록에 대한 홈페이지, _Further Reading_ 섹션 및 RSS 피드의 XML에 표시하는 데 사용됩니다. 게시물에 대한 자동 생성 설명을 표시하지 않으려면 _Front Matter_ 의 'description' 필드를 사용하여 사용자 지정할 수 있습니다:

```yaml
---
description: Short summary of the post.
---
```

또한 게시물 페이지의 게시물 제목 아래에 'description' 텍스트도 표시됩니다.

## 목차 (Table of Contents)

기본적으로 목차(TOC, **T**able **o**f **C**ontents)는 게시물 오른쪽 패널에 표시됩니다. 전역적으로 해제하려면 `_config.yml`{: .filepath}에 변수 `toc` 값을 `false`로 설정합니다. 특정 게시물에 대한 TOC를 히제하려면 게시물의 [Front Matter](https://jekyllrb.com/docs/front-matter/)에 다음을 추가합니다:

```yaml
---
toc: false
---
```

## 댓글

댓글의 글로벌 전환은 `_config.yml`{: .filepath} 파일의 `comments.active` 변수로 정의됩니다. 이 변수에 대한 댓글 시스템을 선택한 후 모든 게시물에 대해 댓글이 켜집니다.

특정 게시물에 대한 댓글을 닫으려면 게시물의 **Front Matter**에 다음을 추가합니다:

```yaml
---
comments: false
---
```

## 미디어

이미지, 오디오, 비디오를 _Chirpy_의 미디어 리소스라고 합니다.

### URL 접두사

때때로 게시물의 여러 리소스에 대한 중복 URL 접두사를 정의해야 하는데, 이는 두 개의 매개 변수를 설정하면 피할 수 있는 지루한 작업입니다.

- CDN을 사용하여 미디어 파일을 호스팅하는 경우, `_config.yml`{: .filepath }에서 cdn을 지정할 수 있습니다. 사이트 아바타 및 게시물의 미디어 리소스 URL은 CDN 도메인 이름 앞에 붙습니다.

  ```yaml
  cdn: https://cdn.com
  ```
  {: file='_config.yml' .nolineno }

- 현재 게시물/페이지 범위에 대한 리소스 경로 접두사를 지정하려면, 게시물의 _front matter_ 에 `media_subpath`를 설정합니다:

  ```yaml
  ---
  media_subpath: /path/to/media/
  ---
  ```
  {: .nolineno }

옵션 `site.cdn`와 `page.media_subpath`를 개별적 또는 조합하여 사용하여 최종 리소스 URL인 `[site.cdn/][page.media_subpath/]file.ext`를 유연하게 구성할 수 있습니다.

### 이미지

#### 설명

이미지의 다음 줄에 이탤릭체를 추가하면, 설명이 이미지 맨 아래에 나타납니다:

```markdown
![img-description](/path/to/image)
_Image Caption_
```
{: .nolineno}

#### 크기

이미지를 로드할 때 페이지 콘텐츠 레이아웃이 이동하는 것을 방지하기 위해 각 이미지의 너비와 높이를 설정해야 합니다.

```markdown
![Desktop View](/assets/img/sample/mockup.png){: width="700" height="400" }
```
{: .nolineno}

> SVG의 경우 적어도 _width_를 지정해야 합니다. 그렇지 않으면 렌더링되지 않습니다.
{: .prompt-info }

_Chirpy v5.0.0_ 버전부터는, `height` and `width` 축약어를 지원합니다. (`height` → `h`, `width` → `w`). 다음 예제는 위의 예와 동일한 효과를 같습니다:

```markdown
![Desktop View](/assets/img/sample/mockup.png){: w="700" h="400" }
```
{: .nolineno}

#### 위치

기본적으로 이미지는 중앙에 배치되지만, `normal`, `left`, `right` 중 하나를 사용하여 위치를 지정할 수 있습니다.

> 위치를 지정하면 이미지 설명이 추가되지 않습니다.
{: .prompt-warning }

- **기본 위치**

  이미지는 아래 샘플에 정렬된 상태로 유지됩니다:

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .normal }
  ```
  {: .nolineno}

- **왼쪽 정렬**

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .left }
  ```
  {: .nolineno}

- **오른쪽 정렬**

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .right }
  ```
  {: .nolineno}

#### 다크/라이트 모드

다크/라이트 모드에서 이미지가 테마 기본 설정을 따르도록 할 수 있습니다. 이를 위해서는 다크 모드와 라이트 모드의 두 개의 이미지를 준비한 다음 특정 클래스(`dark` 또는 `light`)를 지정해야 합니다:

```markdown
![Light mode only](/path/to/light-mode.png){: .light }
![Dark mode only](/path/to/dark-mode.png){: .dark }
```

#### 그림자

프로그램 창의 스크린샷은 그림자 효과를 보여주는 것으로 간주할 수 있습니다:

```markdown
![Desktop View](/assets/img/sample/mockup.png){: .shadow }
```
{: .nolineno}

#### 미리보기 이미지

게시물 상단에 이미지를 추가하시려면, `1200 x 630`의 해상도를 가진 이미지를 제공해주시기 바랍니다. 이미지 가로 세로 비율이 `1.91 : 1`을 만족하지 않으면 이미지의 스케일과 크롭이 진행됩니다.

이러한 전제 조건을 알고 이미지의 속성 설정을 시작할 수 있습니다:

```yaml
---
image:
  path: /path/to/image
  alt: image alternative text
---
```

미리보기 이미지에 ['media_subpath'](#url-prefix)를 전달할 수도 있습니다. 즉, 미리보기 이미지가 설정된 경우 `path` 속성은 이미지 파일 이름만 있으면 됩니다.

간단한 사용을 위해 `image`를 사용하여 경로를 정의할 수도 있습니다.

```yml
---
image: /path/to/image
---
```

#### LQIP

미리보기 이미지의 경우:

```yaml
---
image:
  lqip: /path/to/lqip-file # or base64 URI
---
```

> You can observe LQIP in the preview image of post \"[Text and Typography](../text-and-typography/)\".
> 게시물 \"[Text and Typography](.../Text and Typography/)\"의 미리보기 이미지에서 LQIP를 관찰할 수 있습니다.

일반 이미지:

```markdown
![Image description](/path/to/image){: lqip="/path/to/lqip-file" }
```
{: .nolineno }

### 비디오

#### 소셜 미디어 플랫폼

다음 구문을 사용하여 소셜 미디어 플랫폼의 비디오를 내장할 수 있습니다:

```liquid
{% include embed/{Platform}.html id='{ID}' %}
```

여기서 `Platform`은 플랫폼 이름의 소문자이고, `ID`는 비디오 ID입니다.

다음 표는 주어진 비디오 URL에서 필요한 두 개의 파라미터를 얻는 방법을 보여주며, 현재 지원되는 비디오 플랫폼도 알 수 있습니다.

| Video URL                                                                                          | Platform   | ID             |
| -------------------------------------------------------------------------------------------------- | ---------- | :------------- |
| [https://www.**youtube**.com/watch?v=**H-B46URT4mg**](https://www.youtube.com/watch?v=H-B46URT4mg) | `youtube`  | `H-B46URT4mg`  |
| [https://www.**twitch**.tv/videos/**1634779211**](https://www.twitch.tv/videos/1634779211)         | `twitch`   | `1634779211`   |
| [https://www.**bilibili**.com/video/**BV1Q44y1B7Wf**](https://www.bilibili.com/video/BV1Q44y1B7Wf) | `bilibili` | `BV1Q44y1B7Wf` |

#### 비디오 파일

비디오 파일을 직접 내장하려면 다음 구문을 사용합니다:

```liquid
{% include embed/video.html src='{URL}' %}
```

여기서 `URL`은 동영상 파일의 URL입니다 e.g. `/path/to/sample/video.mp4`.

내장된 비디오 파일에 대한 추가 속성을 지정할 수도 있습니다. 여기에 허용되는 전체 속성 목록이 있습니다.

- `poster='/path/to/poster.png'` — 비디오가 다운로드되는 동안 표시되는 비디오의 포스터 이미지
- `title='Text'` — title for a video that appears below the video and looks same as for images
- `autoplay=true` — 비디오 아래에 표시되고 이미지와 동일하게 보이는 비디오의 제목
- `loop=true` — 비디오 끝에 도달하면 자동으로 처음으로 되돌아갑니다
- `muted=true` — 오디오가 초기에 비활성화됩니다
- `types` — 추가 비디오 형식의 확장자를 '|'로 구분하여 지정합니다. 이러한 파일이 기본 비디오 파일과 동일한 디렉토리에 있는지 확인합니다.

위의 모든 것을 활용한 예를 생각해 보십시오:

```liquid
{%
  include embed/video.html
  src='/path/to/video.mp4'
  types='ogg|mov'
  poster='poster.png'
  title='Demo video'
  autoplay=true
  loop=true
  muted=true
%}
```

### 오디오

오디오 파일을 직접 내장하려면 다음 구문을 사용합니다:

```liquid
{% include embed/audio.html src='{URL}' %}
```

여기서 `URL`은 오디오 파일의 URL입니다 e.g. `/path/to/audio.mp3`.

내장된 오디오 파일에 대한 추가 속성을 지정할 수도 있습니다. 여기에 허용되는 전체 속성 목록이 있습니다.

- `title='Text'` — 오디오 아래에 표시되고 이미지와 동일하게 보이는 오디오의 제목
- `types` — 추가 오디오 형식의 확장자를 '|'로 구분하여 지정합니다. 이 파일들이 기본 오디오 파일과 동일한 디렉토리에 존재하는지 확인합니다.

위의 모든 것을 활용한 예를 생각해 보십시오:

```liquid
{%
  include embed/audio.html
  src='/path/to/audio.mp3'
  types='ogg|wav|aac'
  title='Demo audio'
%}
```

## 고정 게시물

하나 이상의 게시물을 홈 페이지 상단에 고정할 수 있으며, 고정된 게시물은 출시일에 따라 역순으로 정렬됩니다. 활성화 기준:

```yaml
---
pin: true
---
```

## Prompts

프롬프트 타입 종류: `tip`, `info`, `warning`, and `danger`. 이러한 프롬프트는 `prompt-{type}`클래스를 블록 인용문에 추가하여 생성할 수 있습니다. 예를 들어 `info` 유형의 프롬프트를 다음과 같이 정의합니다:

```md
> Example line for prompt.
{: .prompt-info }
```
{: .nolineno }

## 구문

### 인라인 코드

```md
`inline code part`
```
{: .nolineno }

### 파일주소 하이라이트

```md
`/path/to/a/file.extend`{: .filepath}
```
{: .nolineno }

### 코드블럭

Markdown 심볼 ```` ``` ````은 코드 블록을 다음과 같이 쉽게 만들 수 있습니다:

````md
```
This is a plaintext code snippet.
```
````

#### 언어 지정

```` ```{language} ```` 구문 강조 표시가 있는 코드 블록을 사용할 수 있습니다:

````markdown
```yaml
key: value
```
````

> The Jekyll 태그 `{% highlight %}` 는 이 테마와 호환되지 않습니다.
{: .prompt-danger }

#### 줄 번호

기본적으로 `plaintext`, `console`, `terminal`를 제외한 모든 언어는 줄 번호를 표시합니다. 코드 블록의 줄 번호를 숨기려면 다음과 같은 클래스 `nolineno를` 추가합니다:

````markdown
```shell
echo 'No more line numbers!'
```
{: .nolineno }
````

#### 파일 이름 지정

코드 블록의 맨 위에 코드 언어가 표시되는 것을 알아차렸을 수도 있습니다. 파일 이름으로 대체하려면 `file` 속성을 추가하여 다음을 수행할 수 있습니다:

````markdown
```shell
# content
```
{: file="path/to/file" }
````

#### Liquid Codes

**Liquid** 스니펫을 표시하려면 Liquid 코드를 `{%raw %}` 및 `{% endraw %}`로 둘러싸십시오:

````markdown
{% raw %}
```liquid
{% if product.title contains 'Pack' %}
  This product's title contains the word Pack.
{% endif %}
```
{% endraw %}
````

또는 게시물의 YAML 블록에 `render_with_liquid: false`(Jekyll 4.0 이상 필요)를 추가합니다.

```

## 수학

우리는 수학을 생성하기 위해 [**MathJax**][mathjax]를 사용합니다. 웹사이트 성능상의 이유로, 수학적 기능은 기본적으로 로드되지 않습니다. 그러나 다음을 통해 활성화할 수 있습니다:

[mathjax]: https://www.mathjax.org/

```yaml
---
math: true
---
```

수학적 기능을 활성화한 후 다음 구문을 사용하여 수학 방정식을 추가할 수 있습니다:

- **수학 블록**에는  빈 줄이 포함된 `$$`가 앞뒤로 추가되어야 합니다. `$$ math $$`
  - **방정식 번호 지정**을(를) 삽입하려면 `$$\begin{equation} math \end{equation}$$`를 추가해야 합니다
  - **등식 번호 지정** 참조는 등식 블록의 `\label{eq:label_name}`과 텍스트에 맞춰 `\eqref{eq:label_name}`으로 수행해야 합니다(아래 예시 참조)
- **inline math**(행 안에) `$$` 앞 또는 뒤에 공백 줄 없이 `$$ math $$`를 추가해야 합니다
- **inline math**(목록)에 `\$$ math $$`를 추가해야 합니다

```markdown
<!-- Block math, keep all blank lines -->

$$
LaTeX_math_expression
$$

<!-- Equation numbering, keep all blank lines  -->

$$
\begin{equation}
  LaTeX_math_expression
  \label{eq:label_name}
\end{equation}
$$

Can be referenced as \eqref{eq:label_name}.

<!-- Inline math in lines, NO blank lines -->

"Lorem ipsum dolor sit amet, $$ LaTeX_math_expression $$ consectetur adipiscing elit."

<!-- Inline math in lists, escape the first `$` -->

1. \$$ LaTeX_math_expression $$
2. \$$ LaTeX_math_expression $$
3. \$$ LaTeX_math_expression $$
```

'v7.0.0'부터 **MathJax**의 구성 옵션이 `asset/js/data/mathjax.js`{: .filepath} 파일로 이동되었으며, 필요에 따라 [extensions][mathjax-exts]를 추가하는 등의 옵션을 변경할 수 있습니다.  
> `chirpy-starter`를 통해 사이트를 구축하는 경우 gem 설치 디렉토리(명령어 `bundle info --path jekyll-theme-chirpy`로 확인)에서 해당 파일을 리포지토리의 동일한 디렉토리로 복사합니다.
{: .prompt-tip }

[mathjax-exts]: https://docs.mathjax.org/en/latest/input/tex/extensions/index.html

## Mermaid

[**Mermaid**](https://github.com/mermaid-js/mermaid) 는 훌륭한 다이어그램 생성 도구입니다. 게시물에서 활성화하려면 YAML 블록에 다음을 추가하십시오:

```yaml
---
mermaid: true
---
```

그런 다음 다른 마크다운 언어처럼 사용할 수 있습니다: 그래프 코드 ```` ```mermaid ```` 와 ```` ``` ````를 감싸세요.

## Learn More

Jekyll 게시물에 대한 자세한 내용은, [Jekyll Docs: Posts](https://jekyllrb.com/docs/posts/)를 방문하세요.
