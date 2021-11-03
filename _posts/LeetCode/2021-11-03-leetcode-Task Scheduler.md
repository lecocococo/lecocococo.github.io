---
date: 2021-11-03
title: "[LeetCode] Task Scheduler"
categories: LeetCode
tags: 알고리즘 leetcode
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

# <span style="color:#58ACFA">Task Scheduler</span>

## <span style="color:#58ACFA">문제</span>

![이미지](</assets/images/Task Scheduler.png> "Task Scheduler")
task는 처리하는데 1만큼의 시간이 걸리고 같은 task는 주어진 n만큼 쉬었다가 다시 작업에 들어가야할때 작업을 다 끝내는데 걸리는 시간을 반환하면된다.  
여기서 주어진 n만큼 쉬었다가 다시 작업에 들어가야할때 남아있는 다른 작업이 없다면 idle이 되어 1만큼의 시간을 보낸다.

## <span style="color:#58ACFA">풀이</span>

1. Counter를 이용하여 가장 많이 나온 순서대로 만든다.
2. 그리고 최빈도 task가 전부 수행되는데 필요한 시간을 idle 시간으로 잡는다.
3. Counter를 value만을 따로 빼내어 리스트를 만들어준다.
4. 만들어진 리스트를 돌면서 리스트 내의 value값과 (최빈도 task - 1) 값 중 작은값을 idle값에서 빼준다.  
   ( n=2 라고할때 `A _ _ A _ _ ...`이렇게 구성이 되는데 idle의 시간을 줄여 나가는 것이 때문에 value값이 더 크다면 A와 A사이에 들어있는 idle시간보다 커지기 떄문이다. )
5. idle시간이 존재하면 task의 길이에 더해주고 idle이 0보다 작아지면 task의 길이만을 반환한다. ( idle값이 음수가 된다는 것은 task에 idle값이 필요없고 task끼리 스케쥴링 될수 있다는 것이기 때문이다. )

_번외_ - heap을 이용하여 스케쥴링을 직접 해가며 구할 수도 있다.

## <span style="color:#58ACFA">코드</span>

```python
from heapq import heappush, heappop
from collections import Counter
class Solution:
    def leastInterval(self, tasks, n):
        # time = 0
        # heap = []
        # for key, val in Counter(tasks).items():
        #     heappush(heap, (-1*val, key)) # heapq가 minheap이기 때문에 maxheap처럼 사용하기위해 -1을 곱해줌
        # while heap:
        #     idx = 0
        #     temp = []
        #     while idx <= n:
        #         time += 1
        #         if heap:
        #             i,j = heappop(heap)
        #             if i != -1:
        #                 temp.append((i+1,j)) # 1개사용
        #         # 더이상 할 작업이 없다면 break
        #         if not heap and not temp:
        #             break
        #         else:
        #             idx += 1
        #     # 다시 heap에 넣기(-1보다 작은 숫자는 아직 남아있는 task가 있기 때문에)
        #     for item in temp:
        #         heappush(heap, item)
        # return time

        count = Counter(tasks)
        values = sorted(count.values())
        max_item = values.pop()
        curr_idle = (max_item - 1) * n

        for v in values:
            curr_idle -= min(v, max_item - 1)
        return max(curr_idle, 0) + len(tasks)
```

## <span style="color:#58ACFA">마무리</span>

이 문제는 동일한 task가 계속 수행되기 위해 쉬어야할때 다른 작업을 해야하는지 idle상태가 되어야하는지를 묻는 문제이다.  
즉, idle에 들어가야하는 시간을 계산하여 task의 수에 더해주면 되는 문제이다. ( heap을 이용하면 좀 더 복잡하긴 하다. )

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
