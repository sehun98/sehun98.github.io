---
title: "Git : cooperation"
excerpt: "협력의 시작 branch"
categories:
  - Git
---

<br>

<br>

## 협력 !!! (기본)

<br>

### git clone

``` bash
$git clone 저장소URL
```

<br>

### git branch

``` bash
$git switch -c 브랜치명   # create
$git branch 브랜치명
```

`switch`

- switch is created for the **single purpose of changing branches**, and when you do that, **you do want to be at the HEAD of that branch**.

<br>

### 브랜치 확인

``` bash
$git branch
$git log --all --oneline --graph
```

![4](https://github.com/sehun98/TIL/assets/100746863/3d3e6b7b-d8fd-4a10-b5e1-9273ae844bc6)

<br>

### 브랜치 이동

``` bash
$git switch 브랜치명
```

<br>

### git merge 브랜치명

``` bash
$git merge 브랜치명
```

> [주의 사항] 
>
> 반드시 `master` 브랜치에 `브랜치` 를 병합

<br>

### 브랜치 삭제

``` bash
$git branch -d 브랜치명
$git branch -D 브랜치명 # 강제 삭제(merge 되지 않은 객체 삭제하는 방법)
```

> [주의 사항]
>
> `merge`후에는 항상 사용하지 않는 브랜치를 삭제해줘야 합니다 !!!

<br>

## git push -u origin 브랜치명

```bash
$git push -u origin 브랜치명
```

<br>

## 3가지 Merge 상황

### 1. fast-forward

> "다른 브랜치가 생성된 이후 master 브랜치에 변경 사항이 없는 상황"
>
> 즉, master 브랜치에서 login 브랜치를 Merge 할 때 
> login 브랜치가 master 브랜치 이후의 커밋을 가리키고 있으면 
> 그저 master 브랜치가 login 브랜치와 동일한 커밋을 가리키도록 이동시킬 뿐

![5](https://github.com/sehun98/TIL/assets/100746863/4cd7eacf-2db0-4b35-804b-438c0f71634c)

1. login branch 생성 및 이동

   ```bash
   $ git switch -c login 
   ```

2. 특정 작업 완료 후 commit

   ```bash
   $ touch login.txt
   $ git add .
   $ git commit -m "login test 1"
   ```

3. master 브랜치로 이동

   ```bash
   $ git checkout master
   
   $ git log --oneline --all -graph
   
   * 7a79de3 (login) login test 1
   * 5910361 (HEAD -> master) master test 1
   ```

4. master 에 병합

   ```bash
   $ git merge login
   
   Updating 5910361..7a79de3
   Fast-forward
    login.txt | 0
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 login.txt
   ```

5. 결과 확인 (fast-foward, 단순히 HEAD를 이동)

   ```bash
   $ git log --oneline --all -graph
   
   7a79de3 (HEAD -> master, login) login test 1
   5910361 master test 1
   ```

6. branch 삭제

   ```bash
   $ git branch -d login
   
   $ git log --oneline --all -graph
   
   7a79de3 (HEAD -> master) login test 1
   5910361 master test 1
   ```

<br>

### 2. 3-way Merge (Merge commit)

> 현재 브랜치(master)가 가리키는 커밋이 Merge 할 브랜치의 조상이 아니면, 
> git 은 각 브랜치가 가리키는 커밋 2 개와 공통조상 하나를 사용하며 3-way Merge 한다.
>
> 단순히 브랜치 포인터를 최신 커밋으로 옮기는 게 아니라 3-way Merge 의 결과를 
> 별도의 커밋으로 만들고 나서 해당 브랜치가 그 커밋을 가리키도록 이동시킵니다. 
> 그래서 이런 커밋은 부모가 여러 개고 Merge commit 이라고 부릅니다.

![6](https://github.com/sehun98/TIL/assets/100746863/1966f0b2-865a-4790-82fe-5d5abc8203d8)

1. signout 브랜치 생성 및 이동

   ```bash
   $ git checkout -b signout
   ```

2. 특정 작업 완료 후 commit

   ```bash
   $ touch signout.txt
   
   $ git add .
   $ git commit -m "signout test 1"
   
   $ git log --oneline
   37c8937 (HEAD -> signout) signout test 1
   7a79de3 (master) login test 1
   5910361 master test 1
   ```

3. master 브랜치로 이동

   ```bash
   $ git checkout master
   ```

4. master 에 추가 작업 후 commit (단 **signout 브랜치와 다른 파일**을 생성 혹은 수정)

   ```bash
   $ touch master.txt
   
   $ git add .
   $ git commit -m "master test 2"
   
   $ git log --all --oneline
   5ae736d (HEAD -> master) master test 2
   37c8937 (signout) signout test 1
   7a79de3 login test 1
   5910361 master test 1
   ```

5. master 에 병합

   ```bash
   $ git merge signout
   ```

6. 자동 merge commit 발생

   - 커밋 편집기 화면 등장

   - 자동으로 작성된 커밋 메세지를 확인하고 저장 및 종료

     ```bash
     $ git merge signout
     Merge made by the 'recursive' strategy.
      signout.txt | 0
      1 file changed, 0 insertions(+), 0 deletions(-)
      create mode 100644 signout.txt
     ```

7. log 확인

   ```bash
   $ git log --all --graph --oneline
   *   3ae8333 (HEAD -> master) Merge branch 'signout'
   |\
   | * 37c8937 (signout) signout test 1
   * | 5ae736d master test 2
   |/
   * 7a79de3 login test 1
   * 5910361 master test 1
   ```

8. branch 삭제

   ```bash
   $ git branch -d signout
   ```

<br>

### 3. Merge Conflict

> Merge 하는 두 브랜치에서 **같은 파일의 한 부분을 동시에 수정**하고 Merge 하면 
> Git은 해당 부분을 자동으로 Merge 하지 못한다. 
> (반면 동일 파일이더라도 서로 다른 부분을 수정했다면, Conflict 없이 자동으로 Merge Commit 된다.)

![7](https://github.com/sehun98/TIL/assets/100746863/48b6f116-9626-49ca-918e-eae57219fadb)

1. hotfix 브랜치 생성 및 이동

   ```bash
   $ git checkout -b hotfix
   ```

2. 특정 작업 완료 후 commit

   ```bash
   # test.txt 수정
   
   master test 1
   이건 hotfix 에서 작성한
   문장이에요!!
   ```

   ```bash
   $ git add .
   $ git commit -m "hotfix test 1"
   
   $ git log --graph --oneline
   * 1a12012 (HEAD -> hotfix) hotfix test 1
   *   3ae8333 (master) Merge branch 'signout'
   |\
   | * 37c8937 signout test 1
   * | 5ae736d master test 2
   |/
   * 7a79de3 login test 1
   * 5910361 master test 1
   ```

3. master 브랜치로 이동

   ```bash
   $ git checkout master
   ```

4. 특정 작업(hotfix 와 동일 파일의 동일 부분 수정) 완료 후 commit

   ```bash
   # text.txt 수정
   
   master test 1
   이건 master 에서 작성한
   코드에용ㅎㅎ!!
   ```

   ```bash
   $ git add .
   $ git commit -m "master test 3"
   
   $ git log --graph --oneline --all
   * ac05762 (HEAD -> master) master test 3
   | * 1a12012 (hotfix) hotfix test 1
   |/
   *   3ae8333 Merge branch 'signout'
   |\
   | * 37c8937 signout test 1
   * | 5ae736d master test 2
   |/
   * 7a79de3 login test 1
   * 5910361 master test 1
   ```

5. master 에 병합

   ```bash
   $ git merge hotfix
   ```

6. 결과 → `merge conflict` 발생

7. 충돌 확인 및 해결

   - Merge 충돌이 일어났을 때 Git이 어떤 파일을 Merge 할 수 없었는지 살펴보려면 git status 명령을 이용한다.

   ```bash
   $ git status
   On branch master
   You have unmerged paths.
     (fix conflicts and run "git commit")
     (use "git merge --abort" to abort the merge)
   
   Unmerged paths:
     (use "git add <file>..." to mark resolution)
   
           both modified:   test.txt
   
   no changes added to commit (use "git add" and/or "git commit -a")
   ```

   ```
   master test 1
   <<<<<<< HEAD
   이건 master 에서 작성한
   코드에용ㅎㅎ!!
   =======
   이건 hotfix 에서 작성한
   문장이에요!!
   >>>>>>> hotfix
   ```

   - `=======` 위쪽의 내용은 HEAD 버전(merge 명령을 실행할 때 작업하던 master 브랜치)의 내용이고 아래쪽은 `hotfix` 브랜치의 내용이다. 충돌을 해결하려면 위쪽이나 아래쪽 내용 중에서 고르거나 새로 작성하여 Merge 한다. (`<<<<<<<, =======, >>>>>>>` 가 포함된 행을 삭제)

   ```bash
   # test.txt 최종본
   
   master test 1
   충돌을
   해결해보자!!
   ```

8. merge commit 진행

   ```bash
   $ git add .
   $ git commit
   ```

   - 이전에 진행했던 커밋 편집기 재등장

     ```bash
     Merge branch 'hotfix'
     
     # Conflicts:
     #       test.txt
     #
     # It looks like you may be committing a merge.
     # If this is not correct, please remove the file
     #       .git/MERGE_HEAD
     # and try again.
     
     # Please enter the commit message for your changes. Lines starting
     # with '#' will be ignored, and an empty message aborts the commit.
     #
     # On branch master
     # All conflicts fixed but you are still merging.
     #
     # Changes to be committed:
     #       modified:   test.txt
     #
     ```

     - 자동으로 작성된 커밋 메세지를 확인하고 저장 및 종료

       ```bash
       $ git commit
       [master 2aa2b1e] Merge branch 'hotfix'
       ```

9. log 확인

   ```bash
   $ git log --all --graph --oneline
   *   2aa2b1e (HEAD -> master) Merge branch 'hotfix'
   |\
   | * 1a12012 (hotfix) hotfix test 1
   * | ac05762 master test 3
   |/
   *   3ae8333 Merge branch 'signout'
   |\
   | * 37c8937 signout test 1
   * | 5ae736d master test 2
   |/
   * 7a79de3 login test 1
   * 5910361 master test 1
   ```

10. 브랜치 삭제

    ```bash
    $ git branch -d hotfix
    ```



# push error

#### 원격 저장소 수정으로 충돌

![8](https://github.com/sehun98/TIL/assets/100746863/267838a8-a664-474e-bb00-dfe0a1c6f5b9)

- 첫 커밋

![9](https://github.com/sehun98/TIL/assets/100746863/1870ec37-3590-410b-bf4e-8da62fdc220c)

- 원격 저장소에서 수정 후 커밋

  ![10](https://github.com/sehun98/TIL/assets/100746863/f457b8df-ebae-4293-af75-372e367eff73)

![11](https://github.com/sehun98/TIL/assets/100746863/ffe52144-ee26-4406-83fb-e390fc644b65)

> [!!!! 오류 오류 오류 !!!!]

![12](https://github.com/sehun98/TIL/assets/100746863/0ddda71f-153c-4b4f-aa33-ab8ef4ccc744)

```bash
$ git push origin master

To https://github.com/sehunOoh/sehunOoh.git
 ! [rejected]        master -> master (fetch first)
 # 에러!!!
error: failed to push some refs to 'https://github.com/sehunOoh/gitTestRepository.git'
# Updates이 거절되었다. 
# 원격저장소 작업이 로컬에 가지고 있지 않아...
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
# 너는 원격저장소 변경사항들을 먼저(first) 통합하는것을 원할거야....
# 다시 push 하기 전에....
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

```

- 확인 해보기

> 원격저장소 커밋과 로컬 저장소 커밋 히스토리를 서로 비교
>
> 서로 다른 히스토리를 가지고 있다!!

![13](https://github.com/sehun98/TIL/assets/100746863/e3e3f677-e712-43b5-aec6-d7f0be1bb022)

![14](https://github.com/sehun98/TIL/assets/100746863/cd46d866-fd4e-4443-b5b3-d18f331b0f69)



##### 해결 방법

![15](https://github.com/sehun98/TIL/assets/100746863/9239aabc-1652-4a5b-ab1d-dad83954db1e)
![16](https://github.com/sehun98/TIL/assets/100746863/f79161d4-6901-4f36-893a-3551217fdb31)

> 수정 후 재 push

```bash
$ git pull origin master
# 아마 커밋이 발생할 것.

$ git log --oneline
# Merge 커밋 => 원격이랑, 로컬 다른 버전을 두개 합쳤다!
b7b72e1 (HEAD -> master) Merge branch 'master' of https://github.com/sehunOoh/gitTestRepository 
3946b62 Update 경력
e884994 (origin/master) Update README.md
dcf3558 Add README
```

```bash
$ git push origin master

Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 725 bytes | 725.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/sehunOoh/gitTestRepository.git
   e884994..b7b72e1  master -> master

```

<br>

<br>

------

#### git the requested URL returend error : 403

##### 해결방법

```bash
$ git remote set-url origin 깃헙주소
```

<br>

# undoing 되돌리기

## add

> 원상태로 되돌리기

![17](https://github.com/sehun98/TIL/assets/100746863/78d2156a-438c-4893-afca-7562de6822df)



사전 준비

```bash
$ mkdir undoing
$ cd undoing
$ touch a.txt README.md
```

<br>

#### 1. add 취소

Staging Area와 Worink Directory 사이를 넘나드는 방법

<br>

##### 첫번째 커밋이 존재하지 않는 경우

> ```bash
> $ git rm --cached <file>
> ```
>
> - 따로 따로 커밋하려고 했지만, 실수로 `git add .` 이라고 실행해 버린 상황
> - 처음으로 add 된 상황

```bash
$ git init
$ git add .
```

```bash
$ git status

On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
        new file:   a.txt
```

```bash
# a.txt를 unstage

$ git rm --cached a.txt
```

```bash
$ git status

On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        a.txt
```

<br>

두번째 실습 전 사전 준비

```bash
$ git add .
$ git commit -m "first commit"
```

<br>

##### 두번째 커밋이 존재하는 경우

> ```bash
> $ git restore --staged <file>
> ```
>
> 두 개의 파일을 모두 수정하고서 따로따로 커밋하려고 했지만, 
> 실수로 `git add .` 라고 실행해 버린 상황

```bash
$ git add .
```

```bash
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
        modified:   a.txt
```

```bash
# a.txt를 unstage

$ git restore --staged a.txt
```

```bash
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt
```

<br>

##### 첫번째와 두번째 상황에서 명령어가 다른 이유

> 1. `git rm --cached <file>`
>    - 기존에 커밋이 없는 경우
>    - to unstage and remove paths only from the staging area
> 2. `git restore --staged <file>`
>    - 기존에 커밋이 존재하는 경우
>    - the contents are restored from `HEAD`

<br>

------

<br>

#### 2. add 전 수정본 원본으로 되돌리기

스테이지 올리기 전 수정본이 마음에 안들어서 되돌리기

> ```bash
> $ git restore <file>
> ```
>
> (add가 되어있지 않은, working derictory에 있는)
>
> 수정된 a.txt를 다시 되돌리기
>
> [주의 사항] 
>
> - 원래 파일로 덮어썼기 때문에 수정한 내용은 전부 사라짐
> - 수정한 내용이 진짜 마음에 들지 않을 때만 사용
> - 즉, 해당 명령어를 실행한 이후 절대로 다시 복원 불가능

```bash
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt
```

```bash
$ git restore a.txt
```

```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
```

<br>

------

<br>

## commit

#### 완료한 커밋 되돌리기

> ```bash
> $ git commit --amend
> ```
>
> 1. 커밋 메시지를 잘못 적었을 때
> 2. 너무 일찍 커밋했거나 (어떤 파일을 빼먹었을 때)
>
> [주의 사항]
>
> - 공개된 저장소에 push 된 커밋 메세지는 절대 수정하지 말기
> - 커밋 해시값이 변경되기 때문

<br>

#### 1. 커밋 메세지 수정

> 마지막으로 커밋하고 나서 수정한 것이 없다면 
> (커밋하자마자 바로 이 명령을 실행하는 경우)
>
> 이때는 커밋 메시지만 수정함

```bash
$ git add .

$ git commit -m "test"
[master b0a352d] test
 1 file changed, 1 insertion(+)
 create mode 100644 asd.txt
```

```bash
$ git commit --amend

hint: Waiting for your editor to close the file..[master c01f908] Add no.txt
 Date: Fri Jun 4 17:21:43 2021 +0900
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 asd.txt
```

- 설정에 따라 visual studio code나 vim 등 커밋 메시지 작성 화면이 나옴
- 여기에서 커밋 메세지를 수정하고 저장하면 반영 됨

<br>

#### 2. 어떤 파일을 빼먹었을 때

> 다시 커밋하고 싶으면 파일 수정 작업을 하고 Staging Area에 추가한 다음 
>
> `--amend` 옵션을 사용하여 커밋을 재작성

```bash
$ touch foo.txt bar.txt
$ git add foo.txt
```

```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   foo.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        bar.txt


$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        omit.txt

nothing added to commit but untracked files present (use "git add" to track)

```

```bash
# 실수로 bar.txt를 빼고 커밋 함

$ git commit -m "foo & bar"

[master 4221af6] foo & bar
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 foo.txt
```

```bash
$ git status

On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        bar.txt
```

<br>

**해결하기**

```bash
$ git add bar.txt

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   bar.txt

$ git commit --amend
hint: Waiting for your editor to close the file..[master ce77c2d] omit & real
 Date: Fri Jun 4 17:29:22 2021 +0900
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 omit.txt
 create mode 100644 real.txt
```

```bash
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   bar.txt
```

```bash
# 커밋 편집기 활성화 됨
$ git commit --amend

foo & bar

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Mon Jun 10 18:27:08 2021 +0900
#
# On branch master
# Changes to be committed:
#       new file:   bar.txt
#       new file:   foo.txt
```

- 저장 후 종료

  ```bash
  $ git commit --amend
  
  [master 7f6c24c] foo & bar
   Date: Mon Jun 10 18:27:08 2021 +0900
   2 files changed, 0 insertions(+), 0 deletions(-)
   create mode 100644 bar.txt
   create mode 100644 foo.txt
  ```

  - `create mode 100644 bar.txt` 가 추가된 것을 확인
  - commit은 새로 추가되지 않았음

<br>

# git push/pull이 안될때

> 주의사항
>
> 어지간하면 쓰지 말고 해결해라.

```
$ git push/pull origin --allow-unrelated-histories
```

<br>

<br>
