---
layout: post
title: "매일 프로그래밍 6"
date: 2018-04-25
excerpt:
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 간격(interval)으로 이루어진 배열이 주어지면, 겹치는 간격 원소들을 합친 새로운 배열을 만드시오. 간격은 시작과 끝으로 이루어져 있으며, 시작은 끝보다 작거나 같습니다.
- - -
<br/>


**예제)**

Input: [[2, 4], [1, 5], [7, 9]]  

Output: [[1, 5], [7, 9]]  


Input: [[3, 6], [1, 3], [2, 4]]  

Output: [[1, 6]]

<br/>


**풀이)**

먼저 각 interval을 표현하는 struct interval을 만들고, 두 struct interval의 start 원소를 비교하는 compare 함수를 만들었다. 이 compare 함수를 sort에 인자로 넘겨주어 start값의 오름차순으로 배열을 정렬할 수 있다.

이렇게 정렬 후 배열을 탐색하면서 만약 앞 원소의 end 값보다 현재 원소의 start값이 더 작다면 두 interval을 합쳐주면 된다.

<br/>

``` cpp
#include <algorithm>
#include <vector>
using namespace std;

struct interval {
    int start;
    int end;
}

bool compare (struct interval a, struct interval b) {
    return a.start < b.start
}

vector<struct interval> mergeInterval (vector<struct interval> intervals) {
    /* Sort the list by start of the intervals */
    sort(intervals.begin(), intervals.end(), compare);

    /* Compare the intervals and merge */
    vector<struct interval> merged;
    merged.push_back(intervals[0]);
    for (int i = 1; i < intervals.size(); i++) {
        if (merged.back().end > intervals[i].start) {
            struct interval newInterval = merged.back();
            merged.pop_back();
            newInterval.end = max(newInterval.end, intervals[i].end);
            merged.push_back(newInterval);
        }
        else {
            merged.push_back(intervals[i]);
        }
    }
    
    return merged;
}
```

<br/>

**시간복잡도 O(nlog(n))**  
**공간복잡도 O(n)**

<br/>
<br/>

출처: mailprogramming.com
