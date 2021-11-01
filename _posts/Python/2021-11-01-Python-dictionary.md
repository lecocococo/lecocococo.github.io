---
date: 2021-11-01
title: "[Python] 파이썬 딕셔너리 자료형"
categories: Python
tags: 자료형 딕셔너리 {}
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

# <span style="color:#58ACFA">파이썬 딕셔너리 자료형</span>

다른 언어에서는 해쉬로 사용되는 자료형이 파이썬에선 딕셔너리로 정의한다.

```python
dictionary = {'key_1':'value_1', 'key_2':'value_2', 'key_3':'value_3'}
```

딧셔너리는 {}로 감싸져 있고 key와 value가 한쌍으로 딕셔너리는 구성된다.

## <span style="color:#58ACFA">딕셔너리 key, value 쌍 추가</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary['c'] = 5

# 결과
# {'a':'pypy', 'b':[1,2], 3:4, 'c':5}
```

## <span style="color:#58ACFA">딕셔너리 key로 value값 가져오기</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary['b']

# 결과
# [1, 2]
```

## <span style="color:#58ACFA">딕셔너리 요소 삭제</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
del dictionary[3]

# 결과
# {'a':'pypy', 'b':[1,2]}
```

## <span style="color:#58ACFA">딕셔너리와 관련된 함수들</span>

<span style="color:#58ACFA">1. _items()_ - key, value 모든 쌍 가져오기</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary.items()

# 결과
# dict_items([('a', 'pypy'), ('b', [1,2]), (3, 4)])
```

- 쌍을 튜플로 묶은 dict_items 객체로 돌려준다.
- 리스트를 사용하는 것처럼 사용할 수 있다.

<span style="color:#58ACFA">2. _keys()_ - key 리스트 생성</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary.keys()

# 결과
# dict_keys(['a', 'b', 3])
```

- 리스트가 필요하다면 list()로 감싸주면 된다.

<span style="color:#58ACFA">3. _values()_ - value 리스트 생성</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary.values()

# 결과
# dict_keys(['pypy', [1,2], 4])
```

- 리스트가 필요하다면 list()로 감싸주면 된다.

<span style="color:#58ACFA">4. _get()_ - key로 value 가져오기</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary.get('a')

# 결과
# 'pypy'
```

<span style="color:#58ACFA">5. _pop()_ - key, value 쌍 삭제하기</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary.pop('a')

# 결과
# 'pypy'
```

- pop()하면 삭제된 값을 반환한다.

<span style="color:#58ACFA">6. _in_ - key가 딕셔너리에 들어있는지 확인하기</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
if 'a' in dictionary:
    print('true')

# 결과
# 'true'
```

<span style="color:#58ACFA">7. _update()_ - key의 value값 수정</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary.update('a' = 34)

# 결과
# {'a':34, 'b':[1,2], 3:4}
```

<span style="color:#58ACFA">8. _clear()_ - 딕셔너리의 모든 key, vlaue 쌍 삭제하기</span>

```python
dictionary = {'a':'pypy', 'b':[1,2], 3:4}
dictionary.clear()
print(dictionary)
# 결과
# {}
```

## <span style="color:#58ACFA">번외: defaultdict 사용하기</span>

기본적으로 사용하는 딕셔너리는 없는 키에 접근할 경우 에러가 발생하는데 `defaultdict`를 사용하면 에러가 발생하지 않고 기본값을 반환한다.

```python
from collections import defaultdict    # collections모듈에서 defaultdict를 가져온다.
dictionary = defaultdict(int)    # 기본값: int (호출시 0으로 나온다.)
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
