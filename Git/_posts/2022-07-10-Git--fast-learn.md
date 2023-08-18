---
title: "Git : fast learn"
excerpt: "이거 하나 못해서 그렇게 해매고 있을꺼야?! 할일이 산더미인데?!"
categories:
  - Git
---

<br>

<br>

## Git 초기 설정

### 커밋 작성자(author) 설정

```bash
$ git config --global user.email "메일주소"
$ git config --global user.name "유저네임"
```

> github 주소를 적어줘야 합니다.

- 지정된 설정 확인 방법

```bash
$ git config --global -l
```

<br>

<br>

------

### 커밋 편집기 변경

```bash
$ git config --global core.editor "code --wait"
```

- 해당 명령어는 반드시 vscode가 설치되어 있어야 합니다.

> 기본 텍스트 편집기 `vim`을 `vscode`로 대체하는 것

<br>

<br>

------

### 원격 저장소 (remote repository)

1. 로컬 git 저장소 준비
2. Github repository 생성
3. Repository default branch 변경 (settings -> repositories)
   - main -> master로 변경

![3](https://github.com/sehun98/TIL/assets/100746863/82c24294-9022-4da5-b82c-43843e243038)

### gitignore

> git으로 관리하고 싶지 않은 파일들의 리스트를 작성하여, 
> 특정 파일들을 git이 버전 관리를 하지 않도록 하는 것

- 일반적으로 개인정보 및 특정 사람에게만 적용되는 환경들(개인 개발환경 관련)이 이 파일에 작성 됨
- 개발환경 관련 파일들(.idea 등)은 버전관리가 될 필요도 없을 뿐더러, 개인정보 같은건 애초에 GitHub에 올라가서는 안됨
- `.gitignore` 파일을 만들어서 관리 (위치는 `.git` 파일과 동일한 곳)
- https://gitignore.io/
  - 본인 개발 환경에 대한 내용을 넣고 생성하면, 일반적으로 개발자들이 많이 쓰는 gitignore 문서를 제공

> 일반적으로 `git init` 후 첫 `add` 전 작성할 것

<br>

<br>

------

### README.md

> 디렉토리나 압축 파일에 포함된 기타 파일에 대한 정보를 작성합니다.

<br>

<br>

---



## ❄️빠르게 익히자 !!!


### 폴더 만들기

``` bash
$mkdir 폴더명
```

<br>

### 폴더 이동

``` bash
$cd 폴더명
$cd ..
```

<br>

### 파일 만들기

``` bash
$touch README.md
$touch .gitignore
```

<br>

### 파일 열기

``` bash
$explorer README.md/
$code text.txt
```

<br>

### git init

``` bash
$git init
```

<br>

### git status

``` bash
$git status
```

> [주의 사항]
>
> 백번을 사용해도 모자라다. 항상 git 상태를 체크 할 것!!

<br>

### git add .

``` bash
$git add .
$git add 폴더명
```

<br>

### git status

``` bash
$git status
```

>  [주의 사항]
>
>  백번을 사용해도 모자라다. 항상 git 상태를 체크 할 것!!

<br>

### git commit -m " "

``` bash
$git commit -m "커밋 메세지"
```

<br>

### 깃허브 연결

``` bash
$git remote add origin 저장소URL
```

<br>

### git push -u origin master

``` bash
$git push -u origin master
$git push
```

> 한번 push 했을 경우 두번째 명령어를 사용해도 됩니다.

### git pull origin master

``` bash
$git pull origin master
```

<br>

### 폴더 삭제

``` bash
$rm 폴더명
```

<br>

<br>
