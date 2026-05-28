---
     layout: post
     title: Ein Blog auf Github.io
     excerpt: "Einen Blog auf github.io zu bringen ist in der Tat so einfach wie überall beworben und geht innerhalb von Minuten. Wir zeigen hier die minimalste Version, für die man kein theme, keine fork und keinerlei Installation benötigt."
     tags: [deutsch, github]
---

Einen Blog auf github.io zu bringen ist in der Tat so einfach wie überall beworben und geht innerhalb von Minuten. Wir zeigen hier die *minimalste* Version, für die man kein *theme*, keine *fork* und keinerlei Installation benötigt.

Zunächst schaltet man die Webseite `username.github.io` online, dazu gibt es zahlreiche Anleitungen. Anschließend erstellt man drei Dateien und ist fertig. (Die drei Dateien entsprechen den von der offiziellen Dokumentation unter [jekyllrb.com](https://jekyllrb.com/docs/step-by-step/08-blogging/) – Schritt 8)

### Erstens: ein Blog-Beitrag

Im Verzeichnis `_posts` erstellt man eine Datei, deren Dateiname folgendes Format haben muss:

    JJJJ-MM-TT-es-folgt-der-restliche-Dateiname.md

Entscheidend ist Jahr, Monat und Tag vorne, je getrennt durch einen Bindestrich.

Die Datei selbst hat einen Kopf im yaml-Format und der Text folgt in Markdown. Als Beispiel zitieren wir diese Datei selbst:

    ---
       layout: post
       title: Ein Blog auf Github.io
    ---
    Einen Blog auf github.io zu bringen ist in der Tat so einfach wie überall beworben und geht innerhalb von Minuten. Wir zeigen hier die //minimalste// Version, für die man kein //theme//, keine //fork// und keinerlei Installation benötigt. 

    Zunächst schaltet man die Webseite ''username.github.io'' online, dazu gibt es zahlreiche Anleitungen. Anschließend erstellt man drei Dateien...

### Zweitens: Die Formatvorlage des Blogs

Das Format der Blog-Einträge wird von der Datei `_layouts/post.html` festgelegt. Man erstellt die Datei mit dem folgenden Inhalt:

<pre><code>{% raw %}---
layout: default
---
&lt;h1&gt;{{ page.title }}&lt;/h1&gt;
&lt;p&gt;{{ page.date | date_to_string }} - {{ page.author }}&lt;/p&gt;
{{ content }}
{% endraw %}</code></pre>

Der Blog-Eintrag von Schritt 1 wird nun bereits als Eintrag im Blog dargestellt, es fehlt nur noch der Link.

### Drittens: Links zu den Blog-Beiträgen

Damit Besucher der Webseite die Blog-Einträge sehen und anklicken können, listen wir sie unter `username.github.io/blog` auf. Dazu erstellen wir die Datei `blog.html` mit dem folgenden Inhalt:

<pre><code>{% raw %}---
layout: default
title: Blog
---
&lt;h1&gt;Neueste Beiträge&lt;/h1&gt;

&lt;ul&gt;
  {% for post in site.posts %}
    &lt;li&gt;
      &lt;h2&gt;&lt;a href="{{ post.url }}"&gt;{{ post.title }}&lt;/a&gt;&lt;/h2&gt;
      {{ post.excerpt }}
    &lt;/li&gt;
  {% endfor %}
&lt;/ul&gt;
{% endraw %}</code></pre>


Fertig!, der Blog ist nun verfügbar unter `username.github.io/blog`, z.B.
<https://flobophysics.github.io/blog>

Für weitere Einträge auf dem Blog werden nur die Markdown-Dateien unter `_posts` benötigt, der Rest geschieht automatisch.

