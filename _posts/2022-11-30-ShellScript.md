---
title: Shell Script [Linux]
author: Soowan Cho
date: 2022-11-30 12:00:00 +0500
categories: [Linux, Linux Shell]
tags: [Linux, Shell Script]
---

## 1. Shell Script
- 자동화 프로그램 만들 때 사용<br>
- 확장자 : .sh<br>
- 실행법
```bash
$ source [File Name].sh
$ ./go.sh # 실행권한 줘야함, 간헐적으로 사용
```

> CLI Shell 여러 가지 존재- bash, dash 등등 ...<br>bash : 기능 많음, 주로 리눅스<br>dash : 경량, 임베디드에 많이 씀<br>shell 확인법 : $cat /etc/shells
{: .prompt-tip }


## 2. 작성 문법
### 1. Shebang(쉬뱅, #!)
- 파일 맨위에 작성<br>
- 어느 Shell 인지 나타냄
```bash
#!/bin/bash (bash shell)
#!/bin/sh (dash shell)
```

### 2. 출력 & 입력
- 출략 : echoㅤㅤㅤ입력 : read

### 3. 변수
- 모든 값을 문자열로 취급

```bash
#!/bin bash

# 선언
변수명=값
NAME=ZIVALLO

# 변수 사용
$변수명
echo "My name is "$NAME
```

<img src="/assets/img/ShellScript/variable.jpg">

### 4. Argument
- 받은 Argument를 $1, $2, $3 ... 로 사용가능

```bash
#!/bin bash

# Argument 사용
echo $1
echo $2
echo $3
```

<img src="/assets/img/ShellScript/argument.jpg">

### 5. 산술 연산
- $(( )) 사용

```bash
#!/bin bash

echo $(($1+$2))
```

<img src="/assets/../../assets/img/ShellScript/operator.jpg">

### 6. 한줄 주석
```bash
# 한줄 주석
```


### 7. 실행결과 변수 저장
- 변수명=$(Shell 명령어)

```bash
#!/bin bash

echo $(date)
```

<img src="/assets/img/ShellScript/cmd.jpg">

### 8. if문[^f1]
- 띄어쓰기 중요
- 비교식

|비교식|의미|비교식|의미|
|---|---|---|---|
|-lt|<(less than)|-gt|>(greater than)|
|-le|<=|-ge|>=|
|-eq|=|-ne|!=|
|\|\||or|&&|and|

- 파일 관련 조건식

|조건식|의미|조건식|의미|
|---|---|---|---|
|-n "문자열"|문자열길이 > 0 일때|-z "문자열"|문자열길이 == 0 일때|
|-x "파일"|파일 존재, 권한 실행(+x) 일때|-f "파일" |파일 존재, Ruguler 파일 일때|

```bash
#!/bin bash

a=$1

if [ $a = "100" ];then
   echo first
elif [ $a -eq "200" ];then
   echo second
else
   echo third
fi
```
<img src="/assets/img/ShellScript/if1.jpg">

> for, printf, 함수, 배열 사용 가능하지만 자주 사용하지 않음.
{: .prompt-tip }

## 3. Environmet Variable(환경 변수)
- Shell 에 저장되는 변수 (사용자, Process, 리눅스 등 다같이 사용)
- 터미널 종료시 없어짐 -> ~/.bashrc[^f2] 에 추가


```bash
# 환경 변수 전체 읽기
$ printenv

# 하나만 읽기
$ echo $변수명
$ printenv | grep [변수명]

# 변수 저장
export [변수명]=[값]

# 변수 제거
unset [변수명]
```

## 4. alias
- 별명을 만들어내는 명령어
```bash
alias f1='mkdir ./ziv;ls'
alias f2='rm -r ./ziv;ls'
```
<img src="/assets/img/ShellScript/alias.jpg">

## 5. Crontab
- 주기적으로 Shell Script 파일 수행시켜야 할때 사용
1. Shell Script 파일 작성
2. sh 파일에 +x 실행권한 주기
```bash
$ sudo chmod +x ~/test.sh
```
3. /etc/crontab 파일에 추가
```bash
$ sudo vi /etc/crontab
```
<img src="/assets/img/ShellScript/crontab.jpg">

      |표현식|의미|
      |---|---|
      |* * * * *|매 분마다 수행|
      |*/5 * * * *|매 5분마다 수행|
      |* */5 * * *|매 5시간마다 수행|
      |* 8 * * *|매일 8시마다 수행|


---
[^f1]: [Shell script(쉘) if 조건문, 조건식](https://hand-over.tistory.com/32)
[^f2]: bash shell이 시작될때 자동 시작되는 bash script 파일