---
     layout: post
     title: "Aufgaben TeXen mit ChatGPT"
     excerpt: "Stand 2026 können die Chat-Bots die Markup-Sprache LaTeX bereits sehr gut. Insbesondere produzieren sie verlässlich Code, der ohne Probleme das Kompilieren übersteht. Mit den folgenden Anweisungen arbeite ich seit einiger Zeit problemlos."
     tags: [deutsch, LaTeX, LLMs]
     category: blog
---

<!-- # Aufgaben TeXen mit ChatGPT -->

Stand 2026 können die Chat-Bots die Markup-Sprache LaTeX bereits sehr gut. Insbesondere produzieren sie verlässlich Code, der ohne Probleme das Kompilieren übersteht. Mit den folgenden Anweisungen arbeite ich seit einiger Zeit problemlos und -- was das Abschreiben von Text und Übertragen nach TeX betrifft -- sehr effizient. 

(Wenn man die Anweisungen verwenden wollte:
Die Quelldatei dieser Datei für die Eingabe bei ChatGPT 
[gibt es hier]({{ site.github.repository_url }}/blob/main/{{ page.path }}), mit weiteren Klicks auf "Code" und "raw".)

## Eingabe an ChatGPT

Hilf mir die folgende Aufgabe bzw. die Aufgabe in der Abbildung anbei in LaTeX-Code zu übertragen.

Wenn ich dich nach dem LaTeX-Code zu der Lösung dieser Aufgabe frage, dann halte dich bei den Hinweisen zur Lösung sehr knapp. Wenn ich nicht nach den Lösungen frage, dann gib keine Lösungen aus.

Ich gebe dir zunächst einige Hinweise zum LaTeX-Markup.
Ich verwende für die folgenden Hinweise das Markup von Markdown. Lies dir die folgenden Hinweise genau durch und halte dich daran.

Nach den Hinweisen folgt dann die eigentliche Aufgabe, die du in LaTeX-Code übertragen sollst.

## Hinweise zum LaTeX-Code

### exam documentclass

Verwende die documentclass `exam` und für die Teilaufgaben verwende nicht `\part`, sondern verwende stattdessen `\subpart`, z.B. so:

``` latex {% raw %}
    \begin{subparts}
      \subpart erste Teilaufgabe
      \subpart zweite Teilaufgabe
    \end{subparts}{% endraw %}
```

Ich gebe dir hier noch ein Beispiel für die Formatierung einer Frage im Stil der `exam`-Dokumentenklasse. Das Beispiel hat inhaltlich nichts mit dem zu tun, was du jetzt für mich machst:

``` latex {% raw %}
    \question
    Eine Münze wird sechsmal geworfen. Mit welcher Wahrscheinlichkeit fallen
    \begin{subparts}
    \subpart genau drei Wappen
    \subpart mindestens drei Wappen
    \subpart höchstens drei Wappen    
    \end{subparts}
    % end question
    \omitsolution{% endraw %}
```

Ich verwende `\omitsolution` um anzuzeigen, dass es noch keine getippte Lösung zu dieser Aufgabe gibt. Wenn du eine Lösung zu der Aufgabe ausgibst, dann soll sie in einer `solution`-Umgebung sein, also folgendes Format haben:

``` latex {% raw %}
    % \omitsolution
    \begin{solution}
    \begin{subparts}
      \subpart ...
    \end{subparts}
    \end{solution}{% endraw %}
```

Die Teilaufgaben (a), (b) usw. werden aus den `\subpart`-Befehlen erstellt.

Der Befehl `\omitsolution` entfällt bei der Ausgabe einer Lösung (im Beispiel oben ist es entsprechend auskommentiert).

### Das Paket siunitx

Verwende das Paket `siunitx` durch den Aufruf von:

``` latex {% raw %}
    \usepackage{siunitx}{% endraw %}
```

mit den folgenden Spracheinstellungen:

``` latex {% raw %}
    \sisetup{% siunitx-Spracheinstellung deutsch:
      per-mode        = fraction,
      locale          = DE,
      list-final-separator  = { und },
      list-pair-separator   = { und },
      list-separator    = {; },
      range-phrase      = { bis }
    }% Ende
    \DeclareSIUnit\curren{\text{\texteuro}}% Euro als Währung verwenden.{% endraw %}
```

Hier noch einige Beispiele zur Verwendung von `siunitx`:
Die Größe 3,5N steht für eine Kraft von 3,5 Newton, sie muss als `\qty{3.5}{\newton}` eingegeben werden.

Währungsbeträge wie z.B. 3,50€ setzt du ebenfalls mit `siunitx`, und zwar so:
`\SI{3.50}[\curren]{}`. Jeder Betrag in € soll so gesetzt werden, halte dich an diese Regel.

Auch Kommazahlen müssen mit `siunitx` eingegeben werden, das geht mit `\num{…}`. Zum Beispiel muss die Kommazahl 0,12 als `\num{0.12}` eingegeben werden. Die Schreibweise `0.12` soll nicht möglich sein, halte dich auch an diese Regel. (Der Grund dafür ist die Spracheinstellung: Auf deutsch müssen die Kommazahlen mit einem Komma `,` gesetzt werden und nicht mit einem Punkt `.`, der Befehl `\num{…}` setzt die Zahl richtig in Abhängigkeit von der Spracheinstellung.)

### Hinweise zum Setzen von Mathematik

Für das Setzen von Mathematik innerhalb der Zeile verwende nicht: `\( \)` sondern verwende stattdessen `$ $`. Füge zwischen `$` und dem Mathematik-Text kein Leerzeichen ein, sondern mache das wie in diesem Beispiel: `$4+3=7$` anstelle von `$ 4+3=7 $`.
Ein zweites Beispiel dafür wäre `$\frac{9}{10}$` anstelle von `$ \frac{9}{10} $`. Halte dich auch an diese Regel.

Für das Setzen von Mathematik in einer eigenen Zeile verwende nicht `\[ \]` oder `$$`, sondern verwende stattdessen:

``` latex {% raw %}
    \begin{equation*}
      ...
    \end{equation*}{% endraw %}
```

Das war wichtig, ich wiederhole es deshalb: Setze Mathematik-Zeilen nicht als `\[ \]` oder `$$`, sondern verwende stattdessen die `equation`-Umgebung. Die `equation`-Umgebung soll auch nicht von Leerzeilen von dem restlichen Text getrennt werden: Setze zwischen Text und `\begin{equation}` keine Leerzeile.

In der Regel will ich keine nummerierten Gleichungen, daher verwenden wir die Umgebung mit `*`, also `equation*`. Ich will, dass du dich an diese Vorgabe hältst.

### Die Vektorgeometrie mit LaTeX

Ich verwende eine eigene Notation für die Eingabe von (dreidimensionalen) Vektoren. Der Befehl `\vector` nimmt die Einträge entgegen und setzt sie in LaTeX übereinander. Beachte, dass das Argument mit runden Klammern eingegeben werden muss und dass die Einträge mit einem Komma getrennt sind.
Wenn ich z.B. eintippe `\vec{v} = \vector(1,2,3)`, dann ergibt sich das Resultat so (angenähert in ascii code):

         ( 1 )
    v =  ( 2 )
         ( 3 )

Dieser Abschnitt ist wichtig, daher sage ich dir das Fazit dieser Ausführung hier nochmals: Verwende den Befehl `\vector(…)` für Vektoren und trenne die Komponenten mit einem Komma. Beachte die runden Klammern für das Argument von `\vector`.

Entsprechendes gilt für die Angabe von Koordinaten mit dem Befehl `\coords(…)`. Zum Beispiel führt die Eingabe von `$A\coords(-5,5,0)$` zu dem Ergebnis `A(-5|5|0)`. Auch hier ist beim Argument eine runde Klammer zu verwenden.

## Die Struktur meines Dokumentes

All die beschriebenen Hinweise sind in der Preamble meines Dokumentes bereits untergebracht. Von dir will ich nur den LaTeX-Code der Aufgabe, den ich mit einem `input` statement in mein Dokument laden kann. Die Struktur meines Dokumentes ist also wie folgt:

``` latex {% raw %}
    \documentclass{exam}
    % Preamble mit den Paketen und Definitionen 
    \begin{document}
    \input{aufgabe.tex}
    \end{document}{% endraw %}
```

Du sollst also nur den LaTeX-Code erzeugen, den ich in der Datei `aufgabe.tex` abspeichere.

## Die eigentliche Aufgabe

Gib mir die Aufgabe anbei im LaTeX-Code aus.
Erstelle auch die Lösung der Aufgabe und gib sie in demselben Format aus; halte dich bei der Lösung sehr knapp.

ODER 

Übertrage den Aufgabentext in der Abbildung ins Englische. Es ist also eine Übersetzung gewünscht. Übertrage die Aufgabe dabei auch in LaTeX-Code.

<!-- EINGABE ERFOLGT HIER -->
