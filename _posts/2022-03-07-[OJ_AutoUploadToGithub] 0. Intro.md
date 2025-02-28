---
title: 백준 코드 자동업로드 프로젝트 / 0. intro
date: 2022-03-07 13:14:30 + 0900
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [TAG]     # TAG names should always be lowercase
---

## 코드를 작성하기 전, 대략적인 프로그램의 동작 순서

1. 매 시간마다 사용자의 유저페이지에서 '맞았습니다'의 개수가 이전 시간과 다른지 확인한다.
1. 다르다면, 새롭게 맞은 문제들의 코드를 사용자의 깃에 등록한다.

<br>
각 과정을 수행하기 위해선 어떤 것들이 필요할까?

---

### 1. 매 시간마다 사용자의 유저페이지에서 '맞았습니다'의 개수가 이전 시간과 다른지 확인한다.


#### 1. '매 시간마다'

매 시간마다 프로그램을 작동시키기 위해서는 24시간 동작할 서버가 필요하다. -> 오라클 free tier 사용

#### 2. '사용자'

프로그램을 이용하는 사용자의 계정을 기준으로 작동할것이기 때문에 사용자의 계정에 로그인 할 필요가 있다. -> id, pw를 저장해 로그인하거나, 한번 로그인 한 후 연결이 끊어지지 않도록 계속 동작한다.

#### 3. '유저페이지'

CLI환경에 서버에서 특정 페이지에 접근하기 위해서는 크롤러가 필요하다. -> 셀레니움 사용

#### 4. ''맞았습니다'의 개수가 이전 시간과 다른지 확인'

'맞았습니다'의 개수를 세는 것은 유저페이지에 접근한 이후라면 어렵지 않지만, 이전 시간보다 몇개가 더 늘었는지 확인하기 위해서는 이전 시간의 '맞았습니다' 개수를 저장할 필요가 있다.

<br>
<br>

### 2. 다르다면, 새롭게 맞은 문제들의 코드를 사용자의 깃에 등록한다.


#### 1. '새롭게 맞은 문제들의 코드'

코드 역시 마찬가지로 크롤러를 통해 쉽게 접근할 수 있다.

#### 2. '사용자'

사용자의 깃에 권한을 갖고 접근하려면, BOJ와 마찬가지로 사용자의 계정으로 로그인 해야한다. -> id, pw를 저장해 로그인하거나, 한번 로그인 한 후 연결이 끊어지지 않도록 계속 동작한다.

#### 3. '깃에 등록한다'

깃에서 제공하는 REST API 또는 pygithub 패키지를 이용해 코드를 해당 사용자의 리포지토리에 push한다.