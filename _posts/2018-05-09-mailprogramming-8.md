---
layout: post
title: "매일 프로그래밍 8"
date: 2018-05-09
excerpt:
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 정수 배열(int array)이 주어지면 두 번째로 큰 값을 프린트하시오.
- - -

<br/>

**예제)**

Input: [10, 5, 4, 3, -1]  
Output: 5  

Input: [3, 3, 3]  
Output: Does not exist.

<br/>

**풀이)**

단순히 배열을 정렬한 다음 두 번째 원소를 프린트할 수도 있을 것이다. (시간복잡도 O(nlog(n)))

O(n)에 풀기 위해서 첫 번째와 두 번째로 큰 값을 저장하면서 배열을 탐색했다.

0번째 원소를 first, second에 저장하고 시작할 수도 있겠지만 탐색 후 두 번째로 큰 원소가 존재하지 않는 case를 검출하기 위해서 INT_MIN으로 초기화했다.


<br/>

``` cpp
#include <vector>
#include <climits>
#include <iostream>
using namespace std;

void secondLargest (vector<int> numbers) {
	int first = INT_MIN;
	int second = INT_MIN;

	/* Corner case 1. */
	if (numbers.size() < 2) {
		cout << "Does not exist." << endl;
		return;
	}

	for (int i = 0; i < numbers.size(); i++) {
		if (numbers[i] > first) {
			second = first;
			first = numbers[i];
		}
		else if (second < numbers[i] && numbers[i] < first) {
			second = numbers[i];
        }
	}

	/* Corner case 2. */
	if (second == INT_MIN) {
		cout << "Does not exist." << endl;
		return;
	}

	cout << second << endl;
}
```

<br/>

**시간복잡도 O(n)**  
**공간복잡도 O(1)**  

<br/>
<br/>

출처: mailprogramming.com
