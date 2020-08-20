CLI (Command line interface)

명령줄 인터페이스

GUI(Graphic User Interface)

그래픽 유저 인터페이스



ls = 목록

touch CLI.txt 파일생성

mkdir git 폴더생성

git init - 저장소 생성(초기화) 최초의 한번만

----------------------------------------------------------------

어떠한 작업을 하고 나서



1) 커밋할 목록에 등록

git add . 

2) 커밋

git commit -m 'First commit'

3) 버전(이력)

git log

4) 상태

git status

# Git 기초

>  git은 분산형 버전관리시스템(DVCS)이다.

Git을 윈도우에서 활용하기 위해서는 [git bash](https://gitforwindows.org/)를 설치해야한다.

## 1. 저장소 초기화

```bash
$ git init
Initialized empty Git repository in C:/Users/HOME/Desktop/TIL/.git/
(master) $
```

* 로컬 저장소를 만들고 나면, `.git/` 폴더가 생성되고, bash에 `(master)` 라고 표기 된다.
* 반드시 저장소를 만들기 전에 원하는 디렉토리인지 확인하는 습관을 가지고, 저장소 내부에 저장소를 만들지는 말자.
  * 예) Desktop-> git 저장소, TIL-> 다른 git 저장소(x)

## 2. `add`

작업한 내용을 커밋 대상 목록에 추가한다.

```bash
# 작업 후 상태
$ git status
On branch master

No commits yet
# Untracked files => Git 으로 관리 된적 없는 파일
Untracked files:
# 커밋 될 것들에 포함시키기 위해서는 add 명령어를 써라
  (use "git add <file>..." to include in what will be committed)
        Markdown.md
# 총평
# 커밋될 곳에 없다(nothing)
# 하지만, 새로 생성한 파일(untracked files)은 존재한다.

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
$ git add .
```

```bash
# add 명령어 후 상태
$ git status
On branch master

No commits yet
# 커밋이 될 변경 사항들
# working directory X
# Staging area O
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   Markdown.md

```

## 3. `commit`

```bash
$ git commit -m 'Add markdown.md'
[master (root-commit) 1633ea7] Add markdown.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 Markdown.md
```

* 커밋은 버전(이력)을 기록하는 명령어이다.
* 커밋 메시지는 해당하는 이력을 나타낼 수 있도록 작성 하여야 한다.
* 커밋 이력을 확인하기 위해서는 아래의 명령어를 사용한다.

```bash
$ git log
commit 1633ea7fd202c1d4c2e0118e773a0268ccf3c09a (HEAD -> master)
Author: gockdrjqnr <gockd0105@naver.com>
Date:   Thu Aug 20 14:58:07 2020 +0900

    Add markdown.md
$ git log -1
$ git log --oneline
1633ea7 (HEAD -> master) Add markdown.md
$ git log --oneline -1
```





