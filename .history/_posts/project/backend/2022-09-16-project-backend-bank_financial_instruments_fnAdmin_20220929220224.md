---
layout: post
title: Project-BackEnd-bank_financial_instruments_fnAdmin
image: /assets/img/blog/project/background-project1.png
sitemap: false
hide_last_modified: false
categories:
  - project
  - backend
---

# [Project]은행금융상품_상세기능_관리자

---
* toc
{:toc .large-only}

## 1. 회원 관리 페이지

<details>
  <summary>전체 회원 정보 조회</summary>
    <div markdown="1">

    - GET /admin/member/list.do
    - 요청 : 이메일

</div>
</details>
<details>
  <summary>해당 회원정보 상세 조회</summary>
    <div markdown="1">

    - - GET /api/admin/member/detail.do
    - 요청 : 이메일, 회원 이메일

</div>
</details>
<details>
  <summary>해당 회원 상태 정보 수정</summary>
    <div markdown="1">

    - PATCH /api/admin/member/status.do
    - 요청 : 이메일, 회원 이메일, 회원상태

</div>
</details>
<details>
  <summary>해당 회원 비밀번호 초기화</summary>
    <div markdown="1">

    - POST /api/admin/member/password.do
    - 요청 : 이메일, 회원 이메일, 비밀번호

</div>
</details>
<details>
  <summary>해당 회원 로그 히스토리 정보 조회</summary>
    <div markdown="1">

    - POST /admin/member/history.do
    - 요청 : 이메일, 유저이메일

</div>
</details>