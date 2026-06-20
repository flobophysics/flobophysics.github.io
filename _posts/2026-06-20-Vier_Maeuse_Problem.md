---
   layout: post
   title: "Das Vier-Mäuse-Problem"
   excerpt: "Vier Mäuse sitzen in den vier Ecken eines quadratischen Käfigs. 
Sie beginnen gleichzeitig loszurennen, und steuern dabei immer auf die im Gegenuhrzeigersinn vor ihnen rennende Maus zu. – Ein berühmtes Problem das schnell zu Differentialgleichungen und komplexen mathematischen Lösungsansätzen führt."
   tags: [deutsch, maths]
   category: blog
---

<!-- Lade MathJax um Formeln darzustellen -->
<script>
MathJax = {
  tex: {inlineMath: {'[+]': [['$', '$']]}}
};
</script>
<script defer src="https://cdn.jsdelivr.net/npm/mathjax@4/tex-chtml.js"></script>


## Das Problem

Vier Mäuse sitzen in den vier Ecken eines quadratischen Käfigs. 
Sie beginnen gleichzeitig loszurennen, und steuern dabei immer auf die im Gegenuhrzeigersinn vor ihnen rennende Maus zu. Alle Mäuse rennen gleich schnell.

Man beschreibe die Kurve(n), auf der die Mäuse im Käfig rennen, und berechne ggfs. ihre Länge.




## Hilfestellung

Wir nehmen an, der Käfig habe Seitenlänge $2$, und die Startposition der ersten Maus sei $\binom{1}{1}$. 
Die Wege der Mäuse seien 

$$
\gamma_j(t) = \binom{x_j(t)}{y_j(t)},\quad 
j=1,2,3,4
$$

und $t$ die Zeit ab dem Start $t=0$.

Aufgrund der Symmetrie findet man den Ort der voraus rennenden Maus durch Drehung um $\frac{\pi}{2}$, ausgeschrieben:

$$\gamma_{j+1}(t)=
\binom{x_{j+1}(t)}{y_{j+1}(t)}=
\begin{pmatrix}
\cos\!\left(\frac{\pi}{2}\right) & -\sin\!\left(\frac{\pi}{2}\right) \\
\sin\!\left(\frac{\pi}{2}\right) & \cos\!\left(\frac{\pi}{2}\right)
\end{pmatrix}
\binom{x_{j}(t)}{y_{j}(t)}
$$

Die Geschwindigkeiten der Mäuse sind durch die Ableitungen gegeben:
$$\dot{\gamma}_{j}(t) = \frac{d}{dt}\gamma_{j}(t)$$
Nach Voraussetzung zeigen diese immer in Richtung der jeweils voraus rennenden Maus:

$$\dot{\gamma}_j(t)=\gamma_{j+1}(t)-\gamma_j(t)$$

Die folgende Anleitung soll bei der Lösung hilfreich sein:

1\. Man bestimme die Differentialgleichung des Problems und entkopple sie, sodass nur noch die Position $\gamma(t)=\binom{x(t)}{y(t)}$ einer einzigen Maus auftritt (vorzugsweise der ersten Maus):
   
   $\dot{\gamma}(t)=A\gamma(t)$.

2\. Man führe eine Basistransformation $S$ durch, sodass die Matrix $A$ diagonalisiert wird, also 
$
\gamma'(t)=S\gamma(t)
$

$$
\Rightarrow\quad
\dot{\gamma}'(t)
=
SA\gamma(t)
=
SAS^{-1}S\gamma(t)
=
D_A\gamma'(t)
$$

3\. Die Differentialgleichungen der transformierten Koordinaten $x'(t)$ und $y'(t)$ entkoppeln und können einzeln gelöst werden:

$$
\dot{\gamma}'(t)
=
\binom{\dot{x}'(t)}{\dot{y}'(t)}
=
D\gamma'(t)
=
\begin{pmatrix}
\lambda_1 & 0 \\
0 & \lambda_2
\end{pmatrix}
\binom{x'(t)}{y'(t)}
$$

4\. Die Lösung $\gamma'(t)$ wird wieder in die Standardbasis zurück transformiert, um den Weg $\gamma(t)$ zu erhalten:

$$
\gamma(t)
=
S^{-1}\gamma'(t)
=
S^{-1}
\binom{x'(t)}{y'(t)}
$$

5\. Die Länge der Kurve wird mithilfe des Integrals über die Geschwindigkeit eines Weges $\gamma(t)=\binom{x(t)}{y(t)}$ berechnet:

$$
L(\gamma)
=
\int \sqrt{\dot{x}^2(t)+\dot{y}^2(t)}\,dt
$$

----

## Die Lösung des Vier-Mäuse-Problems

Eine Lösung der Aufgabe ist
[hier (PDF)]({{ GITHUB_REPOSITORY }}/assets/PDFs/26i06f2055fu5w.pdf) hochgeladen. 