---
layout: post
title: Project-BackEnd-bank_financial_instruments_fnUser
image: /assets/img/blog/project/background-project1.png
sitemap: false
hide_last_modified: false
categories:
  - project
  - backend
---

# [Project]은행금융상품_상세기능_사용자

---
* toc
{:toc .large-only}

---

## 1. 회원가입 페이지

<details>
  <summary>회원가입 처리</summary>
    <div markdown="1">

    - POST /api/member/signup
    - 요청 : 이메일 ,비밀번호, 이름, 휴대폰번호

</div>
</details>

## 2. 이메일 인증 페이지

<details details>
  <summary>이메일 인증 요청</summary>
    <div markdown="1">

    - GET /api/member/email
    - 요청 : 이메일

</div>
</details>
<details>
  <summary>이메일 인증 요청 처리</summary>
    <div markdown="1">

    - GET /api/member/email-auth
    - 요청 : uuid(범용 고유 식별자)

</div>
</details>

## 3. 로그인 페이지

<details>
  <summary>로그인 요청 처리</summary>
    <div markdown="1">

    - POST /api/member/login
    - 요청 : 이메일, 비밀번호

</div>
</details>
<details>
  <summary>로그아웃 처리</summary>
    <div markdown="1">

    - GET /api/member/logout

</div>
</details>

## 4. 비밀번호 페이지

<details>
  <summary>비밀번호 찾기 요청</summary>
    <div markdown="1">

    - POST/api/member/find/password
    - 요청 : 이메일 이름

</div>
</details>
<details>
  <summary>비밀번호 찾기 요청 처리</summary>
    <div markdown="1">

    - GET /api/member/reset/password
    - 요청 : uuid(범용 고유 식별자)

</div>
</details>
<details>
  <summary>새로운 비밀번호 설정</summary>
    <div markdown="1">

    - PATCH /api/member/reset/password
    - 요청 : uuid(범용 고유 식별자), 비밀번호

</div>
</details>

## 5. 회원정보 페이지

## 6. 계좌 페이지

## 7. 이체 페이지

## 8. 정기예금 페이지


