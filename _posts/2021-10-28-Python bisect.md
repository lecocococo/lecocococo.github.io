---
date: 2021-10-28
title: "[Python] bisect 사용법/이진 탐색(Binary Search)"
categories: Python
tags: 파이썬모듈 알고리즘 이진탐색
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

<br/>
# <span style="color:#58ACFA">파이썬 bisect</span>

bisect 모듈은 이진탐색 알고리즘이 구현되어 있는 모듈이다.
bisect를 사용하면 간결하게 이진 탐색의 결과를 알 수 있다.
import bisect를 이용하면 모듈을 불러올 수 있다.

## <span style="color:#58ACFA">bisect_left()</span>

정렬된 배열에서 삽입할 값의 인덱스를 return해준다.
만약 이미 삽입할 값이 배열에 존재한다면 기존 배열내의 값의 앞(왼쪽)의 인덱스가 반환된다.
<span style="color:#81BEF7">`bisect_left(정렬된 배열, 삽입 값)`</span>을 통해서 사용할 수 있다

ex1)

```python
from bisect import bisect_left # import
arr = [1,2,3,5]
num = 4
index = bisect_left(arr,num)
print(index)
```

3이라는 값이 print된다

ex2)

```python
from bisect import bisect_left # import
arr = [1,2,4,4,5]
num = 4
index = bisect_left(arr,num)
print(index)
```

2라는 값이 print된다.

## <span style="color:#58ACFA">bisect_right(), bisect.bisect()</span>

bisect_left()와 비슷하지만 삽입할 값이 배열에 존재한다면 기존 배열내의 값의 뒤(오른쪽)의 인덱스가 반환된다는것이 차이점이다.

ex1)

```python
from bisect import bisect_right# import
arr = [1,2,3,5]
num = 4
index = bisect_right(arr,num)
print(index)
```

3이라는 값이 print된다

ex2)

```python
from bisect import bisect_right # import
arr = [1,2,4,4,5]
num = 4
index = bisect_right(arr,num)
print(index)
```

4라는 값이 print된다.

## <span style="color:#58ACFA">정리</span>

기본적으로 이진 탐색에 대해 배울때

```python
# 전체적인 형식입니다. 돌아가지 않습니다!
left, right = 0, len(nums)-1
while left < right:
    middle=(left+right)//2
    if nums[m]<target_num:
        left=middle+1
    else:
        right=middle
```

이런식으로 배우게 된다. 물론 위의 방식이 더 문제 해결에 도움이 될 수 있다. 하지만 간단하게 이진 탐색으로 위치를 찾는 경우에 파이썬에서는 bisect를 이용하여 더 간결하게 코드를 작성 할 수 있다.  
<br/>

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
