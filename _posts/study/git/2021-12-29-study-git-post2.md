---
layout: post
title: Study-Git-post2
description: >
  [Git]에러(error: failed to push some refs to...)
sitemap: false
hide_last_modified: false
categories:
  - study
  - git
---

# [Git]에러(error: failed to push some refs to...)

---

상황

Github 주소 Repositary 에서 직접 [README.md](http://README.md) 파일을 수정한 상태로, 로컬에서 ‘git add’ , ‘git commit’, ‘git push’를 한 상태이다.

### 에러발생

Github 주소 Repositary에서 직접 README.md를 수정한것을 잊고, 로컬에서 작업을 진행하였다...

‘git add’, ‘git commit’과 ’git push’ 를 하는 순간.....

```bash
C:\폴더경로>git push -u origin master
To [깃허브 Repository주소]
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to '깃허브 Repository주소'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

에러가 발생하고 말았다...

그리고 hint만 보고 ‘git pull’을 해버렸다...

```bash
C:\폴더경로>git pull origin master    
From [깃허브 Repository 주소]
 * branch            master     -> FETCH_HEAD
Merge made by the 'recursive' strategy.
```

## 해결방법

순간 맨붕이 왔고 구글링을 하기 시작했다.

글을 읽으면서 내가 왜 이런 에러가 발생 했는지 천천히 생각하기 사작했다.

결국 GitHub주소에서 직접 파일을 수정하고 로컬에서 ‘git pull’을 안한게 생각이 났다!ㅠㅠ

그래서 깃 작업을 되돌릴 방법을 찾기 시작했고, ‘git resotre’ 과 ‘git  reset’을 발견하게 되었다.

일단 ‘git status’ 명령어를 통해 현재 파일들의 상태를 보았다.

<aside>
💡 git status : 현재 파일들의 상태를 보여주는 명령어

</aside>

```bash
C:\develp\nikitoe-github-blog\mygitblog>git status
On branch master
Your branch and 'origin/master' have diverged,
and have 5 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

nothing to commit, working tree clean
```

그리고 ‘git log’를 통해 commit의 히스토리를 확인하여 최종버전에 HEAD가 있는것을 확인했다.

<aside>
💡 git log : commit의 히스토리를 확일할 수 있는 명령어

</aside>

```bash
C:\폴더경로>git log
commit 'commit정보이름' (HEAD -> master)
Author: '유저 정보'
Date:   Wed Dec 29 23:01:16 2021 +0900

    Blog

commit 'commit정보이름'
Merge: a09b262 cff8e5c
Author: '유저 정보'
Date:   Wed Dec 29 22:55:52 2021 +0900

    Merge branch 'master' of https://github.com/nikitoe/nikitoe.github.io
```

cmd는 이스케이프 처리로 읽어 ^을 두번 입력하여 ‘git reset HEAD^^’ 명령어를 입력하여, commit이 취소되고 unstaged된 상태를 확인한다.

<aside>
💡 git reset HEAD^^ : 최신 커밋삭제하며 이전으로 되돌리는 명령어

</aside>

```bash
C:\폴더경로>git reset HEAD^^ 
Unstaged changes after reset:
D       README.md
M       _data/authors.yml
M       about.md
```

‘git log’ 명령어를 사용하여 이전 버전에 HEAD가 있는것을 확인하고, ‘git status’ 명령어로 파일이 수정된 상태이고 스테이지에 안올라간 상태임을 확인한다.

```bash
C:\폴더경로>git status
On branch master
Your branch and 'origin/master' have diverged,
and have 4 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    README.md
        modified:   _data/authors.yml
        modified:   about.md

no changes added to commit (use "git add" and/or "git commit -a")
```

마지막으로 ‘git resotre’ 명령어를 사용하여 수정한 파일들을 되돌리고, ‘git status’ 명어로 clean된 작업트리의 상태를 확인한다.

<aside>
💡 git restore <파일명> :  수정한 파일 되돌리는 명령어

</aside>

```bash
C:\폴더경로>git restore README.md

C:\폴더경로>git restore _data/authors.yml         

>git restore about.md

C:\폴더경로>git status
On branch master
Your branch and 'origin/master' have diverged,
and have 4 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

nothing to commit, working tree clean
```

문제점을 해결하고 ‘git pull’명령어를 통해 잘 작동하는것을 확인했다....

```bash
C:\폴더경로>git pull
Removing README.md
Merge made by the 'recursive' strategy.
 README.md | 5 -----
 1 file changed, 5 deletions(-)
 delete mode 100644 README.md
```

### 마무리

이번 git 에러를 통해 많은 것을 배웠다.

- 로컬 작업할 때에는 절대 GibHub Repository를 건들지 말기!!!!!!!
- ’git  add’, ‘git commit’,  ‘git push’ 등 git 명령어 사용할 때에는 꼭!! 먼저 점검하고 해도 되는것인지 생각하고 생각하기!!!!!!!
- 에러 발생 시 문제점이 무엇이고 자세히 찾아보지도 않고, 무작정 hint를 보거나 내 생각대로 판단해서 실행에 옮기지 않기!!!!!!