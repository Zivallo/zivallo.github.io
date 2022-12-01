---
title: Symbolic link / 파일종류 / Host / User / Group [Linux]
author: Soowan Cho
date: 2022-12-01 12:00:00 +0500
categories: [Linux, Concept]
tags: [Linux, Symbolic link, user, host, group, 파일종류]
---

## 1. Symbolic link (심볼릭 링크)
- 절대 경로 또는 상대 경로의 형태로 된 다른 파일이나 디렉토리에 대한 참조를 포함하고 있는 특별한 종류의 파일[^f1]
- 윈도우의 바로 가기와 비슷한 개념
```bash
# 기본꼴
$ ln -s [File 경로] [심볼릭 이름]
# 어디서나 사용하려면?
$ ln -s [File 경로] /usr/bin/[심볼릭 이름]
```
<img src="/assets/img/symboliclink/symbolic_link.jpg">

## 2. 리눅스 파일 종류

|파일 종류|문자|파일 종류|문자|
|---|---|---|---|
|Reguler File(일반파일)|-|Link File|l|
|Directory File|d|Device File(장치파일)|b(block), c(character)|

## 3. 사용자
<img src="/assets/img/symboliclink/user_host.jpg">

### 1. Host
- 네트워크에 연결되어 있는 장치, 컴퓨터
- 리눅스(다중 사용자 시스템)가 설치된 컴퓨터 한 대 자체가 Host
- host name 바꾸기
```bash 
$ sudo vi /etc/hostname # 내용 변경
```

### 2. User
- 리눅스 설치시 root 자동생성
  - 모든 user 들이 root 권한을 가지진 않음
  - sudo(substitute user do) : root 권한으로 명령어 수행


- 새로운 user 생성시
  - root 권한 X
  - /home/[user name] 디렉토리 생성됨
- User 생성 & 삭제
   - User 생성
```bash
$ sudo adduser [user name]
$ sudo useradd [user name] # 필요한 옵션을 명시해줘야 함
```
   - User 삭제
```bash
$ sudo deluser [user name]
$ sudo userdel [user name]
```
- User 변경
```bash
$ su [user name]
$ sudo su # root 계정 접속
$ exit # 계정 탈출
```

### 3. Group
- 보통 그룹 단위로, 권한을 단체 설정함
- adduser 시 user name와 동일한 그룹 자동생성
- 특정 user 그룹 확인
```bash
$ groups [user name]
```
- 그룹 생성 & 삭제
```bash
# 그룹 생성
$ sudo addgroup [group name]
# 그룹 삭제
$ sudo deluser [group name]
```
- Group 에 User 추가 및 제거
```bash
# 그룹에 사용자 추가
$ sudo gpasswd -a [user name] [group name]
# 그룹에 사용자 제거
$ sudo gpasswd -d [user name] [group name]
```
  
---
[^f1]: [Symbolic link(심볼릭링크)](https://ko.wikipedia.org/wiki/%EC%8B%AC%EB%B3%BC%EB%A6%AD_%EB%A7%81%ED%81%AC)