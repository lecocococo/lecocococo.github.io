---
date: 2021-11-01
title: "[LeetCode] Factorial Trailing Zeroes"
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

# <span style="color:#58ACFA">Factorial Trailing Zeroes</span>

## <span style="color:#58ACFA">문제</span>

![이미지](/assets/images/Factorial Trailing Zeroes.png "Factorial Trailing Zeroes")

## <span style="color:#58ACFA">풀이</span>

1. 르장드르 공식의 특별한 case이고 5의 다중도로 결정이 됨
2. 쉽게 생각하면 n이 5의 배수일때마다 뒤에 0이 하나씩 붙는다(팩토리얼 계산기로 돌려보면 증명은 안되지만 눈으로 볼 수는 있다.)

## <span style="color:#58ACFA">코드</span>

```python
class Solution:
    def trailingZeroes(self, n: int) -> int:
        # 르장드르 공식의 특별한 case
        # 5의 다중도로 결정이 됨
        # 쉽게 생각하면 n이 5의 배수일때마다 뒤에 0이 하나씩 붙는다

        # exp = 1
        # while 1:
        #     p = math.pow(5,exp)
        #     if p>n:
        #         break
        #     exp+=1
        # result = 0
        # for j in range(1,exp):
        #     result += (n//math.pow(5,j))
        # return int(result)

        result = 0
        while n > 0:
            result += n // 5
            n = n // 5
        return result
```

## <span style="color:#58ACFA">마무리</span>

수학적 지식이 부족하여 증명은 안되었지만 팩토리얼을 돌려본 결과 주어진 숫자가 5의 배수 일때마다 뒤에 0이 붙는 것을 알 수 있다.

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
