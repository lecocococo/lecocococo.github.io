---
date: 2021-11-03
title: "[LeetCode] Sqrt(x)"
categories: LeetCode
tags: 알고리즘 수학 leetcode
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

# <span style="color:#58ACFA">Sqrt(x)</span>

## <span style="color:#58ACFA">문제</span>

![이미지](</assets/images/Sqrt(x).png> "Sqrt(x)")
주어진 숫자 n의 제곱근을 구하여 소수점을 버리고 반환하는 문제이다.  
조건으로는 `pow(x, 0.5)` or `x ** 0.5`와 같은 오퍼레이터나 만들어져있는 지수 함수를 쓰지 않아야 된다는 것이다.

## <span style="color:#58ACFA">풀이</span>

빠른 방법:

1. 숫자를 제곱했을때 제곱한 값보다 주어진 숫자가 더 큰 경우 제곱을 한 숫자가 답이된다.  
   ex1) n=67이면 8\*8일때 주어진 값이 제곱한 값보다 커지므로 8을 반환하면 된다.
2. 이때 1부터 하나씩 늘여가면서 비교하는 것은 비효율적으므로 10씩 늘려가며 제곱하다가 제곱한 값이 주어진 값보다 커지면 1씩 줄여가며 비교하여 찾는다.

느린방법:

1. 1부터 하나씩 제곱근에서 소수를 제거한 부분을 보면 같은 답을 가지는 개수가 3, 5, 7, 9, 11 ... 이렇게 나오게된다.
2. 즉, 공차가 2인 등차수열이 만들어지게 되고 이를 이용하여 문제를 해결 할 수 있다.

## <span style="color:#58ACFA">코드</span>

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        # 느린방법
        # cnt = 0
        # su = 0
        # while x > su:
        #     su += (3+2*cnt)
        #     cnt += 1
        # return cnt

        # 빠른 방법
        num = 0
        while num * num < x:
            num += 10
        while num * num > x:
            num -= 1
        return num
```

## <span style="color:#58ACFA">마무리</span>

처음에는 하나씩 해보며 등차 수열인 것을 확인하여 문제를 풀어봐도 되지만 가장 빠른 방법은 제곱한 값과 비교하면서 찾아나가는 것이다.
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
