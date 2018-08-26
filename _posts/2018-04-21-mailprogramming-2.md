---
layout: post
title: "매일 프로그래밍 2"
date: 2018-04-21
excerpt: 
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 피보나치 배열은 0과 1로 시작하며, 다음 피보나치 수는 바로 앞의 두 피보나치 수의 합이 된다. 정수 N이 주어지면, N보다 작은 모든 짝수 피보나치 수의 합을 구하여라.
- - -
<br/>

**예제)**

Input: N = 12  
Output: 10 // 0, 1, 2, 3, 5, 8 중 짝수인 2 + 8 = 10
  
<br/>

**풀이)**

재귀함수를 사용해서 피보나치 수열을 구하면서 만약 현재 피보나치 수가 짝수라면 변수 sum에 더하도록 했다.

피보나치 수가 주어진 N보다 커지게 될 경우를 종료조건으로 두었다.

<br/>
  
``` cpp
int fibonacci (int a, int b, int n, int sum) {
	if (b > n) {
		return sum;
	}

	if (b % 2 == 0) {
		sum += b;
	}

	return fibonacci (b, a + b, n, sum);
}

int evenFibonacci (int N) {
	return fibonacci (0, 1, N, 0);
}
```
<br/>

예시 답안에서는 재귀함수를 사용하지 않고 반복문을 사용해서 풀이하였다.

``` cpp
int evenFibSum(int N) {
	int sum = 0;
	int x = 1;
	int y = 2;

	while (x <= N) {
		if (x % 2 == 0) {
			sum += x;
		}
		int z = x + y;
		x = y;
		y = z;
	}

	return sum;
}
```
<br/>
<br/>

출처: mailprogramming.com
