---
title: "Github Blog : Start"
excerpt: "Github Blog를 사용하면서 커스터마이징을 위해 간단하게 알아봅니다."
categories:
  - Github Blog
---

<br>

<br>

# Getting started Liquid Template Language

Github Blog 테마의 Jekyll minimal mistakes를 사용하기로 결정을 하고 Liquid Template Language를 학습하기 위해 <a href="https://shopify.github.io/liquid/">liguid 가이드 홈페이지</a> 기반으로 학습을 진행하였습니다.

<br>

## Operator

In tags with more than one `and` or `or` operator, operators are checked in order *from right to left*. 

| Operator | description              |
| -------- | ------------------------ |
| `==`     | equals                   |
| `!=`     | does not equal           |
| `>`      | greater than             |
| `<`      | less than                |
| `>=`     | greater than or equal to |
| `<=`     | less than or equal to    |
| `or`     | logical or               |
| `and`    | logical and              |

```
{% raw %}{% if true and false and false or true %}
  This evaluates to false, since the tags are checked like this:

  true and (false and (false or true))
  true and (false and true)
  true and false
  false
{% endif %}{% endraw %}
```

<br>

## Contain

**Contains** checks for the presence of a substring inside a string.

```
{% raw %}{% if product.title contains "Pack" %}
  This product's title contains the word Pack.
{% endif %}{% endraw %}
```

<br>

## Truthy and falsy

All values in Liquid are truthy except `nil` and `false`.

<br>

## if

```
{% raw %}<!-- If customer.name = "anonymous" -->
{% if customer.name == "kevin" %}
  Hey Kevin!
{% elsif customer.name == "anonymous" %}
  Hey Anonymous!
{% else %}
  Hi Stranger!
{% endif %}{% endraw %}
```

<br>

## unless

This would be the equivalent of doing the following

```
{% raw %}{% unless product.title == "Awesome Shoes" %}
	These shoes are awesome!
{% endunless %}
<!-- equivalent -->
{% if product.title != "Awssome Shoes" %}
	These shoes are awesome!
{% endif %}{% endraw %}
```

<br>

## case/when

```
{% raw %}{% assign handle = "cake" %}
{% case handle %}
  {% when "cake" %}
     This is a cake
  {% when "cookie", "biscuit" %}
     This is a cookie
  {% else %}
     This is not a cake nor a cookie
{% endcase %}{% endraw %}
```

<br>

## for

```
{% raw %}{% for i in (1..5) %}
  {% if i == 4 %}
    {% break %}
  {% else %}
    {{ i }}
  {% endif %}
{% endfor %}{% endraw %}
```

<br>

## continue

```
{% raw %}{% for i in (1..5) %}
  {% if i == 4 %}
    {% continue %}
  {% else %}
    {{ i }}
  {% endif %}
{% endfor %}{% endraw %}
```

<br>

## limit

```
{% raw %}<!-- if array = [1,2,3,4,5,6] -->
{% for item in array limit:2 %}
  {{ item }}
{% endfor %}
<!-- output : 1 2 -->{% endraw %}
```

<br>

## offset

```
{% raw %}<!-- if array = [1,2,3,4,5,6] -->
{% for item in array offset:2 %}
  {{ item }}
{% endfor %}
<!-- output : 3 4 5 6 -->{% endraw %}
```

<br>

## range

```
{% raw %}{% for i in (3..5) %}
  {{ i }}
{% endfor %}

{% assign num = 4 %}
{% assign range = (1..num) %}
{% for i in range %}
  {{ i }}
{% endfor %}{% endraw %}
```

<br>

## reversed

```
{% raw %}<!-- if array = [1,2,3,4,5,6] -->
{% for item in array reversed %}
  {{ item }}
{% endfor %}{% endraw %}
```

<br>

## cycle (group)

```
{% raw %}{% cycle "first": "one", "two", "three" %}
{% cycle "first": "one", "two", "three" %}
{% cycle "second": "one", "two", "three" %}
{% cycle "second": "one", "two", "three" %}
<!-- output : one two one two -->{% endraw %}
```

<br>

## tablerow

```
{% raw %}<table>
{% tablerow product in collection.products %}
  {{ product.title }}
{% endtablerow %}
</table>{% endraw %}
```

<br>

<br>
