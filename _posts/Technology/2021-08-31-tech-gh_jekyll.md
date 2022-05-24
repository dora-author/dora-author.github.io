---
layout: post
title: "[Tech] Jekyll을 사용한 나만의 Github Pages 만들기"
excerpt: Github Pages, Jekyll를 활용한 정적 사이트 개설에 관하여
tags:
  - Github Pages
  - Jekyll
category: Technology
date: 2021-08-31
comments: true
---

## Intro - 나의 블로그는 어떻게 만들어졌을까

현재 나의 블로그는 [GitHub][github]에서 제공하는 웹사이트 호스팅 서비스인 [GitHub Pages][github-pages]과 정적 사이트 생성기인 [Jekyll][jekyll]을 통하여 만들어졌다.
<br> **GitHub Pages**가 사이트를 개설하기 위한 도메인과 퍼블리셔 기능을 제공한다면, **Jekyll**은 이 블로그 전체 UI, 디자인 등을 포괄하는 사이트 생성 기능을 제공한다.
<Br> 책이 웹사이트라면 그 책을 작성하는 작가를 **Jekyll**, 그 책을 출판하는 출판사를 **GitHub Pages**로 비유하고 싶다.
<br> 단, 이를 가능하게 하는 사전 조건은 사용자 계정의 GitHub에 `<username>.github.io` 이름의 repository가 존재해야 하며, 이 repository에 사이트 생성에 필요한 'HTML', 'CSS', 'JavaScript', 'Markdown' 형태의 정적 파일들이 업로드(`git push`)되어야 한다. 

[github]: https://github.com/

[github-pages]: https://pages.github.com/

[jekyll]: https://jekyllrb.com/

---
<Br>

## GitHub Pages에 관하여

**GitHub Pages**는 GitHub의 repository에 있는 HTML, CSS 및 JavaScript 등의 정적 사이트 파일들을 빌드 프로세스를 통해 실행하고, 해당 사이트를 게시하는 static site 호스팅 서비스이다.

<br>

### 호스팅

사용자는 GitHub에서 제공하는 `github.io` 도메인에 웹사이트를 호스팅하거나 혹은 사용자 자체 커스텀 도메인에서 사이트를 호스팅할 수 있다. 이에 대한 자세한 방법은 GitHub Docs에서 제공하는 [Using a custom domain with GitHub Pages](https://docs.github.com/en/articles/using-a-custom-domain-with-github-pages)을 참고한다.

<br>

### 빌드 및 게시

**GitHub Pages**는 사용자 GitHub repository의 사이트 파일들을 정적 사이트로 자동 게시한다. 
<br> 사용자는 자체적으로 사이트용 static 파일들을 생성하거나 내부적인 빌드 프로세스를 활용해도 된다. 혹은 사용자 사이트를 빌드하는 `static site generator`를 사용할 수 있다.
<br> **GitHub Pages**는 사이트를 생성하고 빌드하기 위하여 기본적으로 **Jekyll**을 사용한다.

<br>

## Jekyll에 관하여

[Jekyll](https://jekyllrb.com/)은 **GitHub Pages**에 대한 빌트인 기능이 있는 `static site generator`이다.

**Jekyll**은 Markdown, HTML, CSS 형태의 파일들을 가지고 사용자가 선택한 레이아웃 기반의 정적 웹사이트를 생성하기까지 매우 간단한 빌드 프로세스를 지원한다.

<Br>

### Jekyll Theme

사이트에서 보여지는 스타일이나 디자인은 정적 파일 중 CSS, JS, HTML 파일이 결정하는데, **Jekyll Theme**를 적용하여 사용자 사이트의 Look & Feel을 커스터마이징할 수 있다. 
[Jekyll Theme](https://jekyllrb.com/docs/themes/)는 
Jekyll 커뮤니티에서 유지 관리하는 템플릿과 스타일로 사용할 Plugin을 정의하며, 사용자 콘텐츠로 재정의될 수 있도록 assets, layouts, includes, 그리고 stylesheets 구성의 패키지로 구성된다.
**Jekyll Theme**를 적용하는 방법은 두 가지이다.

-  **GitHub에서 지원해주는 [Supported Themes](https://pages.github.com/themes/) 적용하기**
  <br> -> ["Adding a theme to your GitHub Pages site with the theme chooser."](https://docs.github.com/en/pages/getting-started-with-github-pages/adding-a-theme-to-your-github-pages-site-with-the-theme-chooser) 참고

- **GitHub에 올라온 오픈소스 형태의 Jekyll theme를 수동으로 적용하기**
<br> -> ["Adding a theme to your GitHub Pages site using Jekyll."](https://docs.github.com/en/articles/adding-a-theme-to-your-github-pages-site-using-jekyll) 참고
<br> 현재 나의 GitHub Page site도 이 방법으로 진행하였으며 보다 다양한 스타일의 [theme](https://jekyllrb.com/docs/themes/#pick-up-a-theme)를 선택하고, 디자인이나 레이아웃 등을 사용자 취향에 맞게 커스터마이징할 수 있다.
다만 `_config.yml`, `*.css`, `*.html`과 같은 theme와 관련한 파일들을 사용자 로컬 환경에서 수정하고 **Jekyll**을 통하여 사이트를 빌드해야하므로 GitHub의 Supported Themes 기능을 사용하는 방법보다 복잡할 수 있다.

<br>

## 실습 Tutorial - 설치부터 사이트 게시까지 <br> (feat. [GitHub Doc's Setting up your GitHub Pages site locally with Jekyll](https://docs.github.com/en/enterprise/2.13/user/articles/setting-up-your-github-pages-site-locally-with-jekyll))

Github Pages, Jekyll를 활용하여 직접 사이트를 개설해보는 과정은 위에 설명한 [Jekyll theme를 수동으로 적용하는 과정](#Jekyll Theme)을 step-by-step으로 풀이한 내용이라고 볼 수 있다. 
<br> 요약하자면 Jekyll theme를 적용하기에 앞서 Jekyll 실행을 위한 필요 환경을 설치 후 사용자의 Git repository에 Jekyll theme 설정 파일들을 생성하고 커스터마이징을 위한 파일 수정, 해당 사이트에 대한 파일 생성, 사이트 빌드 및 게시이다.


### 사전 조건(Prequisite)
{:toc}

사용자 [GitHub 계정](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)에 `username.github.io`이름의 원격 repository가 존재해야 한다.([참고](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites
))
<br> 없다면 GitHub에서 해당 이름의 repository를 만든 후 로컬에서 `git clone <remote origin 주소>` 하거나 로컬 특정 폴더에서 `git init` -> `git checkout -b <브랜치명>` -> `git remote add origin <remote origin 주소>` 로 진행한다.
<br> 이 repository 및 특정 브랜치에 사용자 사이트를 빌드하기 위한 필요 파일들이 저장되어야 하며 해당 repository 접근 설정은 `public`으로 해야 한다. 
사이트에 대한 소스 파일이 민감한 내용을 포함한다면 `private`설정도 가능하나 유료이다. 자세한 내용은 [GitHub's products의 가격 정책](
https://github.com/pricing#compare-features)을 참고한다.

<br>

### 1. 필요 환경 설치

GitHub Pages는 PHP, Ruby, Python과 같은 사용자 서버 쪽 언어을 지원하지 않으므로, Jekyll을 설치하고 실행하기 위해 사용자 로컬 PC 환경에 Ruby와 Bundler가 설치되어 있어야 한다. 

  > ℹ️ <span style="color:#247CFF"> **_NOTE_** </span>
  > <br> Jekyll은 `Ruby`라는 언어로 만들어진 `Ruby` [Gem]( https://jekyllrb.com/docs/ruby-101/#gems)이며, `Bundler`는 Ruby Gems 간의 의존성, 빌드 에러 등을 관리하는 프로그램이다.

  > ⚠️ <span style="color:#FFE423"> **_Warning_** </span>
  > <Br> Bundler를 설치하려면, Ruby가 설치되어 있어야 한다.

<br>

  **Step1.** Ruby 2.1.0 or higher [설치](https://rubyinstaller.org/downloads/)

  **Step2.** [Bundler](https://bundler.io/) 설치
    <br> CMD window 혹은 `Git Bash`에서 아래와 같이 실행

  ``` Bash 
    
    $ gem install bundler
 
  ```
<Br>

### 2. Gemfile을 통한 Jekyll 및 Plugin 설치

Jekyll 사이트 빌드에 필요한 [Gems](https://jekyllrb.com/docs/ruby-101/#gems)을 설치해야 한다.
Gems 정보는 [Gemfile](https://jekyllrb.com/docs/ruby-101/#gemfile)에 Jekyll 및 Plugin 리스트로 정의되어 있으며 `Gemfile`은 Jekyll 사이트 파일들이 저장되는 `username.github.io` repository 폴더 루트에 존재한다.

  **Step1.** Jekyll 사이트 파일들이 저장된 로컬 repository 폴더에 `Gemfil`이 없으면 아래와 같은 내용의 `Gemfile`을 새로 만들어 루트 경로에 저장한다. 
  <br> Jekyll theme에 대한 Git 소스를 `clone`하거나 다운로드해서 `Gemfile`이 존재하다면 `Gemfile` 내 아래 내용이 있는지 확인하고 없으면 추가한다.

  ```ruby
        source 'https://rubygems.org'
        gem 'github-pages', group: :jekyll_plugins
  ```  
    
  > ℹ️ <span style="color:#247CFF"> **_NOTE_** </span>
  > <br> 필자는 사용하고자 하는 [Jekyll theme](http://jekyllthemes.org/themes/moon/)를 다운로드 후 로컬 Git repository 폴더에 복사했기 때문에 이미 Gemfile이 존재해있었다. 따라서 `Gemfile` 내 해당 내용을 추가하는 방식으로 진행했다.

  <br>

  **Step 2.** `Gemfil`에 정의된 `jekyll` Gem 및 `jekyll-feed` 등과 같은 plugin Gem을 아래 명령어를 실행하여 설치한다.

  ```bash
          $ bundle install
  ``` 

설치 후, `Gemfile.lock`이 동일 경로에 생성된다.

  > ℹ️ <span style="color:#247CFF"> **_NOTE_** </span>
  > <br> `jekyll-feed`, `jekyll-seo-tag` and `jekyll-archives`과 같은 Jekyll [plugins](https://jekyllrb.com/docs/plugins/)도 Gem이다. 
  <br> 사용자는 이러한 Jekyll plugins을 사용하여 사이트에 대한 Jekyll 기능을 확장할 수 있다. 
  --> [plugin 사용 방법](https://jekyllrb.com/docs/plugins/installation/)
  <br> GitHub Pages에서 기본적으로 사용하도록 되어있는 [plugins](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll#plugins) 및 지원 가능한 [plugins 리스트](https://pages.github.com/versions/)를 참고한다.

<br>

### 3. 사이트 콘텐츠 커스터마이징

사용자 로컬 Git repository 폴더에 `Gemfile`을 포함하여 Jekyll site 구축을 위한 모든 파일들이 존재한다면 이제 Jekyll site를 빌드하여 게시하면 된다. 하지만 해당 파일들이 최초 Jekyll theme를 복사해온 상태 그대로라면 사이트에 보여질 내용은 사용자 정보를 담고 있지 않을 것이다. 따라서 사이트명, 이메일, SNS 주소를 포함하여 사이트 구조 및 내용은 직접 관련 파일을 수정하거나 추가하는 방식으로 커스터마이징해야 한다.
<br> 커스터마이징할 파일을 포함한 Jekyll site를 구성하는 전체 폴더의 기본 구조는 다음과 같다.

![참고](/img/tech/0831_gh_jekyll_01.png)

[출처: [Jekyll Docs > Site Structure](https://jekyllrb.com/docs/structure)]


<br> 이 중 일부 파일을 수정하여 사이트 콘텐츠을 커스터마이징하는 방법은 다음과 같다.

- 사용자 정보(사이트명, 이메일, 로고, SNS 등) --> `_config.yml` 수정 ([Jekyll Docs 참고](https://jekyllrb.com/docs/configuration/))
  <br> 다운로드한 site theme에 존재하는 `_config.yml` 내용을 보면 본인 개인 정보와 다른 부분이 보이기 때문에 어느 부분을 수정할지 인지할 수 있을 것이다. 예를 들어 사이트 로고에 대한 이미지 파일 수정 방법은 [Jekyll Docs](https://jekyllrb.com/docs/static-files/#add-front-matter-to-static-files)를 참조한다.

- 사이트 구조 및 레이아웃, 콘텐츠
  - 템플릿 구조 -> `_layouts` 폴더 내용 수정 ([Jekyll Docs 참고](https://jekyllrb.com/docs/layouts/))

  - 콘텐츠
    <Br> 사용자가 사이트에 업데이트하는 콘텐츠 유형은 레이아웃에 따라 크게 `page`와 `post`가 있으며 모두 `Markdown` 및 `HTML`형태로 작성한다. 또한 콘텐츠 가장 첫부분에 `YAML`형식의 [Front Matter](https://jekyllrb.com/docs/front-matter/) 블락을 추가하여 현재 작성하는 내용에 대한 `layout`, `title`, `date`와 같은 meta data 정보를 명시한다.   
    - `page` 추가하기 -> 루트 경로에 `.md` 파일 추가
      <br> 자세한 수정 방법은 [GitHub Docs > Adding a new page to your site](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-content-to-your-github-pages-site-using-jekyll#adding-a-new-page-to-your-site) 및 [Jekyll Docs > Pages](https://jekyllrb.com/docs/pages/)를 참고한다.
    - `post` 추가 및 변경하기 ->  `_posts` 폴더 수정 
      <br> 자세한 수정 방법은 [GitHub Docs > Adding a new post to your site](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-content-to-your-github-pages-site-using-jekyll#adding-a-new-post-to-your-site) 및 [Jekyll Docs > Posts](https://jekyllrb.com/docs/posts/)를 참고한다.

<Br>

### 4. Jekyll Site 파일 생성하기

이 단계는 사용자 로컬 환경에서 Jekyll site를 빌드하여 테스트해야하는데 사용자 로컬 PC에 GitHub Page에 게시할 Jekyll site 파일들이 존재하지 않는 경우 진행한다. 즉  site 파일들이 저장될 로컬 폴더가 빈 상태여야 한다.

  > ℹ️ <span style="color:#247CFF"> **_NOTE_** </span>
  > <Br> 사용자가 특정 [Jekyll Theme](https://jekyllrb.com/docs/themes/)를 다운로드하거나 GitHub repository에 게시된 해당 소스를 `clone`한 상태라면 이미 사용자 로컬 폴더에는 관련 사이트 파일들이 존재해있으므로 이 단계를 생략하고 바로 [5. Jekyll Site 빌드 및 테스트하기](#5-jekyll-site-----------)로 넘어간다.

  <br>

  **Step 1.** CMD window 혹은 `Git Bash`에서 해당 로컬 폴더 경로로 이동 후 아래 명령어를 실행한다.
  <br>
  ``` Bash
    
    $ bundle exec jekyll _{jekyll버전명}_ new {local repo명}
  
  ```

  Ex) `$ bundle exec jekyll _3.3.0_ new NEW-JEKYLL-SITE-REPOSITORY-NAME`
      
  위 명령어 대신 `Gemfile`내 정의된 `gem "jekyll", "~> {버전명}"`를 주석 처리 후 `bundle exec jekyll new .`를 실행하거나 `bundle exec jekyll new {my-project}`를 실행한다.

  > ⚠️ <span style="color:#FFE423"> **_Warning_** </span>
  > <br> 이미 파일들이 존재하는 상황에서 위 명령어를 수행하면 다음과 같은 에러가 발생한다.
  > <br> `Conflict: ~ exists and is not empty.`

  <br>

  Site 파일들을 생성하였으면 GitHub Pages를 통하여 site를 게시할 수 있도록 다음 단계를 진행한다.

  **Step 2.** `Gemfile`에 정의된 gem 리스트 중 `jekyll` gem 대신 `github-pages` gem을 사용하도록 아래와 같이 `Gemfile`을 수정한다.
  
  ``` ruby
    # gem "jekyll", "~> 3.9.0" #diable jekyll

    gem "github-pages", group: :jekyll_plugins #using github-pages
  ```

이후 모든 변경 사항을 연결된 Git 원격 repository에 업로드하도록 `git add .` -> `git commit -m "commit message"` -> `git push origin {gh-pages branch}` 순서로 진행한다.
<br> 해당 로컬 폴더가 Git 소스를 `clone`한 상태가 아니거나, Git repository로 초기화되지 않은 상태라면 위의 [사전 조건(Prequisite)](#------prequisite-)을 참고하여 사용자 로컬 상의 Git 환경부터 설정한다.

  
<br>

### 5. Jekyll Site 빌드 및 테스트하기

사용자가 사이트 파일 내용을 위 [3. 사이트 콘텐츠 커스터마이징](#3---------------)처럼 변경했다면 GitHub Pages를 통하여 게시되는 웹사이트 상에서 보기 전에 사용자 로컬 환경에서 확인할 수 있다.

  > ℹ️ <span style="color:#247CFF"> **_NOTE_** </span>
  > <Br> GitHub Pages 사용자가 변경한 콘텐츠를 원격 repository에 `push`하면 Jekyll을 사용해서 사이트를 빌드 후 자동 게시하므로 테스트할 필요가 없다면 해당 단계도 생략할 수 있다.

<br>

해당 과정은 GitHub Pages로 호스팅하는 것이 아닌 Jekyll을 사용하여 사용자 로컬의 서버 환경에서 테스트하는 것이기 때문에 `Gemfile`내 명시된 `github-pages` gem 정보는 주석으로 되어있고, `jekyll` gem 정보는 주석이 해제되어 있는지 확인한다. 

  **Step 1.** CMD window 혹은 `Git Bash`에서 해당 로컬 폴더 경로로 이동 후 아래 명령어를 실행한다. 
  <Br>
   ``` Bash
    
    $ bundle exec jekyll serve

  ```

  > ℹ️ <span style="color:#247CFF"> **_NOTE_** </span>
  > <Br> `jekyll serve` 명령어는 Jekyll site 빌드 후 내부 서버에 게시한다는 의미이다. 
    <br> (이외 다른 Jekyll 명령어는 [Jekyll Docs](https://jekyllrb.com/docs/usage/) 참고)
  
  <br>
  
  이후 명령 실행창에 `Server address: http://127.0.0.1:4000`가 표시된다.

  **Step 2.** 사용자 브라우저에서 `http://127.0.0.1:4000` 주소에 접속 후 해당 사이트가 잘 게시되는지 확인한다.

  > ℹ️ <span style="color:#247CFF"> **_NOTE_** </span>
  > <Br> 사용자 site가 내부 로컬 서버에 게시되는 동안  site 파일을 수정하는 경우,  `ctrl`+ `C` 키를 눌러 종료하지 않는 이상, 자동으로 site에 반영된다.


