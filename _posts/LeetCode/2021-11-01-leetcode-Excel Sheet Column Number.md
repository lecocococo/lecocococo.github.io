---
date: 2021-11-01
title: "[LeetCode] Excel Sheet Column Number"
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

![이미지](/assets/images/Excel Sheet Column Number(1).png "Excel Sheet Column Number")
주어진 excel sheet를 보고 주어진 string의 값을 숫자로 리턴해주면 되는 문제이다.

## <span style="color:#58ACFA">풀이</span>

1. "A"부터 "Z" 까지는 딕셔너리로 저장해둔다. (ex) {"A": 1, "B": 2, })
2. 그리고 마치 26진수를 10진수로 바꾸는 것처럼 계산해주면된다.(1의 자리는 26의 0승, 10의 자리는 26의 1승)
3. 10진수로 바꾸는 것처럼 계산을 해줄때 문자의 값은 딕셔너리로 부터 가져와서 곱해주면된다.

## <span style="color:#58ACFA">코드</span>

```python
class Solution:
    def titleToNumber(self, columnTitle: str) -> int:
        dict = {}
        cnt = 1

        for i in range(26):
            dict[chr(65 + i)] = i+1

        # print(dict)

        result = 0
        i = 0
        for ch in columnTitle[::-1]:
            result+=(math.pow(26,i))*dict[ch]
            i+=1

        return int(result)
```

## <span style="color:#58ACFA">마무리</span>

"A"부터 "Z"까지 딕셔너리에 저장해두고 26진수를 10진수로 바꾸는것처럼 계산만 해주면 되는 문제이다.

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
