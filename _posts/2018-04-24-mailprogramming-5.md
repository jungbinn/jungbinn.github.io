---
layout: post
title: "매일 프로그래밍 5"
date: 2018-04-24
excerpt:
tags: [매일 프로그래밍, 알고리즘, mailprogramming, algorithm]
comments: true
---

### Q. 정수 배열과 타겟 숫자가 주어지면, 합이 타겟값이 되는 두 원소의 인덱스를 찾으시오. 단, 시간복잡도 O(n)이어야 합니다.
- - - 
<br/>


**예시)**

Input: [2, 5, 6, 1, 10], 타겟 8  

Output: [0, 2]  // 배열[0] + 배열[2] = 8

<br/>


**풀이)**

가장 간단하게 생각하면 전체 탐색으로 모든 조합을 검색해보면 되지만 이 경우 시간복잡도가 O(\\(n^{2}\\))이기 때문에 시간복잡도가 O(n)이어야 한다는 조건에 맞지 않는다. 한참 고민해봤지만 O(n)으로 만들 수가 없었다. 그래서 결국 해답을 봤는데 해시맵을 사용하는 것이었다. 해시맵을 사용하면 키값을 찾는 것을 O(1)으로 수행할 수 있다. 역시 stl이나 자료구조를 적절히 잘 사용하는 것도 중요한 것 같다.
  
찾아 보니 C++의 경우 unordered map이 hashmap의 표준인 것 같아서 unordered map을 사용했다.  

배열의 원소를 하나씩 탐색하면서 지금까지 저장한 해시맵에 (타켓 값 - 현재 인덱스의 값)의 값을 가진 원소가 들어있는지를 확인하고, 만약 없다면 현재 원소값을 키로, 현재 인덱스를 값으로 해서 해시맵에 하나를 새롭게 저장한다. 해시맵에 그 값이 있는지는 unordered_map.find()를 사용해서 O(1)에 수행 가능하다.  

이런 방법으로 배열을 한 번만 탐색하면서 합이 타겟값이 되는 두 원소를 찾을 수 있다.

<br/>

``` cpp
#include <vector>
#include <unordered_map>
#include <tuple>

using namespace std;

tuple<int, int> sumIndex (vector<int> arr, int n)
{
    unordered_map<int, int> map;
    tuple<int, int> answer = make_tuple (-1, -1);
        
    for (int i = 0; i < arr.size(); i++) {
        int remain = n - arr[i];
        auto search = map.find (remain);  // O(1) time complexity
        if (search != map.end())
        {
            answer = make_tuple (search->second, i);
            return answer;
        }
        map.insert ({arr[i], i});
    }

    return answer;  // no such combination
}
```

<br/>

시간복잡도 O(n)  
공간복잡도 O(n)


<br/>
<br/>

출처: mailprogramming.com

