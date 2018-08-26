---
layout: post
title: "매일 프로그래밍 1"
date: 2018-04-21
excerpt: 
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 정수 배열(int array)이 주어지면 가장 큰 이어지는 원소들의 합을 구하시오. 단, 시간복잡도는 O(n).
- - -  
<br/>

**예제)**

Input: [-1, 3, -1, 5]  
Output: 7  // 3 + (-1) + 5

Input: [-5, -3, -1]  
Output: -1  // -1

Input: [2, 4, -2, -3, 8]  
Output: 9  // 2 + 4 + (-2) + (-3) + 8  
  
<br/>

**풀이)**

두 개의 정수 변수를 통해 현재의 local maximum과 global maximum을 각각 저장한다.

- Local maximum: 현재 원소와 (현재까지의 local maximum + 현재 원소) 중 큰 값을 저장
- Global maximum: 현재까지의 global maximum과 local maximum을 비교해서 가장 큰 값을 유지한다.  
<br/>
  
**시간복잡도 O(n), 공간복잡도 O(1)**  

<br/>  
  
``` cpp
#include <algorithm>
#include <vector>
using namespace std;

/* Given an int array, find the maximum sum of adjacent numbers. */
int LargestAdjacentSum (vector<int> array) {
    int localMax = array[0];
    int globalMax = array[0];

    for (int i = 1; i < array.size(); i++) {
        localMax = max(localMax + array[i], array[i]);
        globalMax = max(localMax, globalMax);
    }

    return globalMax;
}
```  
<br/>
<br/>

출처: mailprogramming.com
