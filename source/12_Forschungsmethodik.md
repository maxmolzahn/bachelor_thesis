# Forschungsmethodik

Bei der Implementierung von Insassenidentifikationstechnologien im Fahrzeugkontext sind nicht nur Zuverlässigkeit und Präzision entscheidend, sondern auch Aspekte der Sicherheit und Datenschutz spielen eine zentrale Rolle. Dieses Kapitel widmet sich der Forschungsmethodik, die darauf abzielt, die Anwendbarkeit von Identifizierungstechnologien im Fahrzeugumfeld zu evaluieren.

## Auswahl der Identifizierungstechnologien zur Untersuchung

Die grundlegenden Erkenntnisse aus vorangegangenen Untersuchungen über Technologien im aktuellen Fahrzeugkontext wie schlüsselbasierte Identifizierung und biometrische Lösungen bilden die Basis für die hier vorgestellten Identifizierungstechnologien. Die Bewertung dieser Technologien ermöglicht es, den Einsatz im Fahrzeugbereich detailliert zu untersuchen und sowohl ihre Vorzüge als auch potenzielle Herausforderungen zu identifizieren. 

Die ausgewählten Identifizierungstechnologien haben ihre Ursprünge in verschiedenen Branchen außerhalb des Automobilsektors. Die Querverbindung und Anwendbarkeit dieser Technologien in unterschiedlichen Kontexten, sei es in der Telekommunikationsbranche oder bei Banken, unterstreicht ihre Vielseitigkeit und Relevanz, um auch das mögliche Potenzial dieser Technologien im Fahrzeugbereich vollständig zu erfassen. Diese interdisziplinäre Perspektive ermöglicht es, bewährte Verfahren und Innovationen aus anderen Kontexten zu integrieren und somit einen umfassenden Blick auf die Möglichkeiten der Identifizierungstechnologien im Automobilsektor zu werfen.

------------------------------------------------------------------------------------------------------------
Technologie             Kontext             Einsatz als Identifizierungstechnologie  
------------------      --------------      ----------------------------------------------------------------
Mobile App              Gerätebasiert       Mehrfaktor Authentifizierung, Online-Banking TAN Verfahren

Gesichtserkennung       Biometrie           Einsatz in Smartphones und Tablets zur Entsperrung

Stimmerkennung          Biometrie           Einsatz in intelligente Assistenten und Kundenservice Hotlines

Ultrabreitband          Gerätebasiert       Lokalisierung und Entfernungsmessung, nicht als Identifizierungstechnologie

------------------------------------------------------------------------------------------------------------
Table: Auflistung der ausgewählten Identifizierungstechnologien \label{identifizierungstechnologieauflistung}

Die Tabelle \ref{identifizierungstechnologieauflistung} zeigt die ausgewählten Identifizierungstechnologien und ihre Einsatzbereiche. Die Technologien wurden aufgrund ihrer Relevanz und ihres Potenzials für den Einsatz im Fahrzeugbereich ausgewählt. Die Bewertung dieser Technologien ermöglicht es, den Einsatz im Fahrzeugbereich detailliert zu untersuchen und sowohl ihre Vorzüge als auch potenzielle Herausforderungen zu identifizieren.

## Evaluierung der Identifizierungstechnologien

### Zuverlässigkeit und Genauigkeit

Die methodische Evaluierung der Zuverlässigkeit von Identifizierungstechnologien im Fahrzeugkontext beruht auf mehreren Ansätzen. Primär erfolgt eine Bewertung auf Basis der Branchen, in denen die betreffende Technologie bereits erfolgreich eingesetzt wird. Hierbei werden Studien und Erfahrungsberichte aus diesen Branchen herangezogen, um Erkenntnisse über die praktische Anwendbarkeit und Zuverlässigkeit zu gewinnen. Die Untersuchung von Studien ermöglicht eine breite Diversität an Anwendungsszenarien und Nutzerprofilen, wodurch die Technologie in realen Fahrbedingungen auf ihre Verlässlichkeit hin bewertet wird.

Die methodische Herangehensweise beinhaltet schließlich eine Selbsterprobung der Technologie, sofern möglich. Durch diese praktische Umsetzung können spezifische Testszenarien nachgestellt werden, um die Leistungsfähigkeit der Identifizierungstechnologie in einem kontrollierten Umfeld zu überprüfen. Hierbei werden insbesondere Ausfälle und Herausforderungen analysiert, um mögliche Schwachstellen der Technologie zu identifizieren und einen Optimierungsbedarf aufzuzeigen.

Die Identifizierung von potenziellen Schwachstellen kann ebenfalls durch die Analyse wissenschaftlicher und sicherheitstechnischer Konferenzen erfolgen. Diese Quellen bieten Einblicke in aktuelle Forschungsergebnisse, Sicherheitsanalysen und mögliche Schwachstellen von Identifizierungstechnologien. 

### Sicherheit und Datenschutz

Die Evaluierung der Sicherheit und des Datenschutzes von Identifizierungstechnologien im Fahrzeugkontext erfolgt anhand einer systematischen Methodik, die verschiedene Aspekte berücksichtigt. Die Sicherheit der Identifizierungstechnologie wird auf Grundlage einer Konzeptionierung einer möglichen Architektur für den Fahrzeugkontext bewertet. Hierbei wird überprüft ob sensible Daten ausschließlich auf dem Fahrzeug gespeichert und verarbeitet werden können. Falls ein Datenaustausch mit einem Backend notwendig ist, wird die Sicherheit dieses Austausches bewertet. Die Einhaltung von Datenschutzvorgaben wird gewährt, um klare Vorgaben für die Verarbeitung, Speicherung und Übertragung von Identifikationsdaten sicherzustellen. 

### Integration im Fahrzeugkontext

Die Integration von Identifizierungstechnologien im Fahrzeugkontext erfordert eine andere Herangehensweise als in andere Branchen. Unter Berücksichtigung von verschiedenen Faktoren muss eine mögliche Implementierung der Identifikationstechnologie ISO 26262 erfüllen, eine Norm, die sich mit der Funktionalen Sicherheit von Fahrzeugen befasst. *„Gemäß der ISO 26262 Anforderungen muss die Wahrscheinlichkeit eines fehlerfreien Betriebs bei Einzelfehlern bei >99% bzw. für Mehrfachfehler bei > 90% liegen und das bei einer Fehlerrate von weniger als $10^{-8} /h$“*. [@SW_basierte_Integration] 

Um eine effiziente und verzögerungsfreie Identifikation zu gewährleisten, ist der Rechenaufwand für die Identifikation eines Insassen relevant. Die Implementierung leistungsfähiger Hardwarekomponenten kann im Fahrzeugkontext aufgrund des hohen Energiebedarfs, der Größe und der Kostenfaktoren eher unrentable sein.

Auch die Nutzertauglichkeit der Identifizierungstechnologie wird sorgfältig geprüft. Lösungen, die eine unangenehme oder langwierige Interaktion erfordern, könnten die Akzeptanz und Benutzerfreundlichkeit beeinträchtigen. Es ist daher wichtig, Technologien zu wählen, die eine bequeme und benutzerfreundliche Identifizierung gewährleisten, ohne Fahrer oder Fahrgäste in unerwünschte Situationen zu bringen.
