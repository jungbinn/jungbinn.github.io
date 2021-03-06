---
layout: post
title: "매일 프로그래밍 3"
date: 2018-04-22
excerpt: 
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 정수 n이 주어지면, n개의 여는 괄호 "("와 n개의 닫는 괄호 ")"로 만들 수 있는 괄호 조합을 모두 구하시오. (시간복잡도 제한 없음)
- - -  
<br/>

**예제)**

Input: 1  
Output: ["()"]

Input: 2  
Output: ["(())", "()()"]

Input: 3  
Output: ["((()))", "(()())", "()(())", "()()()"]
  
<br/>

**풀이)**

empty string "" 에서부터 시작해서 여는 괄호 "("를 추가해 주거나 닫는 괄호 ")"를 추가해 준 재귀함수를 각각 호출한다.

이 때 여는 괄호의 개수가 n개보다 작을 때만 여는 괄호를 추가하고, 괄호를 연 만큼만 닫아줘야 하므로 다는 괄호의 개수가 여는 괄호의 개수보다 작을 때만 닫는 괄호를 추가한다.

닫힌 괄호의 개수가 n개에 도달하면 해당 괄호 조합이 모두 끝난 것이므로 리스트에 추가해준 후 return한다.

<br/>  
  
``` cpp
#include <string>
#include <vector>
using namespace std;

void parenthesis(int num, int open, int close, string s, vector<string> list) {
    /* Complete, push to the list */
    if (close == num) {
        list.push_back(s);
        return;
    }

    /* Can add a opening parenthesis */
    if (open < num) {
        parenthesis(num, open + 1, close, s + "(", list);
    }

    /* Can add a closing parenthesis */
    if (close < open) {
        parenthesis(num, open, close + 1, s + ")", list);
    }
}
```  
<br/>
<br/>

출처: mailprogramming.com
