---
date: 2021-11-03
title: "[LeetCode] Majority Element"
categories: LeetCode
tags: 알고리즘 leetcode
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

# <span style="color:#58ACFA">Majority Element</span>

## <span style="color:#58ACFA">문제</span>

![이미지](</assets/images/Majority Element.png> "Majority Element")
list에서 list 크기의 절반 이상 등장하는 majority element를 반환하는 문제이다.

## <span style="color:#58ACFA">풀이</span>

1. 가장 간단하게는 nums리스트를 정렬하고 정렬한 nums리스트에서 `nums[len(nums)//2]`를 반환하면 된다.( majority element는 무조건 list 크기의 절반 이상 나타나기 때문이다. )
2. 두번 째로는 collections 모듈의 Counter와 most_common()함수를 이용하여 구하는 방법이 있다.

## <span style="color:#58ACFA">코드</span>

```python
from collections import Counter
class Solution:
    def majorityElement(self, nums: List[int]) -> int:

        # return Counter(nums).most_common(1)[0][0]

        nums.sort()
        return nums[len(nums)//2]
```

## <span style="color:#58ACFA">마무리</span>

majority element의 정의를 잘 본다면 어렵지 않은 문제이다.

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
