## Python AIML-Chatbot


Vor einer Weile schrieb ich ein kurzes Tutorial über das Erstellen eines AIML Chatbot und seine text-Ausgabe

via espeak (https://iniy.org/?p=68).


Nach Jahren stolperte ich über diesen Beitrag wieder und jetzt ist hier der zweite Teil, die Lasten der AI-Stiftung ist A. L. I. C. E.

AIML aus http://www.alicebot.org/aiml.html .


Um ehrlich zu sein, war ich ein wenig darüber überrascht, wie leicht diese zu finden sind und Dokumentation gibt es auf der

net, man diese einfachen aiml-Dateien ausführen. Es ist ein bisschen schwer zu finden, auf der Google Code-Seite:

https://code.google.com/archive/p/aiml-en-us-foundation-alice/


Aber diese AIMLs sind für die Pandorabots online-plattform optimiert, und ich wollte nur etwas spielen, um 

ein wenig mit diesem Zeug lokal vertraut zu sein.


Also hier ist ein Repository mit aiiml-Dateien im Lieferumfang mit enthalten:


- Basiert auf aiml-de-de-foundation-alice-1.9 zip-Datei von der AI Foundation-google code

- entfernte Pandorabots bestimmte Syntax

- Hinzugefügt std-startup.aiml mit den (meiner Meinung) richtigen laden der aiml-Dateien. 

- minimale Version eines Python Chatbot's. 


## Setup


Klonenen des git 


```

git clone https://github.com/dwhr-pi/python-aiml-chatbot.git

```


Erfordert Python3 ist (aber die Portierung des minimal-Skript zu python2 ist sehr einfach)


```

pip3 install python-aiml

```

Dann einfach im Terminal nachfolgend ausführen, um den Pfad zu dem Ordner der python-aiml-chatbot zu ändern:


```

cd python-aiml-chatbot

```


Und den Chatbot im Terminal starten mit:

```

./chatbot.py

```

## Wohin Sie von hier aus gehen.


Dieses minimal-Skript, nicht implementiert ist ein Präprozessor und aufgrund der Entfernung des Codes von einigen Pandorabots. 

Besondere Syntax, die es geben könnte einige merkwürdige Antworten, aber es ist ein Ausgangspunkt.


Fügen Sie Ihre eigenen AIML-Dateien auf der Unterseite der std-startup.aiml-Datei (so haben Sie höchste Priorität) mit ein. 

Und experimentieren damit, um die Herstellung des Bots etwas schlauer zu gestalten. 


Einschließlich der espeak-Ausgabe von meinem anderen blog-post, der auch Spaß machen könnte, (https://iniy.org/?p=68).


## Allgemeine Dokumentation (von der AI Foundation, google code)


Da hatte ich eine harte Zeit auf der Suche und nach dem laden, um die Informationen, die ich auch diese hier im repo veröffendliche. 



### Über die A. L. I. C. E. AIML-Dateien


Die aaiml-en-us-foundation-alice enthalten eine Reihe von Kategorien mit doppelten Muster. Je nach AIML-interpreter verwendet, die Duplikate sind unterschiedlich gehand habt. 


Auf Pandorabots ist die Regel: Die Dateien sind geladen, um von der Spitze der Liste (unter dem "AIML-Dateien" Abschnitt) auf der Unterseite. Wenn eine Kategorie ist geladen, die das gleiche Muster Pfad (d.h. gleicher input Muster, Muster und Thema-Muster-Sie erinnern sich, dass <that> und <topic> eingestellt sind implizit), dann Pandorabots verwirft die frühere Kategorie und wählt die Antwort Vorlage aus dem zuletzt geladenen Kategorie.


Um ein Beispiel zu geben: Angenommen, eine Datei A. aiml hat eine category <category> <pattern>TEST</pattern> <template>Das ist die Antwort von Datei-A.</template> </category> und eine Datei B. aiml hat eine category <category> <pattern>TEST</pattern> <template>Das ist die Antwort von Datei B.</template> </category>


Vorausgesetzt, die Dateien sind geladen in alphabetischer Reihenfolge, die A.aiml geladen, bevor die B.aiml, dann ist die Antwort an den Eingang "Test" sollte "Dies ist die Antwort von Datei B."

A. L. I. C. E. AIML Datei-Bestellung


Die A. L. I. C. E. AIML-Dateien in aiml-de-de-foundation-alice geladen werden soll, in der folgenden Reihenfolge:


- Laden Sie zunächst die Sichere Reduktion Dateien reducation0.sicher.aiml,...,reduction4.sicher.aiml und Ermäßigungen.update.aiml.

- Zweitens, laden Sie die Mindpixel mp0-Dateien.aiml,...,mp6.aiml.

- Laden Sie dann alle verbleibenden AIML-Dateien.

- Pandorabots wird immer die Datei update.aiml als die Letzte Datei laden.


### AIML nutzt einem preprocessing-Schritt Normalisierung genannt.


Dieses AIML-Set ist entwickelt, um mit dem Standard-AIML Präprozessor-geliefert mit Pandorabots.com.


Der Präprozessor


Korrigiert einige Rechtschreibfehler und Redensarten (z.B. "wanna" --> "wollen")

Ersatz Wörter für gemeinsame emoticons (z.B. ":-)" --> "LÄCHELN")

Erweitert Kontraktionen (z.B. "nicht" --> "nicht")

Entfernt intra-Satz Satzzeichen (z.B. "Dr. Wallace lebt auf St. John St. --> "Dr Wallace lebt in der St. John St.")


Wir verweisen auf die obige substitutions Schritte als Normalisierung.


Der Letzte Schritt der Vorverarbeitung


Teilt Sätze basierend auf vordefinierten Zeichen ".", "!", ";" und "?"


Alle diese preprocessing-Schritte werden in der Konfigurationsdatei definiert. Neben der Konfigurationsdatei


Definiert Substitutionen für <gender>, <person> und <person2->


Der Präprozessor normalisiert die Eingänge des Bots durch das laufen und durch eine Reihe von Substitutionen, dann teilt er sich den Eingang in den Sätzen und speist diese in den Bot.