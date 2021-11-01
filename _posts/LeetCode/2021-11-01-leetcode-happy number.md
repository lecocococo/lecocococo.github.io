---
date: 2021-11-01
title: "[LeetCode] Happy Number"
categories: LeetCode
tags: 알고리즘 수학 leetcode
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

<br/>

# <span style="color:#58ACFA">Happy Number</span>

## <span style="color:#58ACFA">문제</span>

![이미지](/assets/images/Happy Number.png "Happy Number")
주어진 숫자가 happy number인지 아닌지 확인 하는 문제
(happy number은 문제의 example을 참고하면 알 수 있다.)

## <span style="color:#58ACFA">풀이</span>

1. 각 자리를 제곱하여 더한 값을 set에 저장한다.
2. 계속 1번을 하다가 같은 값이 나오면 순환(cycle)이 생긴다는 것이다.
3. cycle이 생기면 happy number가 될 수 없기때문에 False를 리턴한다.
4. 만약 제곱하여 더한 값이 1이 나오면 happy number이다.

## <span style="color:#58ACFA">코드</span>

```python
class Solution:
    def isHappy(self, n: int) -> bool:
        nums = set()
        while n!= 1:
            num = 0
            s = str(n)

            for i in s:
                num += int(i)**2

            if num in nums:
                return False

            nums.add(num)
            n = num
        return True
```

## <span style="color:#58ACFA">마무리</span>

이 문제의 핵심은 같은 값이 한번 더 나오면 순환이 생겨 happy number가 될 수 없다는 것이다.
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
