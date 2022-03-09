---
title: 백준 코드 자동업로드 프로젝트 / 1. login
date: 2022-03-08 00:10:00 + 0900
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [TAG]     # TAG names should alw`ays be lowercase
---

###1. fiddler를 이용해 boj에서 로그인을 할 때 id, pw가 어떤식으로 서버에 전송되는지 분석한다.

확인해본 결과, /signin의 body에 내가 입력한 id와 pw가 저장되어 전송되는 것을 볼 수 있었다.
<br>
그런데, 아래에 'g-recaptcha-response'라는 마치 토큰이나 키값처럼 보이는 값이 같이 있었고, 매번 테스트 할 때마다 값이 달라지는 것을 보고 id, pw를 통해서 자동 로그인을 하는 것이 불가능하다고 생각했었다.
<br>
위와같은 문제때문에 처음에는 auto-login을 켜고 한번만 로그인을 하는 방식으로 진행하려 했으나, /signin이 전송되기 바로 직전 google의 recaptcha api를 통해 k라는 값을 파라메터로 전송하는 것을 확인할 수 있었고, 그 값이 매번 일정하다는 것을 알게되었다.
<br>
그러나, body를 확인한 결과, 'g-recaptcha-response' google에 보내는 패킷에도 포함되어있었고, 단순히 접근할 수 있는 것인지 알 수 없게되었다.

<br>
해봐야 할 것

1. 'g-recaptcha-response' 안보내도 로그인 되는지 확인하기

1. recaptcha api를 내가 사용해도 'g-recaptcha-response'를 받을 수 있는지 확인하기

