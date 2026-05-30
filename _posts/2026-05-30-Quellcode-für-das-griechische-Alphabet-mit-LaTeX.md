---
   layout: post
   title: "Quellcode für das griechische Alphabet mit LaTeX"
   excerpt: "Das griechische Alphabet mit Schriftlinien zum Üben steht zum Herunterladen bereit. Veröffentlicht ist hier der Quellcode, wenn man etwas ändern möchte."
   tags: [LaTeX, Physik-Lehrmittel]
---

Das griechische Alphabet mit Schriftlinien zum Üben steht zum Herunterladen bereit ([PDF](https://flobophysics.github.io/physik-lehrmittel/PDFs/das-griechische-Alphabet.pdf)). Veröffentlicht wird hier der Quellcode, wenn man etwas ändern möchte.

``` latex {% raw %}
\makeatletter%
\newcommand{\greek@ii}[2]{%
\begin{pspicture}(-3,0)(3,1)%
    \psline(-3,1.5)(3,1.5)%
    \psline(-3,1)  (3,1.0)%
    \psline(-3,0)  (3,0.0)%
    \psline(-3,-.5)(3,-.5)%
    \rput[B](-1.5,0){\LARGE #1}
    \rput[B]( 1.5,0){\LARGE #2}
\end{pspicture}%
}%
\newcommand{\greek@i}[4]{%
#1 & #2, #3 & (#4) & \greek@ii{#2}{#3}%
}%
%
\begin{table}[htbp!]
%\vspace*{-1.8ex}
\centering
\renewcommand{\arraystretch}{1.8}
% Set the font size:
\LARGE% and then depending on that
% set the units accordingly:
\psset{linewidth=.04pt}%,linecolor=gray!50}%
\psset{xunit=1em,yunit=1ex}%
\normalsize%
\begin{tabular}{lllc}%
\toprule % -----------------------------
\multicolumn{4}{l}{\textbf{\large Das griechische Alphabet}}\\
%\midrule % ----------------------------
    Name    & griech.   
                & (latein.) & Schreibweise  \\
\midrule  % ----------------------------      
\greek@i{Alpha}{A}{$\alpha$}{a}             \\
\greek@i{Beta}{B}{$\beta$}{b}               \\
\greek@i{Gamma}{$\Gamma$}{$\gamma$}{g}      \\
\greek@i{Delta}{$\Delta$}{$\delta$}{d}      \\
\greek@i{Epsilon}{E}{$\epsilon$}{e}         \\
\greek@i{Zeta}{Z}{$\zeta$}{z}               \\
\greek@i{Eta}{H}{$\eta$}{ä}                 \\
\greek@i{Theta}{$\Theta$}{$\vartheta$}{th}  \\
\greek@i{Iota}{I}{$\iota$}{i}               \\
\greek@i{Kappa}{K}{$\kappa$}{k}             \\
\greek@i{Lambda}{$\Lambda$}{$\lambda$}{l}   \\
\greek@i{My}{M}{$\mu$}{m}                   \\
\greek@i{Ny}{N}{$\nu$}{n}                   \\
\greek@i{Xi}{$\Xi$}{$\xi$}{x}               \\
\greek@i{Omikron}{O}{$o$}{o}                \\
\greek@i{Pi}{$\Pi$}{$\pi$}{p}               \\
\greek@i{Rho}{P}{$\rho$}{r}                 \\
\greek@i{Sigma}{$\Sigma$}{$\sigma$}{s}      \\
\greek@i{Tau}{T}{$\tau$}{t}                 \\
\greek@i{Ypsilon}{Y}{$\upsilon$}{y, ü}      \\
\greek@i{Phi}{$\Phi$}{$\phi$}{ph}           \\
\greek@i{Chi}{X}{$\chi$}{ch}                \\
\greek@i{Psi}{$\Psi$}{$\psi$}{ps}           \\
\greek@i{Omega}{$\Omega$}{$\omega$}{o}      \\
\bottomrule % ----------------------------------------
\end{tabular}
\end{table}
{% endraw %}
```

‹Quellcode für das griechische Alphabet mit LaTeX› von [flobophysics](https://flobophysics.github.io), zur Verfügung gestellt unter der CC0-Lizenz. Eine Kopie der Lizenz ist hier verfügbar: [creativecommons.org](https://creativecommons.org/publicdomain/zero/1.0/)
