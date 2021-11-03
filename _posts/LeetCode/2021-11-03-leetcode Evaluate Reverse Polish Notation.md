---
date: 2021-11-03
title: "[LeetCode] Evaluate Reverse Polish Notation"
categories: LeetCode
tags: 알고리즘 수학 leetcode
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

# <span style="color:#58ACFA">Evaluate Reverse Polish Notation</span>

## <span style="color:#58ACFA">문제</span>

![이미지](</assets/images/Evaluate Reverse Polish Notation.png> "Evaluate Reverse Polish Notation")
tokens 리스트는 마치 트리에 들어있는 식을 후위순회한 후와 같은 상태이다. 이식을 계산해서 계산 결과를 반환하는 문제이다.

## <span style="color:#58ACFA">풀이</span>

1. 식이 트리에 있다고 생각해본다.
2. 트리에 있는 식을 후위순회한 결과가 tokens와 같다는 것을 확인 할 수 있다.
3. tokens를 잘 살펴보면 무조건 첫번째 기호가 첫번째로 계산된다.
4. 그리고 첫 번째 기호 계산시 기호 앞에 2개의 숫자는 항상 존재한다.
5. stack을 이용하여 숫자는 모두 append한다.
6. 기호가 나오면 stack에서 2개의 숫자를 pop하여 계산한다.
7. 계산한 값을 다시 스택에 append한다.
8. 마지막 하나가 남을때 까지 수행한다.

## <span style="color:#58ACFA">코드</span>

```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        # 무조건 첫번째 기호가 첫번째로 계산된다
        # 첫번째 기호 계산시 무조건 앞에 2개의 숫자는 존재한다

        # list 이용 (느림)
        # rpn = tokens
        # op = ['+', '-', '*','/']
        # temp = 0
        # def check(a, b, oper):
        #     if oper == '+':
        #         return a + b
        #     elif oper == '-':
        #         return a - b
        #     elif oper == '*':
        #         return a * b
        #     elif oper == '/':
        #         return math.trunc(a / b)
        # # print(math.trunc(6/-132))
        # # print(rpn)
        # i = 0
        # while i < len(rpn):
        #     if len(rpn) == 1:
        #         return int(rpn[0])
        #     if rpn[i] in op:
        #         temp = check(int(rpn[i-2]), int(rpn[i-1]), rpn[i])
        #         print(temp)
        #         del rpn[i], rpn[i-1]
        #         rpn[i-2] = str(temp)
        #         i = -1
        #     i+=1

        # stack 이용
        stack = []
        for token in tokens:
            if token not in '+-*/':
                stack.append(int(token))
            else:
                num1, num2 = stack.pop(), stack.pop()
                if token == "+":
                    stack.append(num2+num1)
                elif token == "-":
                    stack.append(num2-num1)
                elif token == "*":
                    stack.append(num2*num1)
                else:
                    stack.append(math.trunc(num2 / num1))
        return stack.pop()
```

## <span style="color:#58ACFA">마무리</span>

이문제에서 가장 중요한 점은 바로 후위순회표기된 식을 중위순회표기식으로 바꾸어 생각하는 법과 스택을 이용하는 것을 눈치 채는 것이다.

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
