# Einleitung

> *„**Personalisierung** ist sinnlos, ohne den Einzelnen zu kennen. Verstehe die Träume, Hoffnungen und Ängste, die deinen Kunden motivieren, treffe ihn dort, wo es darauf ankommt.“*
> 
> \hfill -- Paul Gillin, Social-Media-Experte

Personalisierung ist ein zentrales Thema im Bereich der sozialen Medien, aber wie sieht es mit den Endgeräten aus, die wir täglich nutzen? Kennen diese uns genauso gut wie unsere sozialen Medien? Diese Arbeit beschäftigt sich mit der Personalisierung im Fahrzeug, insbesondere mit der Insassenerkennung.

## Motivation

Die Integration von Insassenidentifizierungssystemen in Fahrzeugen eröffnet zahlreiche Anwendungsmöglichkeiten für ein personalisiertes Fahrerlebnis. Dieses ermöglicht, die individuellen Bedürfnisse und Vorlieben der Fahrzeuginsassen zu erkennen und entsprechende Anpassungen vorzunehmen. 

Ein praktisches Beispiel hierfür ist die gemeinsame Nutzung eines Fahrzeugs durch eine vierköpfige Familie. Angenommen, die Mutter nimmt auf dem Beifahrersitz Platz – die Insassenidentifizierung könnte automatisch die Klimaautomatik auf ihre bevorzugte Temperatur einstellen. Sobald der Sohn das Steuer übernimmt, passt das System die Fahrzeugleistung an, um den Fahrstil eines jungen und weniger erfahrenen Fahrers zu berücksichtigen. Gleichzeitig kann das Unterhaltungssystem im Fond des Fahrzeugs auf die Interessen der Tochter auf der Rückbank abgestimmt werden. Bei Fahrten, bei denen nur die Eltern anwesend sind, könnte das System sogar automatisch die bevorzugte Musik auswählen, um eine angenehme Atmosphäre zu schaffen.

Ebenso bietet die Insassenidentifikation einen praktischen Vorteil für häufige Nutzer von Mietfahrzeugen. Steigt ein regelmäßiger Nutzer in ein beliebiges Poolfahrzeug ein, wird sofort sein individuelles Fahrerprofil aktiviert. Dadurch werden persönliche Einstellungen wie Sitzposition, gespeicherte Reiseziele und bevorzugte Klimaeinstellungen automatisch angepasst. 

Diese Kurzbeschreibung verdeutlicht, dass die Insassenidentifikation nicht nur das Fahrerlebnis personalisiert, sondern auch den gesamten Fahrzeuginnenraum intelligent auf die Bedürfnisse der Insassen abstimmt. Dies bezieht sich nicht nur auf den Komfortaspekt, sondern trägt zur Verbesserung von Fahrsicherheit und Effizienz bei. In einer Zeit, in der die Umgestaltung der Mobilität in den Mittelpunkt rückt, könnten die beschriebenen innovativen Ansätze einen wesentlichen Beitrag zur zukünftigen Gestaltung der Fahrzeugnutzung leisten.

## Umfang der Arbeit

Die vorliegende Arbeit befasst sich mit der Identifizierung von Insassen in Fahrzeugen, insbesondere im Kontext der BMW Group. Die Abteilung: On-Demand-Mobilität (ODM) der BMW Group entwickelt kontinuierlich neue Konzepte, um die Zukunft der Mobilität aktiv zu gestalten. Ein wichtiger Beobachtungsaskpekt ist der rückläufige Trend des Fahrzeugbesitzes in Großstädten [@staedtevergleich], wobei alternative Lösungen wie Carsharing oder Fahrzeugpools zunehmend an Bedeutung gewinnen. [@carsharing_entlastet_umwelt_verkehr] Das übergeordnete Ziel besteht darin, BMW optimal auf die Herausforderungen der zukünftigen Mobilität vorzubereiten, indem innovative Konzepte entworfen werden, die unter anderem das Teilen von Fahrzeugen erleichtern.

Im Rahmen dieser Arbeit werden verschiedene Identifikationsmethoden inner- und außerhalb der Automobilbranche untersucht. Ein Vergleich mit anderen Automobilherstellern (OEMs) dient der Kontextualisierung und ermöglicht die Ableitung von bewährten Methoden. Die Vorstellung von vier ausgewählten Identifikationsmethoden sowie die prototypische Umsetzung und Erprobung einer dieser Methoden bilden den Schwerpunkt dieser Bachelorarbeit.

Dabei stellt diese Arbeit einen konzeptionellen Ansatz dar und verfolgt nicht das Ziel eines direkten Produktentwurfs. Die Ergebnisse der Arbeit sollen als Grundlage für weitere Forschung und Entwicklung dienen und die BMW Group bei der Gestaltung zukünftiger Mobilitätskonzepte unterstützen.

## Problemstellung und Zielsetzung

Die Einführung von Identifizierungstechnologie im Fahrzeugkontext ist zwangsläufig mit verschiedenen Herausforderungen verbunden. Ein zentraler Aspekt ist der Datenschutz, da es sich bei der Verarbeitung von personenbezogenen Daten um sensible Informationen handelt. Die Gewährleistung eines sicheren und rechtskonformen Umgangs mit diesen Daten ist unerlässlich.

Die Zuverlässigkeit der Identifikationsergebnisse ist ein weiteres Problemfeld, das sich insbesondere bei unterschiedlichen Umgebungs- und Nutzungsbedingungen ergeben kann. Die Benutzerfreundlichkeit ist ein entscheidender Faktor, da die Akzeptanz der Identifizierungsmethode weitgehend von ihrer Einfachheit und Effizienz abhängt. Ein übermäßiger Aufwand bei der Einrichtung der Methode kann die Benutzerfreundlichkeit beeinträchtigen und eine verbreitete Verwendung der Methode verhindern.

Wie im Folgenden deutlich werden wird, ist die Identifikation von Insassen in Fahrzeugen ein komplexes Thema, das mit verschiedenen Herausforderungen verbunden ist. Ziel dieser Arbeit ist daher die Untersuchung verschiedener Identifikationsmethoden und die prototypische Umsetzung einer ausgewählten Methode. Es ist nicht das Ziel, ein voll funktionsfähiges System zu entwickeln, sondern einen Proof of Concept zu erstellen, der weitere Forschungen und Entwicklungen nach sich zieht.

## Forschungsfrage

Mit dem obigen Wissensstand ist es jetzt möglich eine Forschungsfrage zu definieren, welche mit der prototypischen Umsetzung beantwortet werden kann. 

**Wie kann die Insassenidentifizierung unter Berücksichtigung von Datenschutz, Nutzbarkeit und Funktionalität umgesetzt werden?**

Die Forschungsmethodik umfasst die Implementierung eines Prototyps für die Insassenidentifizierung unter Verwendung moderner Technologien. Die Auswertung dieser Implementierung erfolgt anhand einiger Versuche, bei denen die Funktionalität, Sicherheit und Benutzerfreundlichkeit der Implementierung bewertet werden. Die Ergebnisse der Versuche werden in einem umfassenden Kontext betrachtet und diskutiert.

## Aufbau der Arbeit

Diese Bachelorarbeit ist zweigeteilt und widmet sich der innovativen Insassenerkennung in Fahrzeugen. 

Der theoretische Teil der Arbeit konzentriert sich auf die Literaturrecherche verschiedener Technologien zur Insassenidentifikation im Fahrzeug. Dabei wird eine Bestandsaufnahme der derzeit auf dem Markt verfügbaren Lösungen durchgeführt. Der Schwerpunkt liegt dabei auf der Bewertung ihrer Vor- und Nachteile sowie ihrer Anwendbarkeit im Fahrzeugkontext. Die umfassende Recherche gibt einen fundierten Überblick über den Stand der Forschung und die vorhandenen Lösungen in diesem Bereich.

Im zweiten Teil der Arbeit geht es um die prototypische Umsetzung einer ausgewählten Methode. Die Auswahl erfolgt auf der Grundlage der im theoretischen Teil gewonnenen Erkenntnisse. Die Implementierung wird durchgeführt, um die praktische Anwendbarkeit und Funktionalität der ausgewählten Methode zu untersuchen, die im Anschluss anhand von Versuchen evaluiert werden soll.

Die Ergebnisse der theoretischen Forschung und der Implementierung werden in einem ganzheitlichen Kontext betrachtet. Mögliche Implikationen für die weitere Entwicklung und Anwendung der Insassenidentifikation in Fahrzeugen werden diskutiert. Die Arbeit schließt mit einem Ausblick auf mögliche Ansätze für weitere Forschungsprojekte auf diesem komplexen Gebiet.
