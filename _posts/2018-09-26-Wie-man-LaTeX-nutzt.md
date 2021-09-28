---
layout: post
title:  Wie man LaTeX nutzt
date:   2018-09-26 09:00:00
description: Installation, Texte schreiben
#comments: true
---

## Wie man LaTeX installiert

Wie bekommt man nun LaTeX auf den eigenen Rechner und wie sehen die ersten Schritte aus? Wie ich bereits in meinem Beitrag zuvor erwähnt habe, ist LaTeX frei verfügbar und plattformunabhängig. Konkret bedeutet dass, dass durch den Download und die Nutzung dieses Programms keine Kosten für die Nutzer entstehen und das Programm sowohl auf MS Windows, Mac OSX und auf den unterschiedlichsten Linux Distributionen läuft.

Um das Programm nun als herunterzuladen, empfehle ich die Website [The LaTeX Project](https://www.latex-project.org/get/#tex-distributions){:target="\_blank"}. Hier finden sich neben zahlreichen Informationen zu LaTeX und den neusten Entwicklungen, auch der Verweis auf die einzelnen LaTeX-Distributionen für die unterschiedlichsten Betriebssysteme.

![](/assets/img/posts/2018_latex-project-1.jpeg)

<div class="caption">
Das LaTeX-Project – Informationen über LaTeX und Ausgangspunkt zum Downloaden der unterschiedlichen Distributionen
</div>

Wer so wie ich mit Mac OSX arbeitet, muss daher [MacTeX](http://www.tug.org/mactex/){:target="\_blank"} herunterladen und installieren. Das MacTeX-Paket ist rund drei Gigabyte. Es empfiehlt sich daher eine schnelle Verbindung zu nutzen. Nachdem Download muss man das Paket nur noch installieren und kann anschließend gleich mit dem Schreiben beginnen.

Ich empfehle zum Schreiben in LaTeX aber das Programm [TeXstudio](https://www.texstudio.org/){:target="\_blank"} zu verwenden. Dieser Editor ist weitaus komfortabler und bietet viele nützliche Assistenten, die einem dabei helfen, den Fokus vollkommen auf das Schreiben und nicht auf das Programmieren zu legen.

Wichtig zu beachten, ist hier allerdings die Reihenfolge der Installation beider Programme. Man muss erst die LaTeX-Distribution (im Falle von Mac OSX eben MacTeX) installieren und darf erst dann TeXstudio auf den Rechner spielen. Ansonsten besteht die Gefahr, dass die Verlinkungen von TeXstudio zu der LaTeX-Distribution fehlerhaft sind.

Hat man TeXstudio schließlich erfolgreich installiert, sollte das folgende Fenster nach dem Öffnen zu sehen sein.

![](/assets/img/posts/2018_texstudio.jpeg)

<div class="caption">
TexStudio auf einem Mac
</div>

## Wie man in LaTeX Texte verfasst

Wie schreibt man nun aber Texte in LaTeX? Der grundlegende Unterschied zwischen LaTeX und allen herkömmlichen Textverarbeitungsprogrammen ist jener, dass man in LaTeX eigentlich nur eine reine Text-Datei (mit der Dateiendung .tex) verfasst. Was diese Datei zu einer herkömmlichen Textdatei (zB .txt) unterscheidet, sind die Befehle, die diese Textdatei ergänzen. Erst durch das Konvertieren (einfacher Druck per Knopf) entsteht aus dieser Textdatei mit Befehlen ein wunderschönes pdf-Dokument. Jedes Bild (und mag es noch so groß sein), das man in einem Text einbauen möchte, baut man daher nicht durch direktes Einfügen in die Textdatei ein, sondern über einen Befehl, der de facto eine Verlinkung darstellt.

Das bringt den Vorteil mit sich, dass egal wie lange und umfangreich ein Text ist, die Dateigröße dieser .tex-Datei selten bis nie über einen Megabyte groß ist. Man kann diese Datei daher schnell und einfach öffnen, bearbeiten und sichern.

Verfasst wird diese Datei im Hauptfeld von TeXstudio, das wie folgt ausschaut.

![](/assets/img/posts/2018_texstudio-main-1.jpeg)

<div class="caption">
Das Hauptfenster, indem das LaTeX-Dokument geschrieben wird. Hier sieht, wie in der Präambel zahlreiche Pakete geladen werden.
</div>

Auf den ersten Blick schreckt die Vielzahl dieser Befehle ab. Es handelt sich hierbei aber um einen Aufsatz für ein Journal, für den viele Formatierungsvorgaben zu berücksichtigen waren und in dem mein Ko-Autor und ich auch noch zahlreiche Grafiken, Tabellen und Schaubilder eingefügt haben.

Startet man TeXstudio neu, wird man dieses Hauptfeld zunächst aber leer vorfinden. Über die *Option Assistenten – Assistent für ein neues Dokument..*. kann man sich jedoch das Grundgerüst für einen neuen Beitrag automatisch erstellen lassen.

Bevor ich nun die einzelnen Elemente dieses Grundgerüsts erkläre, werde ich zuerst auf einige wichtige Grundlagen eingehen. Um in LaTeX effizient arbeiten zu können, muss man die Funktionsweise von Befehlen und Umgebungen verstehen. Befehle sind so etwas wie eine Aufforderung an LaTeX, etwas bestimmtes zu tun. Befehle beginnen dabei immer mit einem Backslash \, gefolgt von dem **Befehl** und dem `{Objekt}` in geschwungenen Klammern, auf das der Befehl anzuwenden ist. Will man zB ein Wort in LaTeX kursiv hervorheben, dann schaut der Befehl dazu so aus: `\emph{Wort}`.

In gewissen Fällen besteht allerdings auch die Möglichkeit, zwischen dem Befehl und dem auszuführenden Objekt eine oder mehrere `[Option/en]` einzubauen. Ich werde weiter unten ein Beispiel dazu zeigen.

Neben Befehlen spielen in LaTeX **Umgebungen** eine wichtige Rolle. Sie helfen, die eigentliche Formatierung vorübergehend zu deaktivieren und stattdessen eine andere Formatierung anzuwenden. Umgebungen erkennt man daran, dass Sie mit dem Befehl `\begin{xxx}` geöffnet und mit dem Befehl `\end{xxx}` wieder geschlossen werden. Das `xxx` steht hier stellvertretend für den Namen der betreffenden Umgebung. Wichtig dabei zu betonen ist, dass man hier auf eine der grundlegenden Regeln des Programmierens achten muss: **jede Umgebung die geöffnet wird, muss auch wieder ordentlich geschlossen werden**.

Hat man dieses Grundprinzip nun verstanden, versteht man auch das Grundgerüst, das TeXstudio für einen anlegt, besser. Dieses Grundgerüst schaut wie folgt aus und besteht aus zwei Teilen:

```
\documentclass[10pt,a4paper]{article}

\usepackage[latin1]{inputenc}

% Pakete für mathematische Formeln und Sonderzeichen
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{amssymb}

% Paket zum Darstellen von Grafiken
\usepackage{graphicx}

%Paket für Aufzählungen
\usepackage{enumerate}

\begin{document}
	
	
\end{document}
```

1. **Body**: Das ist jener Teil (eigentlich eine Umgebung), der mit dem Befehl `\begin{document}` beginnt und mit `\end{document}` geschlossen wird. Hier schreibt man den eigentlichen Text, der dann auch im PDF sichtbar sein soll.

2. **Präambel**: In der Präambel werden die Grundlegenden Charakteristika des Dokuments festgelegt und alle Pakete geladen, die im Body gebraucht werden.

In der Präambel findet sich gleich zu Beginn der Befehl `\documentclass[10pt,a4paper]{article}`. Dieser Befehl (`\documentclass`) legt legt das Format des Dokuments fest (`{article}`, alternativ wäre auch noch die Möglichkeit `{book}`, `{report}`, `{letter}` oder `{beamer}` vorhanden) und ergänzt dieses Format durch Optionen (`[10pt, a4paper]`). Damit wird die Formatierung für Artikel geladen und die Referenzgröße der Schrift auf die Größe 10 festgelegt. Das heißt, dass alle weiteren Schriftgrößen (Überschriften, Fußnoten, eingezogene Zitate etc.) immer im Verhältnis zu dieser Schriftgröße festgelegt werden. Die Papiergröße wird wiederum mit A4 festgelegt.

Nachdem das Format des Dokuments festgelegt wurde, werden die Pakete geladen. Dazu wird der Befehl `\usepackage` gefolgt vom jeweiligen `{Paket}` angewendet. Pakete sind nichts anderes als Erweiterungen (die in der Regel schon mit der Installation der LaTeX-Distribution auf dem jeweiligen Rechner landen). Diese Erweiterungen ermöglichen es, unterschiedlichste Sonderformatierungen bzw. Spezialaufgaben zu übernehmen.

So kann man mit dem Paket `enumerate` Aufzählungen vornehmen. Dazu muss man das Paket wie oben vorgezeigt zunächst in der Präambel laden

`\usepackage{enumerate}`

bevor man dann im Body, eine Umgebung öffnet und dort die Aufzählung vornimmt:

```
\begin{enumerate}
\item Erstes Element
\item Zweites Element
\item Drittes Element
\end{enumerate}
```

Pakete können jederzeit in der Präambel ergänzt werden und müssen daher nicht von Beginn an vollständig sein. Erst sobald man Befehle aus einem Paket verwendet, muss dieses Paket in der Präambel auch geladen werden. Mit der Zeit und der Erfahrung arbeitet man schlussendlich mit einer Standard-Präambel, die man einfach in jedes neue Dokument kopiert. Auch wenn man nicht alle Pakete braucht, stört es nicht, wenn man sie in der Präambel geladen hat.

Ich will hier nicht auf alle möglichen Befehle und Tricks eingehen. Dazu verweise ich am Schluss dieses Beitrages auf eine wirklich hervorragende Einführung, die zudem noch gratis als PDF verfügbar ist. Ich möchte nur noch kurz die beiden anderen Fenster in TeXstudio vorstellen, die dem Nutzer zur Verfügung stehen. Ganz links findet sich das Seitenpanel.

![](/assets/img/posts/2018_texstudio-panel-2.jpeg)

<div class="caption">
Im Seitenpanel finden sich neben der Struktur des Textes und den Lesezeichen noch zahlreiche andere Funktionen und häufig genutzte Befehle.
</div>

In diesem Seitenpanel finden sich neben der Struktur des Dokuments (also allen Kapiteln und Unterkapiteln) und möglichen Lesezeichen die man sich angelegt hat (ich kann allen nur empfehlen mit Lesezeichen zu arbeiten!) noch zahlreiche weitere Funktionen und Kurzbefehle. Vor allem diese Kurzbefehle sind äußerst handlich. Will man Wörter fett oder kursiv schreiben, reicht es, wenn man sie markiert und wie in jedem anderen Textverarbeitungsprogramm mit einem Klick auf das entsprechende Icon (in diesem Fall **B** oder *em*) in die gewünschte Formatierung bringt.

Ganz unten im Programmfenster findet sich das Meldungs- bzw. Log-Fenster. In diesem Fenster zeigt LaTeX mögliche Fehler bei der Konvertierung der .tex Datei in ein PDF an. Solche Fehler können vorkommen, weil man sich zB bei einem Befehl verschrieben oder eine Umgebung zwar geöffnet, aber nicht wieder richtig geschlossen hat. In solchen Fällen verweist LaTeX in diesem Fenster auf einen Fehler. In den meisten Fällen wird auch die betreffende Zeile, in der der Fehler vorkommt, angezeigt und LaTeX macht einen Vorschlag, worin der Fehler bestehen könnte. Es empfiehlt sich daher, dieses Fenster nicht auszublenden, sondern spätestens bei der Konvertierung zu öffnen.

![](/assets/img/posts/2018_texstudio-log.jpeg)

<div class="caption">
Am unteren Ende des Fenster findet man die Meldungen, die beim Generieren von PDF Dateien ausgegeben werden. Zudem besteht hier die Möglichkeit, den Zeichensatz und die Sprache zu wechseln.
</div>

Das wären im Schnelldurchgang die ersten Schritte in LaTeX. Wer von dieser kurzen Einführung noch nicht abgeschreckt wurde, dem empfehle ich das folgende Buch:

Tobias Oetiker, Hubert Partl, Irene Hyna and Elisabeth Schlegl (2018), *The Not So Short Introduction to LATEX2ε*, [https://tobi.oetiker.ch/lshort/lshort.pdf](https://tobi.oetiker.ch/lshort/lshort.pdf){:target="\_blank"}.

Es ist eine hervorragend geschriebene und einfach zu verstehende Einführung. Am Ende der Lektüre wird LaTeX kein Mysterium mehr sein, sondern das Selbstverständlichste der Welt. Ich rate aber jedem Interessierten, sich einfach einmal hinzusetzen und das nächste Paper in LaTeX zu schreiben. Sobald man an einem konkreten Projekt arbeitet (parallel zum Lesen des eben erwähnten Buches), wird sich schnell der Lernerfolg einstellen und der Spass an LaTeX rasch wachsen.