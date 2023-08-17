---
title: "Github Blog : 레이아웃"
excerpt: "Github Blog를 사용하면서 커스터마이징을 위해 간단하게 알아봅니다."
categories:
  - Github Blog
---

<br>

<br>

# Getting started Liquid Template Language

Github Blog 테마의 Jekyll minimal mistakes를 사용하기로 결정을 하고 Liquid Template Language를 학습하기 위해 <a href="https://shopify.github.io/liquid/">liguid 가이드 홈페이지</a> 기반으로 학습을 진행하였습니다.

<br>

## _Layout

다음 폴더 `_Layout`에 레이아웃 `defult.html`을 생성합니다.

<br>

## 페이지 연결

```
<nav>  
	<a href="/" 
		{% if page.url == "/" %} 
			style="color: red;"
		{% endif %}>
		Home
	</a>  
	<a href="/about.html" 
		{% if page.url == "/about.html" %}
			style="color: red;"
		{% endif %}>
		About
	</a> 
</nav>
```

<br>

<br>
