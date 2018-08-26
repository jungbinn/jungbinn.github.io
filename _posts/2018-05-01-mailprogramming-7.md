---
layout: post
title: "매일 프로그래밍 7"
date: 2018-05-01
excerpt:
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 주어진 string의 모든 단어를 거꾸로 하시오.
- - - 

<br/>

**예제)**

Input: "abc 123 apple"  
Output: "cba 321 elppa"  

<br/>

**풀이)**

string을 탐색하면서 space(' ')가 나오면 이전에 저장되어 있는 단어의 시작 인덱스부터 substring으로 쪼갠 후 reverse를 통해 거꾸로 뒤집고 새로운 string에 더해주는 방식으로 구현했다. 그런 다음 space의 다음 인덱스를 다음 단어의 시작점으로 저장하고, string이 끝날 때까지 같은 과정을 반복한다.

<br/>

``` cpp
#include <string>
#include <algorithm>
using namespace std;

string reverseString(string s) {
    string reversed = "";

    /* Parse, split and reverse the string. */
    int start = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == ' ') {
            string sub = s.substr(start, i - start);
            reverse(sub.begin(), sub.end());
            reversed += sub + " ";
            start = i + 1;
        }
        else if (i == s.length - 1) {
            string sub = s.substr(start, i - start + 1);
            reverse(sub.begin(), sub.end());
            reversed += sub;
        }
    }

    return reversed;
}
```

<br/>

**시간복잡도 O(n)**  
**공간복잡도 O(n)**

<br/>
<br/>

출처: mailprogramming.com
