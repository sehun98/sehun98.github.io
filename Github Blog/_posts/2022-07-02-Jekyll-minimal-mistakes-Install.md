---
title: "Github Blog : Jekyll minimal mistakes Install"
excerpt: "개발자 블로그를 시작하게 된 이유와 시행착오에 대한 느낀점을 정리합니다."
categories:
  - Github Blog
---

<br>

<br>

# 개발자 블로그를 시작하게 된 이유?

저만의 학습 방법은 직접 부딛히는 방법입니다. 

- 손으로 회로도를 직접 그려보고 계산해보는 것이 효과적입니다. 

- 손으로 코드를 작성해보고 구상해보는 것이 효과적입니다.

하지만, 이러한 종이 노트는 시간이 오래 걸려 효율이 떨어지고 시간이 지나면 다시 펴보지 않는 한눈에 알아보기 힘든 가독성이 떨어집니다.

<br>

따라서, `노션` `티스토리` `git TIL` `samsung note` `Typora` `워드프레스` 등 많은 기록을 진행해보았습니다.

---

## `노션`

블록 · 페이지 단위로 드롭다운 방식은 간편하고 빠른 기록이 가능했지만, 간혹 업로드한 이미지와 동영상 기록이 사라져있는 마법을 볼 수 있었습니다. 

![1](https://github.com/sehun98/TIL/assets/100746863/f2871046-03ec-49cd-9e40-8ed5f3f0293d)


<br>

## `티스토리`

전형적인 블로그 형태로 대중적으로 기록하고 관리한다는 장점이 있던 것 같습니다. 스무 개 정도의 블로그밖에 기록하지 않았지만, 대중에게 보여지는 글을 작성하면서 신경을 써야 한다는 점이 있던 것 같습니다. 물론 맞춤법에 대한 문제는 간편하게 해결해 준 장점이 있습니다.

<br>

## `Git TIL` 

프로그래밍 공부할 때 협업 도구로 처음으로 접한 Git을 이용한 TIL (Today I Learned)은 잔디밭을 채운다는 뿌듯함이 있는 것 같습니다.  하지만, TIL을 진행하면 한눈에 볼 수 있는 것은 잔디밭 밖에 없다는 것을 느끼게 될 것입니다. 언제 어떤 생각으로 학습했는지 기억 나지 않는 것이 다반사였습니다.

<br>

## `Samsung note`

모바일을 통해 바로바로 기억이 나는 것, 구상을 손으로 그려보며 기록을 하는 것에 있어 종이 노트와 같은 효과를 낳았습니다. 그렇지만 이 또한 정리되지 않은 기록 방식이었습니다.

<br>

## `Typora`

markdown 방식의 Typora는 블로그 방식이 아니라 내가 무엇을 했는지 알려주기 힘든 단점이 있는 방식이지만 다양한 애플리케이션에서 사용이 가능하다는 이점이 있습니다.

<br>

## `워드프레스`

테마를 통한 노션보다 커스터마이징의 자율성이 높지만 내가 원하는 수준의 커스터마이징이 불가능하며 플러그인을 사용할때 충돌에 의한 불안정성이 존재했습니다. 또한 도메인을 지속해서 유지해야 하는 비용의 문제와 플러그인에 의한 웹 속도에 대한 신경을 더 쓰고 있다는 것을 깨닫게 해주었습니다. 

<br>

<br>

---

# `Github Blog`

1. 블로그 형태의 대중성
2. 한눈에 볼 수 있는 가독성
3. 기록함에 있어 오래 걸리지 않는 효율성
4. 동기부여를 하는 잔디밭의 역할
5. 코드로 커스터마이징을 하는 자율성

<br>

위의 모든 장점을 채택할 수 있는 Github Blog를 채택하였습니다.

<br>

<br>

---

본론으로 들어가 Jekyll minimal mistakes라는 테마의 Github Blog를 사용하는 법을 기록을 하며 익숙해지도록 하겠습니다.

<br>

제일 먼저 Ruby를 설치해야 합니다.

## 1. `Ruby 설치`

<a href="https://rubyinstaller.org/downloads/"> Ruby 다운로드 홈페이지</a> 에서 (x86)으로 다운로드를 진행합니다.

![2](https://github.com/sehun98/TIL/assets/100746863/4a83b18b-6119-4e4b-b06d-475d17b73bed)

Ruby를 실행하여 Jekyll 설치 후 정상적으로 설치되었는지 확인합니다.

![3](https://github.com/sehun98/TIL/assets/100746863/75d02806-afba-4206-9318-5a2a1c144e9a)

```ruby
$ gem install jekyll

$ ruby -v
$ jekyll -v
```

<br>

## 2. `minimal-mistakes 테마 설치`

<a href="https://github.com/mmistakes/minimal-mistakes">minimal-mistakes 테마 Github</a> 에서 clone or Zip을 받습니다.

![4](https://github.com/sehun98/TIL/assets/100746863/a8bef01d-6266-408b-9cc1-a39d654abd4a)

붉은색 파일은 삭제하고 초록색 파일은 예제 파일입니다.

![5](https://github.com/sehun98/TIL/assets/100746863/85d2b07a-cd16-4e5b-9ca5-054d938907ab)

정리한 파일로 github repository를 만들어 줍니다.

![6](https://github.com/sehun98/TIL/assets/100746863/c951541b-7eba-4f19-aff9-4eda03593753)

{: .align-center}

![7](https://github.com/sehun98/TIL/assets/100746863/8e6a391f-52c0-4392-9939-8e0584e03233)

<br>

## 3. `서버 실행`

Ruby를 실행하여 github폴더 경로에 들어갑니다.

![8](https://github.com/sehun98/TIL/assets/100746863/5b3ec1e0-cbea-49a7-992e-dae593cda537)



```ruby
$ cd /d D:
$ cd D:\github

$ gem install bundler
$ bundle exec jekyll serve --trace
```

서버를 실행하면 여러 오류가 생길 것입니다. 내가 발견한 오류는 다음과 같습니다.

## ❌ ERROR 1

`Bundler could not find compatible versions for gem "bundler"`

해결방안

```
$ gem install bundler
$ bundle update
```

## ❌ ERROR 2

`Jekyll 4.2.0 Please append '--trace' to the 'servo' command for any additional information or backtrace.`

해결방안

```
$ bundle exec jekyll serve --trace
```

## ❌ ERROR 3

`'require' : cannot load such file -- webrick (LoadError)`

해결방안

```
$ bundle add webrick
```

 ## ❌ ERROR 4

`Could not find gem 'webrick x64-minw32' in any of the gem source listed in your Gemfile.`

해결방안

```
$ gem intall webrick
$ jekyll build
```

<br>

# 4. `확인하기`

Ruby에서 아래와 같이 뜬다면 서버가 실행 중이므로 <a href="http://127.0.0.1:4000">http://127.0.0.1:4000 </a> 에 접속합니다.

![9](https://github.com/sehun98/TIL/assets/100746863/e4d0a3fc-f608-4105-ac51-4585f1d7d947)

첫번째 Github Blog가 만들어진 것을 볼 수 있습니다.

![10](https://github.com/sehun98/TIL/assets/100746863/387ffef0-777a-4219-8e81-15b2f49fbe85)

<br>

<br>