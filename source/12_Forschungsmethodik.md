# Forschungsmethodik

Bei der Implementierung von Insassenidentifikationstechnologien im Fahrzeugkontext sind nicht nur Zuverlässigkeit und Genauigkeit entscheidend, sondern auch Aspekte der Sicherheit und Datenschutz spielen eine zentrale Rolle. Dieses Kapitel widmet sich der Forschungsmethodik, die darauf abzielt, die Anwendbarkeit von Identifizierungstechnologien im Fahrzeugumfeld zu evaluieren.

## Auswahl der Identifizierungstechnologien zur Untersuchung

Die grundlegenden Erkenntnisse aus vorangegangenen Untersuchungen über Technologien im aktuellen Fahrzeugkontext wie schlüsselbasierte Identifizierung und biometrische Lösungen bilden die Basis für die hier vorgestellten Identifizierungstechnologien. Die Bewertung dieser Technologien ermöglicht es, den Einsatz im Fahrzeugbereich detailliert zu untersuchen und sowohl ihre Vorzüge als auch potenzielle Herausforderungen zu identifizieren. 

Die ausgewählten Identifizierungstechnologien haben ihre Ursprünge in verschiedenen Branchen außerhalb des Automobilsektors. Diese Querverbindungen eröffnen eine neue Perspektive, da sie auf ein bereits etabliertes Potenzial hinweisen. Die Anwendbarkeit dieser Technologien in unterschiedlichen Kontexten, sei es in der Telekommunikationsbranche oder bei Banken, unterstreicht ihre Vielseitigkeit und Relevanz, um das mögliche Potenzial dieser Technologien im Fahrzeugbereich vollständig zu erfassen. Diese interdisziplinäre Perspektive ermöglicht es, bewährte Verfahren und Innovationen aus anderen Kontexten zu integrieren und somit einen umfassenden Blick auf die Möglichkeiten der Identifizierungstechnologien im Automobilsektor zu werfen.

------------------------------------------------------------------------------------------------------------
Technologie             Kontext             Einsatz als Identifizierungstechnologie  
------------------      --------------      ----------------------------------------------------------------
Mobile App              Gerätebasiert       Mehrfaktor Authentifizierung, Online-Banking TAN Verfahren

Gesichtserkennung       Biometrie           Einsatz in Smartphones und Tablets zur Entsperrung

Stimmenerkennung        Biometrie           Einsatz in intelligente Assistenten und Kundenservice Hotlines

Ultrabreitband          Gerätebasiert       Lokalisierung und Entfernungsmessung, nicht als Identifizierungstechnologie

------------------------------------------------------------------------------------------------------------
Table: Auflistung der ausgewählten Identifizierungstechnologien \label{identifizierungstechnologieauflistung}

Die Tabelle \ref{identifizierungstechnologieauflistung} zeigt die ausgewählten Identifizierungstechnologien und ihre Einsatzbereiche. Die Technologien wurden aufgrund ihrer Relevanz und ihres Potenzials für den Einsatz im Fahrzeugbereich ausgewählt. Die Bewertung dieser Technologien ermöglicht es, den Einsatz im Fahrzeugbereich detailliert zu untersuchen und sowohl ihre Vorzüge als auch potenzielle Herausforderungen zu identifizieren.

## Evaluierung der Identifizierungstechnologien

### Zuverlassigkeit und Genauigkeit

Die methodische Evaluierung der Zuverlässigkeit von Identifizierungstechnologien im Fahrzeugkontext beruht auf mehreren Ansätzen. Primär erfolgt eine Bewertung auf Basis der Branchen, in denen die betreffende Technologie bereits erfolgreich eingesetzt wird. Hierbei werden Feldstudien und Erfahrungsberichte aus diesen Branchen herangezogen, um Erkenntnisse über die praktische Anwendbarkeit und Zuverlässigkeit zu gewinnen. Die Integration von Feldstudien ermöglicht eine breite Diversität an Anwendungsszenarien und Nutzerprofilen, wodurch die Technologie in realen Fahrbedingungen auf ihre Konsistenz hin bewertet wird.

Zusätzlich wird geprüft, ob vorhandene Online-Berichte, insbesondere auf Plattformen wie YouTube, Aufschluss über die Leistungsfähigkeit der Identifizierungstechnologie bieten können. Die Auswertung solcher Berichte ermöglicht nicht nur einen Einblick in tatsächliche Anwendungen und Erfahrungen von Endnutzern, sondern kann auch mögliche Herausforderungen und Ausfälle aufzeigen.

Die methodische Herangehensweise beinhaltet schließlich eine eigene Erprobung der Technologie, sofern möglich. Durch diese praktische Umsetzung können spezifische Testszenarien nachgestellt werden, um die Leistungsfähigkeit der Identifizierungstechnologie in einem kontrollierten Umfeld zu überprüfen. Hierbei werden insbesondere Ausfälle und Herausforderungen detailliert analysiert, um mögliche Schwachstellen der Technologie zu identifizieren und Optimierungsbedarf aufzuzeigen. Diese umfassende methodische Vorgehensweise ermöglicht eine wissenschaftlich fundierte Beurteilung der Zuverlässigkeit von Identifizierungstechnologien im Fahrzeugkontext.

### Sicherheit und Datenschutz

Die Evaluierung der Sicherheit und des Datenschutzes von Identifizierungstechnologien im Fahrzeugkontext erfolgt anhand einer systematischen Methodik, die verschiedene Aspekte berücksichtigt. Die Sicherheit der Identifizierungstechnologie wird durch die Konzeptionierung einer möglichen Architektur für den Fahrzeugkontext. Hierbei wird überprüft ob sensible Daten ausschließlich auf dem Fahrzeug gespeichert und verarbeitet werden können. Falls ein Datenaustausch mit einem Backend notwendig ist, wird die Sicherheit des Austauschs bewertet. Die Einhaltung von Datenschutzvorgaben wird bewährt, um klare Maßnahmen für die Verarbeitung, Speicherung und Übertragung von Identifikationsdaten sicherzustellen. Die mögliche Anwendung von Anonymisierungstechniken wird bewertet, um sicherzustellen, dass personenbezogene Identifikationsdaten angemessen geschützt und anonymisiert werden. 

Die Identifizierung von potenziellen Schwachstellen kann ebenfalls durch die Analyse wissenschaftliche Paper und sicherheitstechnischer Konferenzen erfolgen. Diese Quellen bieten Einblicke in aktuelle Forschungsergebnisse, Sicherheitsanalysen und mögliche Schwachstellen von Identifizierungstechnologien. 

### Integration im Fahrzeugkontext

Die Integration von Identifizierungstechnologien im Fahrzeugkontext erfordert eine andere Herangehensweise als in andere Branchen. Unter Berücksichtigung von verschiedenen Faktoren muss eine mögliche Implementierung der Identifikationstechnologie ISO 26262 erfüllen, eine Norm, die sich mit der Funktionalen Sicherheit von Fahrzeugen befasst. „Gemäß der ISO 26262 Anforderungen muss die Wahrscheinlichkeit eines fehlerfreien Betriebs bei Einzelfehlern bei >99% bzw. für Mehrfachfehler bei > 90% liegen und das bei einer Fehlerrate von weniger als $10^{-8} /h$“.[@SW_basierte_Integration] 

Der Rechenaufwand bei der Identifizierung eines Insassen ist relevant, um eine effiziente und verzögerungsfreie Identifikation zu gewährleisten. Die Implementierung von leistungsfähigen Hardwarekomponenten kann in einem Fahrzeugkontext eher unrealistisch sein wegen des hohen Energiebedarfs, Größe- und Kostenfaktoren.

Die Tauglichkeit der Nutzer für die Identifizierungstechnologie wird ebenfalls sorgfältig betrachtet werden. Lösungen, die eine unangenehme oder mühsame Interaktion erfordern, könnten die Akzeptanz und Nutzerfreundlichkeit beeinträchtigen. Daher ist es wichtig, Technologien zu wählen, die eine bequeme und benutzerfreundliche Identifikation gewährleisten, ohne die Fahrer oder Insassen in unangenehme Situationen zu bringen.

<!--
Bilder können mit der folgenden Syntax eingefügt werden:
![Bildunterschrift \label{mein_label}](source/figures/beispielbild.jpg){ width=50% }
-->
