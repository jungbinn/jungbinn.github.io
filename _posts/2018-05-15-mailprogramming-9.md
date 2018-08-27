---
layout: post
title: "매일 프로그래밍 9"
date: 2018-05-15
excerpt:
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 정수 배열(int array)이 주어지면 0이 아닌 정수 순서를 유지하며 모든 0을 배열 오른쪽 끝으로 옮기시오. 단, 시간복잡도는 O(n), 공간복잡도는 O(1)이어야 합니다.
- - -

<br/>

**예제)**

Input: [0, 5, 0, 3, 1]  
Output: [5, 3, -1, 0, 0]  

Input: [3, 0, 3]  
Output: [3, 3, 0]  

<br/>

**풀이)**

먼저 주어진 배열 내의 0의 개수를 센 다음, 0이 아닌 나머지 원소들을 앞으로 당겨준다.

그런 다음 그 뒤에 0을 개수에 맞게 넣어준다.

<br/>

``` cpp
#include <vector>
using namespace std;

vector<int> moveZero (vector<int> vec) {
    /* First, get the number of zeros. */
    int count = 0;
    for (int i = 0; i < vec.size(); i++) {
        if (vec[i] == 0) {
            count ++;
        }
    }

    /* Then, move nonzero numbers. */
    int cur = 0;
    for (int i = 0; cur < vec.size() - count; i++) {
        if (vec[i] == 0) {
            continue;
        }
        vec[cur] = vec[i];
        cur++;
    }

    /* Finally, append zeros at the back. */
    for (int i = vec.size()-count; i < vec.size(); i++) {
        vec[i] = 0;
    }

    return vec;
}
```

<br/>

**시간복잡도 O(n)**  
**공간복잡도 O(1)**  

<br/>
<br/>

출처: mailprogramming.com
