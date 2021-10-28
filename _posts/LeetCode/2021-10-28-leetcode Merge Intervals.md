---
date: 2021-10-28
title: "[LeetCode] Merge Intervals"
categories: LeetCode
tags: 알고리즘 정렬 leetcode
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

<br/>

# Merge Intervals

## 문제

<!-- <img src="/assets/images/Merge Intervals.png" title="Merge Intervals" alt="Merge intervals"> -->

![이미지](/assets/images/Merge Intervals.png "Merge Intervals")
여러 개의 interval들이 주어지고 겹치는 부분이 있다면 겹치는 interval들을 모두 포함하는 하나의 interval들을 만들어주는 문제이다. 예시를 통해서 알 수 있듯이 [1, 3], [2, 6] => [1, 6] 이런식으로 포함하도록 interval을 생성해준다. 그리고 [1, 4], [4, 5] => [1, 5]로 시작과 끝이 같아도 겹쳐진다고 본다.

## 생각

1. 일단 시작을 기준으로 오름차순 정렬
2. 시작이 같은 경우 끝을 기준으로 오름차순으로 정렬
3. 첫번째 interval과 두번째 interval을 비교
4. 정렬을 해두었기 때문에 첫번쨰 interval이 새로 만들어지게 되는 새로운 interval의 시작이 된다.
5. 첫번째 interval의 끝과 두번째 interval의 시작을 비교해서 첫번째 interval의 끝이 크다면
   두번째 interval이 첫번째 interval가 겹치는 부분이 있다는 것이다.
6. 반대로 첫번째 interval의 끝이 작다면 겹치지 않는다는것이다.(새로 만들어진 interval이 result에 포함되어지고 다시 새로운 interval을 만들어야 할때이다.)
7. 새로 만들어지는 interval의 끝부분은 첫번째 interval의 끝과 두번째 interval중 더 큰값이 된다.
8. for문을 돌면서 계속 확인

## 코드

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        arr = sorted(intervals, key = lambda x: (x[0],x[1])) # 오름차순 정렬
        result = []
        temp = [0, 0] # 새로만들어질 interval
        start = 0
        end = 0
        for i in range(len(arr)):
            if i == 0: # 첫번째 interval의 경우
                temp = arr[i]
                start = temp[0]
                end = temp[1]
                continue
            if arr[i][0] <= end: # 두 interval간의 시작, 끝 비교
                temp[1] = max(end,arr[i][1]) # 더 큰 값이 새로 만들어지는 interval의 끝이된다.
                end = temp[1]
            else: # 새로운 interval의 끝이 두번째의 시작보다 더 작은경우
                result.append(temp)
                temp = arr[i]
                start = temp[0]
                end = temp[1]
        result.append(temp)
        return result
```

## 마무리

이 문제 같은 경우는 정렬만 잘하고 비교만 잘하면 풀리는 문제이다.

{% if page.comments %}

<div id="disqus_thread"></div>
<script>
    /**
    *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
    *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    var disqus_config = function () {
        this.page.url = "{{ page.url | absolute_url }};";  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = "{{ page.id }}";; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    (function() { // DON'T EDIT BELOW THIS LINE
        var d = document, s = d.createElement('script');
        s.src = 'https://lecocococo-blog.disqus.com/embed.js';
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();

</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}
