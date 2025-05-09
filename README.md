---
title: 笔记首页
layout: default # 明确使用主题的默认布局
---

# 我的黑客笔记空间

欢迎！这里的目录是自动更新的。

<!-- 这是自动目录代码开始的地方 -->
{% raw %}
## 自动生成的笔记目录

<ul>
  {% assign excluded_files = "README.md,index.md,404.html" | split: "," %}
  {% assign excluded_paths_prefixes = "_layouts,_includes,assets,.github" | split: "," %}

  {% assign all_notes = site.pages | sort: "path" %}

  {% for note in all_notes %}
    {% if note.ext == ".md" %}
      {% unless excluded_files contains note.name %}
        {% assign path_excluded = false %}
        {% for prefix in excluded_paths_prefixes %}
          {% if note.path contains prefix %}
            {% assign path_excluded = true %}
            {% break %}
          {% endif %}
        {% endfor %}
        
        {% unless path_excluded or note.url == "/" %}
          <li>
            <a href="{{ note.url | relative_url }}">
              {% if note.title %}
                {{ note.title }}
              {% else %}
                {{ note.name | remove_first: "_" | remove: ".md" | replace: "-", " " | capitalize }} <span style="font-size:0.8em; color:#888;">({{ note.path }})</span>
              {% endif %}
            </a>
          </li>
        {% endunless %}
      {% endunless %}
    {% endif %}
  {% endfor %}
</ul>
{% endraw %}
<!-- 这是自动目录代码结束的地方 -->

---
在这里可以写其他您想在首页显示的内容。
