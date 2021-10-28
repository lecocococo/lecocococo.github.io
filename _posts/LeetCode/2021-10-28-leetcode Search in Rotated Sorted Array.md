---
date: 2021-10-28
title: "[LeetCode] Search in Rotated Sorted Array"
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

# <span style="color:#58ACFA">Search in Rotated Sorted Array</span>

## <span style="color:#58ACFA">문제</span>

![이미지](/assets/images/Search in Rotated Sorted Array.png "Search in Rotated Sorted Array")

오름차순으로 정렬되어있는 배열에서 pivot index을 기준으로 배열을 회전시킨다. 회전된 배열에서 target으로 지정된 값의 index를 리턴하는 문제이다.(시간복잡도 제한: O(log n))

## <span style="color:#58ACFA">풀이</span>

1. 제약 조건으로 O(log n)이라는 시간복잡도를 주었으므로 이진 탐색을 이용한다(O(n)도 통과하긴 한다...)
2. 이진탐색을 위해서 중간 index를 정한다.
3. 어떤 pivot index를 기준으로 회전을 했던 중간 index를 기준으로 한쪽은 정렬된 상태로 나오게된다.
4. 정렬된 상태인 배열에서 target을 찾는다.  
   (정렬된 상태를 아는 방법:  
   왼쪽은 첫번째 배열 값이 중간 값보다 작으면 정렬된 상태  
   오른쪽은 중간값보다 배열의 마지막 값이 더 크면 정렬된 상태)
5. 없다면 정렬되지 않은 배열에서 target을 찾는다.
6. 반씩 줄여 나가며 답을 찾게 되므로 O(log n)에 탐색 할 수 있다.

## <span style="color:#58ACFA">코드</span>

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if len(nums)<1:
            return -1

        def binary_search(start, end):

            if start>end:
                return -1

            middle = (start + end)//2
            middle_val = nums[middle]

            if target == middle_val:
                return middle

            start_val = nums[start]

            if start_val <= middle_val:
                if start_val<=target and target<middle_val:
                    end = middle - 1
                else:
                    start = middle + 1
            else:
                if middle_val<target and target<=nums[end]:
                    start = middle + 1
                else:
                    end = middle - 1
            return binary_search(start, end)

        return binary_search(0,len(nums)-1)
```

## <span style="color:#58ACFA">마무리</span>

이 문제에서 시간 복잡도에 제약을 두었기 때문에 이진탐색을 이용 해야겠다는 것은 쉽게 생각이 가능하다. 따라서 이 문제의 핵심은 이진 탐색의 기준을 정하는 것이라고 할 수 있다.

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
