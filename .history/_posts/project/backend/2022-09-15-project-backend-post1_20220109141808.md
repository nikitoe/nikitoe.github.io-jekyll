---
layout: post
title: Study-Git-post1
image: /assets/img/blog/study/background-git2.png
sitemap: false
hide_last_modified: false
categories:
  - study
  - git
---

# [Git]에러(error: remote origin already exists)

---

## 상황

블로그 제작을 위해 작업한 폴더를 **SSH Git Repository** 주소로 원격저장소와 연결을 시켰다.

```bash
C:\폴더경로>git remote add origin 'SSH Git **repository** 주소'
```

## 에러발생

하지만 나는 **HTTPS Git Rrepository** 주소로 연결하고 싶었기때문에 ‘git push’ 시 에러가 발생하였다.

```bash
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
```

그래서 다시 ‘git remote add origin’을 지도했지만 해당 에러가 방생하였다.

```bash
error: remote origin already exists.
```

해당 에러를 찾아보니 깃의 Remote origin already exists 에러는 기존에 연결되어 있는 레파지토리가 다시 새로운 레파지토리에 소스코드를 올리려고 하면 발생되는 에러였다.

그래서 원격저장소에 연결되어있는 기존의 연걸을 끊고 새로 올리려서 문제를 해결해 보았다.

## 해결방법

```bash
C:\폴더경로>git remote remove origin
```

1. git remote remove origin 명령어를 통해 기존에 열결되어 있는 원격저장소와 연결을 끊는다.

```bash
C:\폴더경로>git remote add origin 'HTTPS Git **repository** 주소'
```

1. git remote add origin [새롭게 연결할 HTTPS Repository 주소] 명령어를 입력한다.

```bash
C:\폴더경로>git push -u origin master  
Enumerating objects: 112, done.
```

1. git push -u origin master 명령어를 입력하면 소스코드가 잘 올라간것을 확인할 수 있다.

## 마무리

이번 git error를 통해 다음과 같은 것을 배웠다.

- 원격 저장소와 연결하기전에 (HTTPS, SSH)을 확인한다.