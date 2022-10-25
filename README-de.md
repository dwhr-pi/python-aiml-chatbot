## Python AIML-Chatbot


Vor einer Weile schrieb ich ein kurzes tutorial über das erstellen eines AIML chatbot und seine text-Ausgabe

via espeak (https://iniy.org/?p=68).


Nach Jahren stolperte ich über diesen Beitrag wieder und jetzt ist hier der zweite Teil, die Lasten der AI-Stiftung ist A. L. I. C. E.

AIML aus http://www.alicebot.org/aiml.html .


Um ehrlich zu sein war ich ein wenig überrascht darüber, wie wenig schwierig zu finden und Dokumentation gibt es auf der

net man diese einfache aiml-Dateien ausführen. Es ist ein bisschen schwer zu finden, google code Seite:

https://code.google.com/archive/p/aiml-en-us-foundation-alice/


Aber die AIML ist optimiert für die Pandorabots online-plattform, und ich wollte nur zu spielen, um

ein wenig mit diesem Zeug lokal.


Also hier ist ein repository mit Batterien im Lieferumfang enthalten:


- Basiert auf aiml-de-de-foundation-alice-1.9 zip-Datei von der AI Foundation-google code

- entfernt Pandorabots bestimmte syntax

- Hinzugefügt std-startup.aiml mit den (meiner Meinung) richtig laden -, um die aiml-Dateien

- minimale version einer python chatbot


## Setup


Clone git


```

git clone https://github.com/dwhr-pi/python-aiml-chatbot.git

```


Erfordert Python ist3 (aber die Portierung dieser minimal-Skript zu python 2 ist sehr einfach)


```

pip3 install python-aiml

```

Dann einfach im terminal ausführen, um zu ändern Sie für den Ordner der python-aiml-chatbot:


```

cd python-aiml-chatbot

```


Und chatbot mit start im Terminal:

```

./chatbot.py

```

# # , Wohin Sie gehen von hier aus


Dieser minimal-Skript nicht implementieren einen Präprozessor und aufgrund der Entfernung von einigen pandorabots

Besondere syntax, die es geben könnte einige merkwürdige Antworten, aber es ist ein Ausgangspunkt.


Fügen Sie Ihre eigenen AIML-Dateien auf der Unterseite des std-startup.aiml (so haben Sie höchste Priorität)

und spielen, um die Herstellung der bot schlauer.


Einschließlich der espeak-Ausgabe von meinem anderen blog-post auch Spaß machen könnte, (https://iniy.org/?p=68).


## Allgemeine Dokumentation (von der AI Foundation, google code)


Da hatte ich eine harte Zeit der Suche nach dem laden, um die Informationen, die ich auch diese hier im repo.



### Über die A. L. I. C. E. AIML-Dateien


Die aiml-de-de-foundation-alice-Dateien enthalten eine Reihe von Kategorien mit doppelten Muster. Je nach AIML-interpreter verwendet, die Duplikate sind unterschiedlich gehandhabt.


Auf Pandorabots die Regel ist: Die Dateien sind geladen, um von der Spitze der Liste (unter dem "AIML-Dateien" Abschnitt) auf der Unterseite. Wenn eine Kategorie ist geladen, die das gleiche Muster Pfad (d.h. gleicher input Muster, Muster und Thema-Muster-Sie erinnern sich, dass <das> und <Thema> eingestellt sind implizit), dann Pandorabots verwirft die frühere Kategorie und wählt die Antwort Vorlage aus dem zuletzt geladenen Kategorie.


Um ein Beispiel zu geben: Angenommen, eine Datei A. aiml hat eine category <category> <pattern>TEST</pattern> <template>Das ist die Reaktion von Datei-A.</template> </category> und eine Datei B. aiml hat eine category <category> <pattern>TEST</pattern> <template>Das ist die Antwort von Datei B.</template> </category>


Vorausgesetzt, die Dateien sind geladen in alphabetischer Reihenfolge, die A. aiml geladen, bevor der B. aiml, dann ist die Antwort an den Eingang "Test" sollte "Dies ist die Antwort von Datei B."

A. L. I. C. E. AIML Datei-Bestellung


Die A. L. I. C. E. AIML-Dateien in aiml-de-de-foundation-alice geladen werden soll, in der folgenden Reihenfolge:


- Laden Sie zunächst die Sichere Reduktion Dateien reducation0.sicher.aiml,...,reduction4.sicher.aiml und Ermäßigungen.update.aiml.

- Zweite, laden Sie die Mindpixel mp0-Dateien.aiml,...,mp6.aiml.

- Laden Sie dann alle verbleibenden AIML-Dateien.

- Pandorabots wird immer laden Sie die Datei update.aiml als die Letzte Datei.


### AIML nutzt einem preprocessing-Schritt Normalisierung genannt.


Diese AIML set ist entwickelt, um mit dem Standard-AIML Präprozessor-geliefert mit Pandorabots.com.


Der Präprozessor


Korrigiert einige Rechtschreibfehler und Redensarten (z.B. "wanna" --> "wollen")

Ersatz Wörter für gemeinsame emoticons (z.B. ":-)" --> "LÄCHELN")

Erweitert Kontraktionen (z.B. "nicht" --> "nicht")

Entfernt intra-Satz Satzzeichen (z.B. "Dr. Wallace lebt auf St. John St. --> "Dr Wallace lebt in der St. John St.")


Wir verweisen auf die obige substitution Schritte als Normalisierung.


Der Letzte Schritt der Vorverarbeitung


Teilt Sätze basierend auf vordefinierten Zeichen ".", "!", ";" und "?"


Alle diese preprocessing-Schritte werden in der Konfigurationsdatei definiert. Neben der Konfigurationsdatei


Definiert Substitutionen für <gender>, <person> und <person2 ->


Der Präprozessor normalisiert die Eingänge der bot durch das laufen durch eine Reihe von Substitutionen, dann teilt sich den Eingang in Sätzen und speist diese in den bot.