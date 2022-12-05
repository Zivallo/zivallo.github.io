---
title: Symbolic link / 파일종류 / 권한 변경 [Linux]
author: Soowan Cho
date: 2022-12-04 12:00:00 +0500
categories: [Linux, Linux Concept]
tags: [Linux, Symbolic link, 파일종류, 파일정보, 권한변경]
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
<img src="/assets/img/Symbolic_link_file/symbolic_link.jpg">

## 2. 리눅스 파일 종류

|파일 종류|문자|파일 종류|문자|
|---|---|---|---|
|Reguler File(일반파일)|-|Link File|l|
|Directory File|d|Device File(장치파일)|b(block), c(character)|

## 3. 파일 정보
- ls -al 명령어로 파일 정보 확인 가능

<img src="/assets/img/Symbolic_link_file/ls_al.jpg">

1. 파일 종류
2. Owner Permission
3. Group Ownership Permission
4. Other[^f2] Permission
5. Link 수
6. Owner 
7. Group Ownership
8. 용량
9. 파일 생성 날짜
10. 파일명

- Permission(2,3,4)
  - r = 읽기(Read) : 파일을 읽을 수 있는 권한
  - w = 쓰기(Write) : 파일을 수정하거나, 쓰거나, 지울 수 있는 권한
  - x = 실행(Execute) : 파일을 실행할 수 있는 권한

## 4. 파일 정보(Owner, Group, 권한 ...) 설정

### 1. Owner User 와 Group 바꾸기
```bash
$ sudo chown [User name]:[Group name]
```

### 2. 권한 설정
   1. 권한 변경
```bash
# 기본틀
$ sudo chmod [변경할 mode] [File name]
# 권한 변경
$ sudo chmod u = rwx ./aaa
$ sudo chmod g = rw ./bbb
```
u = user(owner) / g = group / o = other / a = all(u+g+o)
   1. 권한 추가 / 제거
```bash
# 권한 추가
$ sudo chmod u+r ./aaa
$ sudo chmod a+w ./bbb
# 권한 제거
$ sudo chmod o-w ./aaa
```
   1. 2진수로 권한 변경
```bash
# 2진수로 권한 변경
$ sudo chmod 777 ./aaa # rwxrwxrwx = 111 111 111
$ sudo chmod 113 ./aaa # --x--x-wx = 001 001 011
```
  
  
---
[^f1]: [Symbolic link(심볼릭링크)](https://ko.wikipedia.org/wiki/%EC%8B%AC%EB%B3%BC%EB%A6%AD_%EB%A7%81%ED%81%AC)
[^f2]: Owner 와 Group Ownership 이 아닌 User