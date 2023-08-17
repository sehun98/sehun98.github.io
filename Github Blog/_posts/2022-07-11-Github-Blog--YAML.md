---
title: "Github Blog : YAML"
excerpt: "Github Blog를 사용하면서 커스터마이징을 위해 간단하게 알아봅니다."
categories:
  - Github Blog
---

<br>

<br>

# Getting started Liquid Template Language

Github Blog 테마의 Jekyll minimal mistakes를 사용하기로 결정을 하고 Liquid Template Language를 학습하기 위해 <a href="https://shopify.github.io/liquid/">liguid 가이드 홈페이지</a> 기반으로 학습을 진행하였습니다.

<br>

## YAML

YAML (YAML Ain't Markup Language) 으로 재귀 약어로 생각하면 될 것 입니다.

YAML을 사용하면 다음 수식을 변경해서 사용할 수 있습니다.\

< 변경 전 navigation.html>

```\
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

<naviagion.yaml>

```
- name: Home
  link: /
- name: About
  link: /about.html
```

< 변경 후 navigation.html>

```
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>
```



<br>

<br>
