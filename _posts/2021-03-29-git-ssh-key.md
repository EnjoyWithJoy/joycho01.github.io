---
title: '깃허브 계정 여러 개 사용하기'
categories:
  - 오답노트
tags:
  - git
  - ssh
---

github계정을 새로 만들면서 두 개의 계정을 관리할 필요가 생겼다.   
그 과정에서 진행했던 ssh-key 설정과 git config 설정에 대해 정리해보고자 한다.   

# git config

`git config`는 git의 사용 환경 설정을 확인하고 변경할 때 사용된다.   

1.  `/etc/gitconfig` 파일: 시스템의 모든 사용자와 모든 저장소에 적용되는 설정   
    `git config --system`옵션으로 이 파일을 읽고 쓸 수 있다.
2.  `/etc/gitconfig` 파일: 특정 사용자(즉, 현재 사용자)에게만 적용되는 설정   
    `git config --global`옵션으로 이 파일을 읽고 쓸 수 있다.
3.  `.git/config` 파일: 특정 저장소(혹은 현재 작업 중인 프로젝트)에만 적용되는 설정   
    `git config --local`옵션으로 이 파일을 읽고 쓸 수 있다.

참고: [시작하기 - Git 최초 설정](https://velog.io/@jay/multiplegithubaccounts)

# ssh-key

`ssh-key`는 서버에 접속할 때 비밀번호 대신 key를 제출하는 방식

```bash
$> ssh-keygen -t rsa -C "userA@my_email.com" -f "id_rsa_userA"
$> ssh-keygen -t rsa -C "userB@my_email.com" -f "id_rsa_userB"
```
`-t rsa`는 rsa라는 암호화 방식으로 키를 생성한다는 뜻   
`-C`는 주석을 입력할 수 있다. git hub에서는 사용자의 로그인 ID를 적어놓으라고 가이드한다.

참고: [한 컴퓨터에서 여러 개의 깃허브 계정 사용하기](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)

