---
date: 2021-10-29
title: "[LeetCode] Search a 2D Matrix II"
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

# <span style="color:#58ACFA">Search a 2D Matrix II</span>

## <span style="color:#58ACFA">문제</span>

![이미지](/assets/images/Search a 2D Matrix II(1).png "Search a 2D Matrix II")
![이미지](/assets/images/Search a 2D Matrix II(2).png "Search a 2D Matrix II")
![이미지](/assets/images/Search a 2D Matrix II(3).png "Search a 2D Matrix II")
모든 행과 열은 오름차순으로 정렬되어있는 2차원 배열에 target 숫자r가 있는지 없는지 찾는 문제이다.

## <span style="color:#58ACFA">풀이</span>

1. 첫번쨰 열을 보았을때 target보다 큰 값이 있다면 그 행은 target이 있을수 없다.
2. 첫번째 열의 값 중 target보다 작다면 그 행에 값이 존재할 가능성이 있다는 것이다. (무조건 적으로 있지 않다.)

## <span style="color:#58ACFA">코드</span>

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m, n = len(matrix), len(matrix[0])
        row, col = m-1, 0
        # example의 배열로 보자면 18부터 검사한 것이다.
        while row >= 0 and col < n:
            if target > matrix[row][col]: # target보다 작다면 그 행에 값이 존재할 가능성이 있다
                col += 1
            elif target < matrix[row][col]: # arget보다 큰 값이 있다면 그 행은 target이 있을수 없다
                row -= 1
            else:
                return True

        return False
```

## <span style="color:#58ACFA">마무리</span>

이 문제의 주요 요점은 target보다 큰 경우와 작은 경우에 행이 검사되어야 하는지 검사가 필요없는지를 알아내는 것이다. (정렬되있다는 조건으로부터 알아낼수 있다.)

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
