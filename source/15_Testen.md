# Evaluierung der Implementierung

Die Implementierung der Identifizierungstechnologie im Fahrzeugkontext erweist sich als komplexer Prozess, bei dem verschiedene Aspekte zu berücksichtigen sind. Die Bewertung der Implementierung erfolgt anhand der Kriterien Funktionalität und Genauigkeit, Datensicherheit sowie Benutzerfreundlichkeit. Die Ergebnisse der Implementierung werden in einem Gesamtkontext betrachtet und im Anschluss diskutiert.

## Versuchsübersicht und Ergebnisse

Um die Funktionalität der Implementierung zu bewerten, werden verschiedene Versuche durchgeführt. Zunächst wird untersucht, wie das ML-Modell am besten trainiert werden kann, um eine hohe Genauigkeit zu erreichen, ohne den Insassen zu überfordern. Zusätzlich werden verschiedene Szenarien für die Aufnahme und Klassifizierung der Stimmdaten geprobt, um die Funktionalität des Systems unter verschiedenen Bedingungen zu testen. 

### Aufbau

Der Versuchsaufbau gliedert sich in zwei Abschnitte. Zuerst wurden Experimente zur Verbesserung des Erkennungsprozesses durchgeführt. Anschließend wurden Experimente zur Bestimmung der Trainingslänge sowie zum Testen der Funktionalität durchgeführt.

Das Modelltraining wurde für alle Experimente im Vorfeld durchgeführt. Dazu wurden sechs Modelle mit fünf Klassen bzw. Sprechern trainiert, wobei pro Sprecher verschiedene Audioaufnahmen verwendet wurden, die sich insgesamt auf mindestens 15 Minuten summierten. Diese Audioaufnahmen wurden in verschiedenen Längen für das Training verwendet, um eine optimale Audiolänge für das Training zu bestimmen. Insgesamt wurden sechs Audiolängen ausgewertet. Die Tabelle \ref{übersicht_modellergebnisse} veranschaulicht den Trainingsprozess, wobei die Audiolänge der Trainingsdaten $T_{train}$, der Loss (Verlust) für die Trainingsdaten $L_{train}$ und für die Validierungsdaten $L_{val}$, die Accuracy (Genauigkeit) für die Trainingsdaten $A_{train}$ und für die Validierungsdaten $A_{val}$ als auch die Anzahl der Epochen bis zur Konvergenz $E$ und die Zeit bis zur Konvergenz $T_{conv}$ aufgeführt sind. Alle Zeiten sind in Sekunden angegeben.

| $T_{train}$ | $L_{train}$ | $L_{val}$ | $A_{train}$ | $A_{val}$ | $E$ | $T_{conv}$ |
|-------------|-------------|-----------|-------------|-----------|-----|------------|
| $1$         | 0.1455      | 0.3337    | 0.9352      | 0.8750    | 26  | 32         |
| $3$         | 0.1344      | 0.2410    | 0.9506      | 0.9167    | 34  | 62         |
| $5$         | 0.0421      | 0.1620    | 0.9806      | 0.9333    | 42  | 118        |
| $8$         | 0.1217      | 0.3440    | 0.9595      | 0.9062    | 24  | 104        |
| $10$        | 0.1630      | 0.3295    | 0.9394      | 0.9167    | 22  | 119        |
| $15$        | 0.1813      | 0.2647    | 0.9302      | 0.9306    | 26  | 193        |

Table: Übersicht der Modellergebnisse \label{übersicht_modellergebnisse}

In Anhang 5 sind die detaillierten Ergebnisse der Modelltrainings anhand von Accuracy- und Loss-Graphen dargestellt. Die Graphen zeigen, dass die Modelle nach einer gewissen Anzahl von Epochen konvergieren und eine hohe Genauigkeit erreichen. Das Modell mit einer Trainingslänge von fünf Minuten erreichte die höchste Genauigkeit und konvergierte am schnellsten. Das liegt daran dass die längeren Trainingsdaten eine höhere Datenvielfalt bieten, was zu einer besseren Generalisierung des Modells führt. Dafür könnte es jedoch notwendig sein, die patience (Geduld) des "Early Stopping Callback" zu erhöhen um somit das Modell länger trainieren zu lassen. 

Für die Bestimmung der Parameter für den Identifizierungsprozess wurde das Modell mit 15-minütigen Trainingsdaten verwendet. Die Stimmerkennung wurde mit zwei Personen erprobt und mit zwei Mikrofonen an das Backend verbunden. Es ist zu beachten, dass diese Experimente in einer leeren, büroähnlichen Umgebung mit wenig Hintergrundgeräuschen durchgeführt wurden. Obwohl dies keine realistische Fahrzeugumgebung darstellt, hat sich die Wahl dieser Umgebung als optimal für schnelle Anpassungen der Parameter und wiederholte Tests erwiesen.

Weitere Experimente zur Bestimmung der optimalen Audiolänge für das Training wurden simuliert. Dazu wurde im Vorfeld ein Dialog der fünf trainierten Sprecher aufgenommen, der zur Evaluierung der verschiedenen Modelle verwendet wurde. Jeder Sprecher verfügte über ein eigenes Mikrofon, so dass für die Auswertung fünf Tonspuren entstanden sind. Die identischen Daten für die Klassifizierung gewährleisten einen homogenen Vergleich. Bei der Aufnahme des Dialogs wurde darauf geachtet, dass dieser mindestens drei Minuten lang ist und jeder Sprecher den gleichen Redeanteil hat. 

Die funktionellen Tests wurden im Fahrzeug durchgeführt. Dort wurden fünf Mikrofone installiert, die mit der Incar-Komponente verbunden waren. Für die Durchführung der Tests wurde ein Fahrzeug der Kompaktklasse mit fünf Sitzplätzen gewählt. Die Lavaliermikrofone wurden am Dachhimmel des Fahrzeugs befestigt und jeweils auf den Kopf des sitzenden Insassen in der jeweiligen Sitzposition ausgerichtet. In Anhang 6 wird dieser Aufbau anhand von Bildern gezeigt. Die Incar-Komponente wurde über Mobilfunk mit dem Backend verbunden.

### Bestimmung der Parameter

Es wurden verschiedene Kombinationen aus der Aufnahmedauer der Incar-Komponente und der Intervallzeit zwischen dem Versenden der Nachricht getestet. Die Parameter wurden mittels dynamischer Tests angepasst. Dabei konnten verschiedene Durchläufe mit angepassten Parametern zur Laufzeit bewertet und verbessert werden. Die Dokumentation der unterschiedlichen Ergebnisse war für das Erkennen und Nachvollziehen von Zusammenhängen von großer Bedeutung. 

Im Laufe der Tests konnten bereits Schwachstellen in der Fahrzeugerkennung erkannt werden, darunter die Verarbeitung von Situationen, in denen es still ist, das heißt in denen keiner der Insassen spricht. Dies führte häufig zu falschen Klassifizierungen. Aus dieser Erkenntnis wurde ein 'leerer Sprecher' trainiert, der ausschließlich aus Audiodaten besteht, die während einer ruhigen Leerfahrt aufgenommen wurden, ohne Stimmen. Dieser leere Sprecher wird bei der Bewertung nicht berücksichtigt und fließt nicht in die Berechnung des Medians zur Bestimmung des Sprechers ein.

Im Folgenden, eine kurze Dokumentation der beim Testen verwendeten Parameter, welche einen Zusammenhang erkennen lassen. Dabei steht $t_D$ für die Aufnahmedauer, $t_I$ für das Aufnahmeintervall, $c$ für die Klassifizierungs-Confidence (auf zwei Dezimalstellen gerundet) und $T$ für die Zeit, die erforderlich ist, um alle fünf Insassen richtig zu identifizieren. Alle Zeiten sind in Sekunden angegeben.

| $t_D$ | $t_I$ | $c$  | $T$ |
|-------|-------|------|-----|
| $1$   | $1$   | 0.82 | 51  |
| $1$   | $2$   | 0.79 | 58  |
| $5$   | $1$   | 0.93 | 34  |
| $5$   | $3$   | 0.91 | 41  |
| $10$  | $5$   | 0.94 | 65  |

Table: Versuchsergebnisse: Bestimmung der Parameter \label{versuch_parameter}

Eine weitere Aufteilung der Audiodaten in Sekundenabschnitte hatte keinen Einfluss auf die Klassifikationsergebnisse und daher wurde immer die volle Länge von $t_D$ als Modelleingabe verwendet. Aus Tabelle \ref{versuch_parameter} ergab sich, dass eine kurze $t_D$ keine guten Ergebnisse lieferte und $T$ daher angepasst werden musste. Zu lange $t_D$ erwiesen sich als unpraktisch, da sie eine längere Verarbeitungszeit durch das Socket verursachten und somit eine höhere $t_I$ verwendet werden musste. Die Bestimmung von $t_I$ hängt auch von der Geschwindigkeit des Verarbeitens im Backend ab. Obwohl keine Audiodaten verloren gehen, da diese in einer Queue landen, sollten die Daten zügig behandelt werden, um keine Inkonsistenzen zu haben. Das bedeutet auch, dass das Backend pro Intervall umso länger arbeiten muss, je mehr Insassen erkannt werden.

Final wurde ein $t_D$ von fünf Sekunden und ein $t_I$ von drei Sekunden gewählt, da dies die besten Ergebnisse lieferte ohne die Verarbeitungszeit zu sehr zu erhöhen.

### Bestimmung der Audiolänge

Die Audiolänge für den Trainingsprozess stellt einen entscheidenden Faktor für die Nutzerakzeptanz dar. Eine zu lange Audioaufnahme kann die Benutzer negativ beeinflussen, daher ist es wichtig, die Audiolänge auf ein Minimum zu reduzieren. Die im Versuchsaufbau trainierten Modelle wurden hierfür einzeln untersucht. Um die zuvor aufgezeichneten Dialoge an das Backend übertragen zu können, wurde eine Anpassung der Incar-Komponente vorgenommen, die anstelle der Mikrofondaten die Aufzeichnungen im gleichen Sendeformat überträgt.

Die Ergebnisse dieser Untersuchung wurden direkt aus dem Frontend extrahiert. Es wurde evaluiert, ob alle Sprecher korrekt erkannt wurden und wie lange es dauerte, bis alle Sprecher korrekt erkannt wurden.

| $T_{train}$ | Erkannte Sprecher | Erkennungs- dauer | Bemerkungen |
|--|--|---|-------------|
| $1$         |  0                |  -              | Abgebrochen nach 3 Minuten. Keine schlüssigen Ergebnisse. Die Klassifizierung erfolgte sehr sporadisch. |
| $3$         |  2                |  -              | Abgebrochen nach 3 Minuten. Klassifizierung zwar besser aber nicht schlüssig. |
| $5$         |  5                |  ~160s          | Nimmt zu viel Zeit in Anspruch. |
| $8$         |  5                |  ~80s           | Nimmt weniger Zeit in Anspruch. |
| $10$        |  5                |  ~65s           | Nimmt weniger Zeit in Anspruch. |
| $15$        |  5                |  ~60s           | Nimmt minimal weniger Zeit in Anspruch. |

Table: Versuchsergebnisse: Bestimmung der Audiolänge \label{versuch_trainingsdauer}

Wie aus der Tabelle \ref{versuch_trainingsdauer} hervorgeht, werden Sprecher erst ab einer Trainingsdatenlänge von fünf Minuten zuverlässig erkannt. Außerdem nimmt die Zeit bis zur vollständigen Erkennung mit zunehmender $T_{train}$  ab. Die Erkennungsdauer ist jedoch nicht linear proportional zur $T_{train}$ . Sie nimmt ab, bis sie bei einer $T_{train}$  von acht Minuten konstant bleibt. Dies deutet darauf hin, dass eine $T_{train}$  von circa acht Minuten ausreicht, um eine schnelle und zuverlässige Erkennung zu gewährleisten.

Interessanterweise wurde festgestellt, dass obwohl das Modell mit einer $T_{train}$ von fünf Minuten die beste Genauigkeit beim Training erreichte, die Erkennungsdauer bei einer höheren Trainingsdauer deutlich kürzer war. Dies könnte darauf hindeuten, dass die Modelle mit einer höheren Trainingsdauer von acht Minuten besser generalisiert und somit schneller und zuverlässiger arbeitet.

### Funktionalität

Basierend auf den vorherigen Erkenntnissen wurde ein neues Modell entwickelt und trainiert, welches drei Sprecher umfasst. Die jeweiligen Sprecher haben für das Training eine Audiolänge von etwa acht Minuten gesprochen. Verschiedene Szenarien wurden eingeführt, um die Leistungsfähigkeit der Implementierung zu bewerten. Die Szenarien wurden in fünf Versuchsvarianten unterteilt, die in Tabelle \ref{übersicht_funktion} aufgeführt sind.

| Versuch | Beschreibung                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| $V_1$   | Keine Hintergrundmusik, Insassen sprechen in normaler Tonlage und kontinuierlich.             |
| $V_2$   | Keine Hintergrundmusik, Insassen sprechen in normaler Tonlage, jedoch nicht kontinuierlich.     |
| $V_3$   | Hintergrundmusik vorhanden, jedoch weiterhin normale Unterhaltung möglich, Insassen sprechen in normaler Tonlage und kontinuierlich. |
| $V_4$   | Hintergrundmusik vorhanden, jedoch weiterhin normale Unterhaltung möglich, Insassen sprechen in erhöhter und aufgeregter Tonlage und kontinuierlich. |
| $V_5$   | Laute Hintergrundmusik vorhanden, normale Unterhaltung erschwert, Insassen sprechen in erhöhter Tonlage und kontinuierlich. |

Table: Übersicht der Funktionsversuche \label{übersicht_funktion}

Diese Versuche wurden während der Fahrt durchgeführt, so dass auch die Fahrgeräusche berücksichtig wurden. Es ist zu beachten, dass kein Dialog vorgegeben wurde und die Insassen frei gesprochen haben. Diese Versuche sind daher nicht vollständig reproduzierbar, bieten aber einen realitätsnahen Kontext. Für jede Versuchsvariante wurde die Ausgabe im Frontend nach jeder vergangenen Minute aufgezeichnet und in Tabelle \ref{versuch_funktionalität} festgehalten.

| Versuch | $t > 1$ | $t > 2$ | $t > 3$ | $t > 4$ | $t > 5$ |
|---------|---------|---------|---------|---------|---------|
| $V_1$   | 4       | 5       | 5       | 5       | 5       |
| $V_2$   | 1       | 1       | 4       | 5       | 5       |
| $V_3$   | 2       | 3       | 2       | 4       | 4       |
| $V_4$   | 0       | 0       | 1       | 1       | 2       |
| $V_5$   | 0       | 1       | 0       | 0       | 0       |

Table: Versuchsergebnisse: Funktionalität \label{versuch_funktionalität}

Die Ergebnisse des Versuchs ergaben, dass die Insassenidentifizierung in den gewöhnlichen Szenarien zuverlässig funktioniert. In Szenario $V_1$ und $V_2$ wurden nach spätestens drei Minuten alle Insassen korrekt erkannt. In $V_3$ wurden die Insassen ebenfalls fasst vollständig korrekt erkannt, jedoch dauerte dies wegen der Hintergrundmusik etwas länger. In Szenario $V_4$ und $V_5$ wurden die Insassen nicht erkannt. Dies ist auf die laute Hintergrundmusik zurückzuführen, die die Stimmerkennung beeinträchtigt.

Aus diesen Erkenntnissen lässt sich schließen, dass die Implementierung in der Lage ist, Insassen in einem normalen Fahrzeugumfeld zuverlässig zu identifizieren. Jedoch sollte das Erstellen des Modells so angepasst werden, dass Störfaktoren wie Hintergrundmusik besser verarbeitet werden können.

### Hinweis zur Validität

Unter den gegebenen Umständen ist es wichtig, darauf hinzuweisen, dass die durchgeführten Versuche nicht den strengen Kriterien wissenschaftlicher Validität entsprechen. Dies ist vor allem auf die zeitlichen Beschränkungen und die Schwierigkeit zurückzuführen, genügend Teilnehmer zu rekrutieren, die in der Lage wären, die für die Durchführung der Experimente erforderliche Zeit aufzubringen. Trotz dieser Einschränkungen ermöglichen die durchgeführten Versuche eine grundlegende Bewertung der Implementierung mit geringer Anzahl an Insassen. Diese ähneln einem Familienfahrzeugkontext und bilden ebenso eine solide Grundlage für zukünftige Forschungsarbeiten.

## Bewertung der Implementierung

Aus den durchgeführten Versuchen konnten eine Reihe von Erkenntnissen gewonnen werden. Im Anschluss werden diese Erkenntnisse bewertet und Schlussfolgerungen sowie Verbesserungsmöglichkeiten für zukünftige Forschung im Bereich der Stimmerkennung und ihrer Umsetzung im Fahrzeugkontext diskutiert.

### Datensicherheit

Die aktuelle Implementierung weist erhebliche Schwächen in Bezug auf den Schutz der personenbezogenen Daten auf. Die Übertragung aller Audiodaten für die Insassenerkennung erfolgt unverschlüsselt über ein Websocket zwischen der Incar-Komponente und dem Backend. Eine mögliche Alternative für eine datensichere Lösung wäre die lokale Ausführung der Insassenerkennung im Fahrzeug. Diese Herangehensweise wurde bereits in der Recherche als auch in der Implementierung diskutiert.

Eine sinnvolle Verbesserung der Datensicherheit ist möglich, wenn eine Verschlüsselung der Daten implementiert wird. Durch die Verwendung eines Verschlüsselungsalgorithmus, wie AES (Advanced Encryption Standard) kann sichergestellt werden, dass nur autorisierte Empfänger, in diesem Fall das Backend, die Daten entschlüsseln können. Die Verwendung von digitalen Zertifikaten kann ebenfalls gewährleisten, dass die Daten ausschließlich an den vorgesehenen Empfänger gesendet werden.

Darüber hinaus empfiehlt sich die Implementierung einer Integritätsprüfung, um sicherzustellen, dass die Daten während der Übertragung nicht manipuliert wurden.

Insgesamt ist es essenziell, diese Verbesserungen in einem realen Szenario zu implementieren, insbesondere wenn personenbezogene Daten verarbeitet werden, um die Einhaltung aller Datenschutzrichtlinien zu gewährleisten. Darüber hinaus ist zu beachten, dass der Einsatz von ML in zunehmendem Maße einer rechtlichen Überprüfung unterzogen wird.

### Benutzerfreundlichkeit

Aus den durchgeführten Versuchen konnten erste Eindrücke der Versuchsteilnehmer gewonnen werden. Diese Eindrücke sind zwar wissenschaftlich nicht verwendbar, jedoch für eine erste Einschätzung des Systems aufschlussreich.

Während des Trainingsprozesses wurde festgestellt, dass Audioaufnahmen, die länger als drei Minuten andauern, als ziemlich unattraktiv und unkomfortabel empfunden werden. Eine sinnvollere Alternative könnte das Hochladen von voraufgezeichneten Audioquellen sein. Außerdem wurde festgestellt, dass das erzwungene Sprechen während des Versuchs als störend empfunden wird. Auch wenn dies in der Praxis nicht gefordert wird, ist es für das Funktionieren der Stimmerkennung notwendig, dass die Insassen sprechen.

Es zeigte sich, dass das Konzept der Insassenerkennung mittels Stimmerkennung von den Insassen als eher belastend empfunden wird. Interessanterweise haben die Teilnehmer jedoch das Potenzial der Insassenerkennung erkannt, was als Motivation für weitere Forschungsbemühungen dienen sollte.

### Funktionalität und Genauigkeit

Die Ergebnisse hinsichtlich der Funktionalität sind nicht eindeutig. Obwohl die Genauigkeit mit verlängerter Laufzeit der Tests zunimmt, bleiben die Ergebnisse inkonsistent. Dies erschwert einen zuverlässigen Ersatz für die konventionelle Fahreridentifizierung und beeinträchtigt den Einsatz für die Insassen, da die Insassenerkennung nur während der Fahrt zuverlässige Ergebnisse liefert.

Um den Erkennungsprozess zu verbessern, sollten verschiedene Maßnahmen ergriffen werden. Unter anderem könnte mehr Aufwand in die Optimierung des ML-Modells investiert werden wie die Verfeinerung der Klassifizierungsalgorithmen durch den Einsatz von mehr Datenquellen oder erweiterte ML-Verfahren.

Darüber hinaus könnte die Aufnahme der Insassen in der Incar-Komponente verbessert werden. Wie aus den Versuchen hervorgeht, wird die Stimmerkennung durch laute Hintergrundgeräusche beeinträchtigt. Daher könnten Mechanismen zur Stimmisolierung implementiert werden, um irrelevante Frequenzen herauszufiltern und so die Erkennungsgenauigkeit zu verbessern.

Es ist wichtig zu beachten, dass die Bewertung und Verbesserung einer solchen Implementierung ein iterativer Prozess ist, der weitere Forschung und experimentelle Validierung erfordert, um die Leistungsfähigkeit des Systems zu maximieren.

### Schlussfolgerung

Bei oberflächlicher Betrachtung erscheinen die Versuchsergebnisse hinsichtlich der Anwendbarkeit der Stimmerkennung zur Identifizierung von Fahrzeuginsassen negativ. Das Gesamtkonzept ist aufgrund seiner Komplexität und bezüglich der Genauigkeitsprobleme für die Umsetzung nicht geeignet. Zudem ist eine erhebliche Rechenleistung für das Training des Modells erforderlich und die Klassifikation dauert zu lange.

Dennoch ist festzuhalten, dass die Spracherkennung auch für andere Anwendungsfälle im Fahrzeug eingesetzt werden kann. Die vorliegende Implementierung kann bereits erfolgreich Personen identifizieren und die zugehörige Architektur ist für den Fahrzeugkontext geeignet. Um bessere Ergebnisse zu erzielen oder andere Anwendungsgebiete zu finden, ist jedoch weiterer Zeit- und Forschungsaufwand erforderlich.
