---
title: "Github Blog : Type"
excerpt: "모든 언어의 시작은 타입 확인입니다."
categories:
  - Github Blog
---

<br>

<br>

# Type of Liquid Template Language 

Github Blog 테마의 Jekyll minimal mistakes를 사용하기로 결정을 하고 Liquid Template Language를 학습하기 위해 <a href="https://shopify.github.io/liquid/">liguid 가이드 홈페이지</a> 기반으로 학습을 진행하였습니다.

<br>

## String

```
{% raw %}{% assign my_string = "Hello World!" %}{% endraw %}
```

<br>

## Number ( int & float )

```
{% raw %}{% assignn my_int = 25 %}
{% assign my_float = -39.756 %}{% endraw %}
```

<br>

## Boolean

```
{% raw %}{% assign foo = true %}
{% assign bar = false %}{% endraw %}
```

<br>

## Nil

Liquid 언어에서 empty value이다.

```
{% raw %}{% if user %}
	Hello {{ user.name }}!
{% endif }{% endraw %}
```

<br>

## Array

```
{% raw %}<!-- if site.users = "Tobi", "Laura", "Tetsuro", "Adam" -->
{% for user in site.users %}
	{{ user }}
{% endfor %}
<!-- Tobi Laura Tetsuro Adam --!>{% endraw %}
```

```
{% raw %}<!-- if site.users = "Tobi", "Laura", "Tetsuro", "Adam" -->
{{ site.users[0] }}
{{ site.users[1] }}
{{ site.users[-1] }}
<!-- Tobi --!>
<!-- Laura --!>
<!-- Adam --!>{% endraw %}
```

<br>

## EmptyDrop

삭제된 객체에 접근하면 EmptyDrop이 됩니다.

You can check to see if an object exists or not before you access any of its attributes.

```
{% raw %}{% assign variable = "hello" %}
{% assign page_1 = pages[variable] %}
{% assign page_2 = pages["does-not-exist"] %}
{% assign page_3 = pages.this-handle-does-not-exist %}

{% unless pages == empty %}
  <h1>{{ pages.frontpage.title }}</h1>
  <div>{{ pages.frontpage.content }}</div>
{% endunless %}{% endraw %}
```

<br>

<br>
