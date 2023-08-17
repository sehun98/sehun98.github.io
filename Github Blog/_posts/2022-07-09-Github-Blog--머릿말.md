---
title: "Github Blog : 머릿말"
excerpt: "Github Blog를 사용하면서 커스터마이징을 위해 간단하게 알아봅니다."
categories:
  - Github Blog
---

<br>

<br>

# Getting started Liquid Template Language

Github Blog 테마의 Jekyll minimal mistakes를 사용하기로 결정을 하고 Liquid Template Language를 학습하기 위해 <a href="https://shopify.github.io/liquid/">liguid 가이드 홈페이지</a> 기반으로 학습을 진행하였습니다.

<br>

## 머릿말

머릿말은 해당 페이지에 대한 변수를 설정하는데에 사용됩니다. 

```html
---
title: Home
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```

<br>

<br>
