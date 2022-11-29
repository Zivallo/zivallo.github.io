---
title: 유클리드 호제법(Euclidean algorithm) [C++]
author: Soowan Cho
date: 2022-11-11 12:00:00 +0500
categories: [Algorithm, Concept]
tags: [Algorithm, GCD,LCM]
---

## 1. 정의
2개의 자연수의 최대공약수[^f1]를 구하는 알고리즘[^f2]

mod(%) 연산자[^f3]를 통해 최대공약수를 구할 수 있다.

## 2. 예시
<img src="/assets/img/Euclidean-Algorithm/Eucildean-algorithm-pic1.jpg"></img>

1. a 와 b를 mod 연산한다.
2. mod 연산의 결과가 0이 아닐시, b를 기준으로 mod 결과를 다시 mod 연산한다.
3. mod 연산의 결과가 0일 때까지 반복한다.
4. mod 연산의 결과가 0일 떄, b 가 최대공약수가 된다.

## 3. 코드
```c++
int gcd(int a,int b){
    int c = a % b;
    while(c){
        a = b;
        b = c;
        c = a % b;
    }
    return b;
}
```
> a × b = GCD(a, b)[^f1] × LCM(a, b)[^f2] 성질을 이용하여 최소공배수[^f4]도 구할 수 있다.  
{: .prompt-tip }

## 4. 관련 문제
- [[BOJ] 최대공약수와 최소공배수](https://www.acmicpc.net/problem/2609)

## 5. 용어 및 출처

[^f1]: [GCD(Greatest Common Divisor) = 최대공약수 : 두 수의 공약수 중 가장 큰 하나](https://ko.wikipedia.org/wiki/%EC%B5%9C%EB%8C%80%EA%B3%B5%EC%95%BD%EC%88%98)

[^f2]: [유클리드 호제법](https://ko.wikipedia.org/wiki/%EC%9C%A0%ED%81%B4%EB%A6%AC%EB%93%9C_%ED%98%B8%EC%A0%9C%EB%B2%95)

[^f3]: [mod(%) 연산 : 어떤 한 숫자를 다른 숫자로 나눈 나머지를 구하는 연산](https://gamedevlog.tistory.com/44)

[^f4]: [LCM(Least common multiple) = 최소공배수 : 두 수의 양의 공배수 중 가장 작은 수 하나](https://ko.wikipedia.org/wiki/%EC%B5%9C%EC%86%8C%EA%B3%B5%EB%B0%B0%EC%88%98)
