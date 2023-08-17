---
title: "Github Blog : Object, Tag, Filter"
excerpt: "Github Blog를 사용하면서 커스터마이징을 위해 간단하게 알아봅니다."
categories:
  - Github Blog
---

<br>

<br>

# Getting started Liquid Template Language

Github Blog 테마의 Jekyll minimal mistakes를 사용하기로 결정을 하고 Liquid Template Language를 학습하기 위해 <a href="https://shopify.github.io/liquid/">liguid 가이드 홈페이지</a> 기반으로 학습을 진행하였습니다.

<br>

## Object

**Objects** contain the content that Liquid displays on a page.

```
{% raw %}{{ page.title }}{% endraw %}
```

<br>

## Tag

**Tags** create the logic and control flow for templates.

```
{% raw %}{% if product.title == "Shirt" or product.type == "Shoes" %}
	This is a shirt or a pair of shoes.
{% endif %}{% endraw %}
```

<br>

## Filter

**Filters** change the output of a Liquid object or variable.

```html
{% raw %}{{ "/my/fancy/url" | append: ".html" }} # /my/fancy/url.html
{{ "adam!" | capitalize | prepend: "Hello " }} # Hello Adam!{% endraw %}
```

`append`, `prepend`, `downcase`, `capitalize ` . . .

<br>

## Hyphen

strip whitespace from the left or right side of a rendered tag.

```
{% raw %}{{- assign my_variable = "tomato" -}}
{{ my_variable }}{% endraw %}
```

<br>

## assign

동적 할당

```
{% raw %}{{- assign my_variable = "tomato" -}}
{{ my_variable }}{% endraw %}
```

<br>

<br>
