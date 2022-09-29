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

<details>
  <summary>로그인한 유저 정보 표시</summary>
    <div markdown="1">

    - GET /api/member/info
    - 요청 :  이메일

</div>
</details>
<details>
  <summary>로그인한 유저 정보 수정</summary>
    <div markdown="1">

    - PATCH /api/member/info
    - 요청 : 이메일, 전화번호(수정 할 유저 정보)

</div>
</details>
<details>
  <summary>비밀번호 재설정</summary>
    <div markdown="1">

    - PATCH /api/member/password
    - 요청 : 이메일, 비밀번호

</div>
</details>
<details>
  <summary>금융상품 신청 내역 조회</summary>
    <div markdown="1">

    - GET /api/member/financial-instruments
    - 요청 : 이메일

</div>
</details>
<details>
  <summary>금융상품 신청 취소</summary>
    <div markdown="1">

    - POST /api/member/financial-instruments/cancel
    - 요청 : 이메일, 금융상품 신청 일련번호, 거래 식별 아이디

</div>
</details>

## 6. 계좌 페이지

<details>
  <summary>입・출력 계좌 생성</summary>
    <div markdown="1">

    - POST /api/account/open
    - 요청 : 이메일, 금융회사코드, 초기 잔액, 계좌비밀번호

</div>
</details>
<details>
  <summary>전체 계좌 정보 조회</summary>
    <div markdown="1">

    - GET /api/account
    - 요청 : 이메일

</div>
</details>
<details>
  <summary>해당 계좌 정보 조회</summary>
    <div markdown="1">

    - GET /api/account/info
    - 요청 : 이메일, 계좌번호

</div>
</details>
<details>
  <summary>해당 계좌 거래 내역 조회</summary>
    <div markdown="1">

    - GET /api/account/history
    - 요청 : 이메일, 계좌번호

</div>
</details>
<details>
  <summary>해당 계좌 해지 신청</summary>
    <div markdown="1">

    - POST /api/account/close
    - 요청 :  이메일, 비밀번호, 계좌번호

</div>
</details>

## 7. 이체 페이지

<details>
  <summary>이체 거래 요청</summary>
    <div markdown="1">

    - POST /api/transfer/transaction
    - 요청 :  이메일, 금융회사코드, 계좌번호, 거래 금액, 받는금융회사코드, 받는계좌번호, 수수료

</div>
</details>
<details>
  <summary>이체 상태 조회</summary>
    <div markdown="1">

    - GET /api/transfer/history
    - 요청 :  이메일, 거래종류

</div>
</details>
<details>
  <summary>이체 거래 취소 요청</summary>
    <div markdown="1">

    - POST /api/transfer/cancel
    - 요청 :  이메일, 거래식별아이디, 계좌번호

</div>
</details>

## 8. 정기예금 페이지

<details>
  <summary>전체 정기예금 정보 조회</summary>
    <div markdown="1">

    - GET /api/time-desposit
    - 요청 :  이메일

</div>
</details>
<details>
  <summary>상세 정기예금 정보 조회</summary>
    <div markdown="1">

    - GET /api/time-desposit/info
    - 요청 :  이메일, 정기예금 일련번호

</div>
</details>
<details>
  <summary>해당 정기예금 신청</summary>
    <div markdown="1">

    - POST /api/time-deposit/apply
    - 요청 :  이메일, 신청금융회사코드, 신청계좌번호금융상품코드, 금융회사코드,금융상품명, 신청금액, 저축금리유형, 저축금리유형명, 저축기간, 저축금리

</div>
</details>
<details>
  <summary>해당 정기예금 신청 취소</summary>
    <div markdown="1">

    - POST /api/time-deposit/cancel
    - 요청 :  이메일, 거래식별아이디
</div>
</details>


