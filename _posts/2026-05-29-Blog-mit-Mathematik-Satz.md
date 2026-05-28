---
   layout: post
   title: "Blog-Beiträge mit Mathematiksatz durch MathJax"
   excerpt: "Hier testen wir die Anzeige von Mathematik-Satz im Blog mit MathJax. MathJax erlaubt die Eingabe im LaTeX-Format direkt im Quellcode."
   tags: [deutsch, github, maths]
---

<!-- Lade MathJax um Formeln darzustellen -->
<script>
MathJax = {
  tex: {inlineMath: {'[+]': [['$', '$']]}}
};
</script>
<script defer src="https://cdn.jsdelivr.net/npm/mathjax@4/tex-chtml.js"></script>

MathJax erlaubt die Eingabe von Mathematik-Satz im LaTeX-Format direkt im Quellcode und stellt alles automatisch dar. 

Ein Beispiel:
Die Funktion $f$ wird definiert durch $$f(x) = \sin(x)$$ und wird integriert,
sodass

$$
\int f(x)\,dx =0
$$



## MathJax laden

Um Mathjax zu laden wird der folgende Code-Block verwendet:
```
<script type="text/javascript" defer
  src="https://cdn.jsdelivr.net/npm/mathjax@4/tex-chtml.js">
</script>
```


### Nachtrag

Wir verwenden eine Variante des Code-Blocks, die Inline-Mathematik mit einzelnen `$` ermöglicht:

```
<script>
MathJax = {
  tex: {inlineMath: {'[+]': [['$', '$']]}}
};
</script>
<script defer src="https://cdn.jsdelivr.net/npm/mathjax@4/tex-chtml.js"></script>
```
Vergleiche dazu auch das Beispiel auf [mathjax.github.io](https://mathjax.github.io/MathJax-demos-web/page/tex-chtml.html)