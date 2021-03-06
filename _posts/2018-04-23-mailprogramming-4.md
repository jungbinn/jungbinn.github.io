---
layout: post
title: "매일 프로그래밍 4"
date: 2018-04-23
excerpt: 
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 정수(int)가 주어지면, 팰린드롬(palindrome)인지 알아내시오. 팰린드롬이란, 앞에서부터 읽으나 뒤에서부터 읽으나 같은 단어를 말합니다. 단, 정수를 문자열로 바꾸면 안됩니다.
- - -  
<br/>

**예제)**

Input: 12345  
Output: False

Input: -101  
Output: False

Input: 11111  
Output: True

Input: 12421  
Output: True
  
<br/>

**풀이)**

일단 예제를 보면 음수의 경우에는 무조건 팰린드롬이 아니기 때문에 음수 케이스를 먼저 걸러주었다.

음수를 제외한 정수에 대해서는 먼저 n을 10으로 나눠주면서 그 나머지를 리스트에 추가해주는 방식으로 주어진 숫자를 각 자리수로 쪼갰다.

그런 다음 for문을 통해 앞에서부터와 뒤에서부터의 i번째 값을 각각 비교해주면서 값이 서로 다를 경우 false를 return하도록 하였다. 만약 앞뒤 모든 자리의 값이 같아면 for문 종료 후 true를 return하게 된다.

<br/>

**시간복잡도 O(n), 공간복잡도 O(n)**

<br/>  
  
``` cpp
#include <vector>
using namespace std;

bool palindrome(int n) {
    if (n < 0) {
        return false;
    }

    /* Split given number into digits. */
    vector<int> digits;
    while (n > 0) {
        int digit = n % 10;
        n /= 10;
        digits.push_back(digit);
    }

    /* Compare each digits. */
    int size = digits.size();
    for (int i = 0; i < size / 2; i++) {
        int front = diits[i];
        int back = digits[size - 1 - i];
        
        if (front != back)
            return false;
    }

    return true;
}
```  
<br/>

**예시 답안)**

주어진 숫자를 전반과 후반으로 나눈 뒤 전반과 거꾸로 된 후반을 비교한다.

정수를 전반과 거꾸로 된 후반으로 나누는 방법은 일단 내가 사용한 방법과 똑같이 10으로 나눠주면서 자리수를 얻은 뒤, 거꾸로 된 후반을 나타내는 변수에 10을 곱하고 거기다 나머지를 더해주는 방식으로 나눠주었다.

이 방법을 거꾸로 된 후반이 전반보다 크거나 같을 때까지 반복한다.
만약 주어진 숫자의 길이가 홀수라면, 거꾸로 된 후반에서 1의 자리를 없애준다.
  
<br/>

이 방법의 경우 내 풀이보다 향상된 공간복잡도 O(1)을 가진다.

<br/>

``` cpp
bool isPalindrome(int n) {
    if (n < 0 || (n % 10 == 0 && n != 0)) {
        return false;
    }

    int revertedHalf = 0;
    while (n > revertedHalf) {
        revertedHalf = revertedHalf * 10 + n % 10;
        n /= 10;
    }

    return n == revertedHalf || n == revertedHalf / 10;
}
```

<br/>
<br/>

출처: mailprogramming.com
