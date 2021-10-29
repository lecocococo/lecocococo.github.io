---
date: 2021-10-29
title: "[Python] 파이썬 집합(set)자료형"
categories: Python
tags: 자료형 집합  set()
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

<br/>

# <span style="color:#58ACFA">파이썬 집합(set) 자료형</span>

## <span style="color:#58ACFA">집합(set)의 특징</span>

1. element간의 순서가 없다.
2. 중복이 허용되지 않는다.

## <span style="color:#58ACFA">집합 자료형 만들기</span>

```python
# 비어있는 set(집합)
s1 = set()
# 리스트를 입력하여 만드는 set
s2 = set([1, 2, 3, 4, 5])
# 문자열을 입력하여 만드는 set
s3 = set("PY")
# {}
s4 = {1, 2, 3}
```

## <span style="color:#58ACFA">합집합, 교집합, 차집합</span>

예제를 위한 집합 2개 선언

```python
s1 = set([1, 4, 5, 6])
s2 = set([3, 5, 6, 8])
```

<span style="color:#58ACFA">1. 합집합</span>

```python
# 방식1
s1 | s2
# 방식2
s1.union(s2)
```

결과: {1, 3, 4, 5, 6, 8}

<span style="color:#58ACFA">2. 차집합</span>

```python
# 방식1
s1 - s2  # s2 - s1
# 방식2
s1.difference(s2)  # s2.difference(s1)은 다른 결과가 나온다
```

결과: {1, 4}

<span style="color:#58ACFA">3. 교집합</span>

```python
# 방식1
s1 & s2
# 방식2
s1.intersection(s2)
```

결과: {5, 6}

## <span style="color:#58ACFA">집합간의 일치, 완전 불일치</span>

<span style="color:#58ACFA">1. 집합이 완전히 일치</span>  
 <span style="color:#81BEF7">`==`</span>을 사용하면 된다.

```python
s1 == s2
```

<span style="color:#58ACFA">2. 집합이 완전히 불일치(같은 원소가 하나라도 없는 것)</span>  
 <span style="color:#81BEF7">`isdisjoint()`</span>를 사용하면 된다.

```python
s1.isdisjoint(s2)
```

## <span style="color:#58ACFA">집합(set)과 관련된 함수들</span>

<span style="color:#58ACFA">1. add - 요소 추가</span>

```python
s1 = set([1, 4, 5, 6])
s1.add(3)
# 결과 {1, 4, 5, 6, 3}
```

- 중복 값은 무시가 된다.
- 중복 값을 넣어도 오류가 발생하지 않는다.

<span style="color:#58ACFA">2. remove - 요소 제거</span>

```python
s1 = set([1, 4, 5, 6])
s1.remove(4)
# 결과: {1, 5, 6}
```

- 집합(set) 내부에 값이 없다면 오류 생긴다.
- <span style="color:#81BEF7">`discard()`</span>를 사용하면 내부에 없는 값을 삭제해도 오류 발생하지 않는다.

<span style="color:#58ACFA">3. update - 여러개의 요소 추가</span>

```python
s1 = set([1, 4, 5, 6])
s1.update({2, 3}) #[2, 3]도 가능
# 결과: {1, 2, 3, 4, 5, 6}
```

<span style="color:#58ACFA">4. in - 집합 내부에 요소 존재여부 확인</span>

```python
s1 = set([1, 4, 5, 6])
if 1 in s1:
    print('yes')
# 결과: yes
```

<span style="color:#58ACFA">5. len - 집합 길이</span>

```python
s1 = set([1, 4, 5, 6])
print(len(s1))
# 결과: 4
```

<span style="color:#58ACFA">6. pop - 가장 앞의 요소를 가져온 후 제거</span>

```python
s1 = set([1, 4, 5, 6])
print(s1,pop())
# 결과: {1}
```

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
