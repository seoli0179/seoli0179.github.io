---
title: Jekyll Git Action Build 에러
date: 2024-05-29 20:30:00 +0900
categories: [Blogging]
tags: [Debug,Git Action,Jekyll]
render_with_liquid: false
---

## Can't find stylesheet to import
Git Action에서 jekyll을 빌드했더니 아래와 같은 오류가 발생했다.

### 에러 Console 내용

```shell
Run bundle exec jekyll build --baseurl "" --trace
Configuration file: /home/runner/work/seoli0179.github.io/seoli0179.github.io/_config.yml
 Theme Config file: /home/runner/work/seoli0179.github.io/seoli0179.github.io/_config.yml
            Source: /home/runner/work/seoli0179.github.io/seoli0179.github.io
       Destination: /home/runner/work/seoli0179.github.io/seoli0179.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
Error: Can't find stylesheet to import.
  ╷
1 │ @import 'dist/bootstrap';
  │         ^^^^^^^^^^^^^^^^
  ╵
  main.bundle.scss 1:9                                                                               @import
  /home/runner/work/seoli0179.github.io/seoli0179.github.io/assets/css/jekyll-theme-chirpy.scss 1:9  root stylesheet 
  Conversion error: Jekyll::Converters::Scss encountered an error while converting 'assets/css/jekyll-theme-chirpy.scss':
                    Can't find stylesheet to import.
bundler: failed to load command: jekyll (/home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/bin/jekyll)
/home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-sass-converter-3.0.0/lib/jekyll/converters/scss.rb:175:in `rescue in convert': Can't find stylesheet to import. (Jekyll::Converters::Scss::SyntaxError)
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-sass-converter-3.0.0/lib/jekyll/converters/scss.rb:159:in `convert'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:105:in `block in convert'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `each'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `reduce'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `convert'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:84:in `render_document'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:63:in `run'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:572:in `render_regenerated'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:564:in `block in render_pages'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:563:in `each'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:563:in `render_pages'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:211:in `render'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:80:in `process'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:28:in `process_site'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/commands/build.rb:65:in `build'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/commands/build.rb:36:in `process'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:91:in `block in process_with_graceful_fail'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:91:in `each'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:91:in `process_with_graceful_fail'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/commands/build.rb:18:in `block (2 levels) in init_with_program'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `block in execute'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `each'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `execute'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary/program.rb:44:in `go'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary.rb:21:in `program'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/exe/jekyll:15:in `<top (required)>'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/bin/jekyll:25:in `load'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/bin/jekyll:25:in `<top (required)>'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli/exec.rb:58:in `load'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli/exec.rb:58:in `kernel_load'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli/exec.rb:23:in `run'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli.rb:486:in `exec'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/vendor/thor/lib/thor/command.rb:27:in `run'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/vendor/thor/lib/thor/invocation.rb:127:in `invoke_command'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/vendor/thor/lib/thor.rb:392:in `dispatch'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli.rb:31:in `dispatch'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/vendor/thor/lib/thor/base.rb:485:in `start'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli.rb:25:in `start'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/gems/3.1.0/gems/bundler-2.3.26/libexec/bundle:48:in `block in <top (required)>'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/friendly_errors.rb:120:in `with_friendly_errors'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/gems/3.1.0/gems/bundler-2.3.26/libexec/bundle:36:in `<top (required)>'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/bin/bundle:25:in `load'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/bin/bundle:25:in `<main>'
/home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/sass-embedded-1.77.2/lib/sass/compiler/host.rb:86:in `compile_request': Can't find stylesheet to import. (Sass::CompileError)
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/sass-embedded-1.77.2/lib/sass/compiler.rb:171:in `compile_string'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/sass-embedded-1.77.2/lib/sass/embedded.rb:37:in `compile_string'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-sass-converter-3.0.0/lib/jekyll/converters/scss.rb:160:in `convert'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:105:in `block in convert'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `each'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `reduce'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `convert'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:84:in `render_document'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:63:in `run'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:572:in `render_regenerated'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:564:in `block in render_pages'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:563:in `each'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:563:in `render_pages'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:211:in `render'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:80:in `process'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:28:in `process_site'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/commands/build.rb:65:in `build'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/commands/build.rb:36:in `process'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:91:in `block in process_with_graceful_fail'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:91:in `each'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:91:in `process_with_graceful_fail'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/commands/build.rb:18:in `block (2 levels) in init_with_program'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `block in execute'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `each'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `execute'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary/program.rb:44:in `go'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/mercenary-0.4.0/lib/mercenary.rb:21:in `program'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/exe/jekyll:15:in `<top (required)>'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/bin/jekyll:25:in `load'
	from /home/runner/work/seoli0179.github.io/seoli0179.github.io/vendor/bundle/ruby/3.1.0/bin/jekyll:25:in `<top (required)>'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli/exec.rb:58:in `load'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli/exec.rb:58:in `kernel_load'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli/exec.rb:23:in `run'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli.rb:486:in `exec'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/vendor/thor/lib/thor/command.rb:27:in `run'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/vendor/thor/lib/thor/invocation.rb:127:in `invoke_command'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/vendor/thor/lib/thor.rb:392:in `dispatch'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli.rb:31:in `dispatch'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/vendor/thor/lib/thor/base.rb:485:in `start'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/cli.rb:25:in `start'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/gems/3.1.0/gems/bundler-2.3.26/libexec/bundle:48:in `block in <top (required)>'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/3.1.0/bundler/friendly_errors.rb:120:in `with_friendly_errors'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/lib/ruby/gems/3.1.0/gems/bundler-2.3.26/libexec/bundle:36:in `<top (required)>'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/bin/bundle:25:in `load'
	from /opt/hostedtoolcache/Ruby/3.1.4/x64/bin/bundle:25:in `<main>'
Error: Process completed with exit code 1.
```



```
---
---

@import 'main
{%- if jekyll.environment == 'production' -%}
  .bundle
{%- endif -%}
';

/* append your custom style below */

```
{: file="assets\css\jekyll-theme-chirpy.scss"}



```
@import 'dist/bootstrap';
@import 'main';
```
{: file="_sass\main.bundle.scss"}



### 해결방법

1. [부트스트랩 Github](https://github.com/twbs/bootstrap/tree/main/dist/css)에서 dist/css 파일을 다운로드 
2. dist/bootstrap 이름 변경
3. _sass\에 폴더 이동
3. Git 푸쉬함


참고 사이트:
