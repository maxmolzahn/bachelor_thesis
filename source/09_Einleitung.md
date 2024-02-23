# Einleitung

## Einrahmung der Arbeit

Die vorliegende Arbeit befasst sich mit der Identifizierung von Insassen in Fahrzeugen, insbesondere im Kontext der BMW Group. Die Abteilung: On-Demand-Mobilität der BMW Group entwickelt kontinuierlich neue Konzepte, um die Zukunft der Mobilität aktiv zu gestalten. Ein wichtiger Beobachtungspunkt ist der rückläufige Trend des Fahrzeugbesitzes in Großstädten[@staedtevergleich], wobei alternative Lösungen wie Carsharing oder Fahrzeug-pools zunehmend an Bedeutung gewinnen[@carsharing_entlastet_umwelt_verkehr]. Das übergeordnete Ziel besteht darin, BMW optimal auf die Herausforderungen der zukünftigen Mobilität vorzubereiten, indem innovative Konzepte entworfen werden, die unter anderem das Teilen von Fahrzeugen erleichtern.

Im Rahmen dieser Arbeit werden verschiedene Identifikationsmethoden in- und außerhalb der Automobilbranche untersucht. Ein Vergleich mit anderen Automobilherstellern (OEMs) dient der Kontextualisierung und ermöglicht die Ableitung von bewährten Methoden. Die Vorstellung von vier ausgewählten Identifikationsmethoden sowie die prototypische Umsetzung und Erprobung einer dieser Methoden bilden den Schwerpunkt dieser Studie.

Dabei stellt diese Arbeit einen konzeptionellen Ansatz dar und verfolgt nicht das Ziel eines direkten Produktentwurfs. Die Ergebnisse der Arbeit sollen als Grundlage für weitere Forschung und Entwicklung dienen und die BMW Group bei der Gestaltung zukünftiger Mobilitätskonzepte unterstützen.

## Hintergrund und Kontext

Die Integration von Insassenidentifizierungssystemen in Fahrzeugen eröffnet zahlreiche Anwendungsmöglichkeiten für ein personalisiertes Fahrerlebnis. Dies ermöglicht, die individuellen Bedürfnisse und Vorlieben der Fahrzeuginsassen zu erkennen und entsprechende Anpassungen vorzunehmen. 

Ein praktisches Beispiel hierfür ist die gemeinsame Nutzung eines Fahrzeugs durch eine vierköpfige Familie. Angenommen, die Mutter nimmt auf dem Beifahrersitz Platz – die Insassenidentifizierung könnte automatisch die Klimaautomatik auf ihre bevorzugte Temperatur einstellen. Sobald der Sohn das Steuer übernimmt, passt das System die Fahrzeugleistung an, um den Fahrstil eines jungen und weniger erfahrenen Fahrers zu berücksichtigen. Gleichzeitig kann das Unterhaltungssystem im Fond des Fahrzeugs auf die Interessen der Tochter auf der Rückbank abgestimmt werden. Bei Fahrten, bei denen nur die Eltern anwesend sind, könnte das System sogar automatisch die passende Musik auswählen, um eine angenehme Atmosphäre zu schaffen.

Ebenso bietet die Insassenidentifikation einen praktischen Vorteil für häufige Nutzer von Mietfahrzeugen. Steigt ein regelmäßiger Nutzer in ein beliebiges Pool-Fahrzeug ein, wird sofort sein individuelles Fahrerprofil aktiviert. Dadurch werden persönliche Einstellungen wie Sitzposition, gespeicherte Reiseziele und bevorzugte Klimaeinstellungen automatisch angepasst. 

Das verdeutlicht, dass die Insassenidentifikation nicht nur das Fahrerlebnis personalisiert, sondern auch den gesamten Fahrzeuginnenraum intelligent auf die Bedürfnisse der Insassen abstimmt. Dies geht über den Komfortaspekt hinaus und trägt zur Verbesserung von Fahrsicherheit und Effizienz bei. In einer Zeit, in der die Umgestaltung der Mobilität in den Mittelpunkt rückt, könnten solche innovativen Ansätze einen wesentlichen Beitrag zur zukünftigen Gestaltung der Fahrzeugnutzung leisten.

## Problemstellung und Zielsetzung

Die Einführung von Identifizierungstechnologie im Fahrzeugkontext ist zwangsläufig mit verschiedenen Herausforderungen verbunden. Ein zentraler Aspekt ist der Datenschutz, da es sich bei der Verarbeitung von personenbezogenen Daten um sensible Informationen handelt. Die Gewährleistung eines sicheren und rechtskonformen Umgangs mit diesen Daten ist unerlässlich.

Die Konsistenz der Identifikationsergebnisse ist ein weiteres Problemfeld, das sich insbesondere bei unterschiedlichen Umgebungs- und Nutzungsbedingungen ergeben kann. Die Benutzerfreundlichkeit ist ein entscheidender Faktor, da die Akzeptanz der Identifizierungsmethode weitgehend von ihrer Einfachheit und Effizienz abhängt. Ein übermäßiger Aufwand bei der Einrichtung der Methode kann die Benutzerfreundlichkeit beeinträchtigen und eine verbreitete Verwendung der Methode verhindern.

Wie im Folgenden deutlich werden wird, ist die Identifikation von Insassen in Fahrzeugen ein komplexes Thema, das mit verschiedenen Herausforderungen verbunden ist. Ziel dieser Arbeit ist daher die Untersuchung verschiedener Identifikationsmethoden und die prototypische Umsetzung einer ausgewählten Methode. Es ist nicht das Ziel, ein voll funktionsfähiges System zu entwickeln, sondern einen Proof of Concept zu erstellen, der weitere Forschungen und Entwicklungen nach sich zieht.

## Definition: Identifizierung

Die Identifikation einer Person ist ein komplexer Prozess, der verschiedene Aspekte umfasst und insbesondere im Hinblick auf Datenschutz von entscheidender Bedeutung ist. 

Identifizierung: „jemanden/etwas meist an bestimmten Merkmalen (wieder)erkennen.“[@definition_identifizierung]

Hierbei spielen Begriffe wie Authentisierung, Authentifizierung und Autorisierung eine Schlüsselrolle, welche auch häufig verwechselt werden.

### Definition: Authentisierung

Im Rahmen einer Authentisierung erbringt eine Person einen Beweis dafür, dass sie ist, wer sie zu sein vorgibt. Im Alltag geschieht dies z. B. durch die Vorlage des Personalausweises. In der IT wird hierfür häufig ein Passwort in Kombination mit einem Benutzernamen genutzt.[@definition_authentisierung_authentifizierung_autorisierung]

### Definition: Authentifizierung

Authentifizierung ist der spezifischere Prozess der Überprüfung der Identität eines Subjekts, normalerweise durch die Verwendung von Anmeldeinformationen wie Benutzername und Passwort, Fingerabdruck, RFID-Karte oder andere biometrische Merkmale.[@definition_authentisierung_authentifizierung_autorisierung]

### Definition: Autorisierung

Autorisierung bezieht sich auf den Prozess der Festlegung von Berechtigungen oder Rechten für eine authentifizierte Entität. Nach erfolgreicher Authentifizierung legt die Autorisierung fest, welche Aktionen oder Ressourcen die authentifizierte Entität nutzen kann.[@definition_authentisierung_authentifizierung_autorisierung]

Diese Begriffe sind im Zusammenhang mit der Identifizierung von Personen im digitalen Alltag von Bedeutung. Dabei steht auch der Umgang mit personenbezogenen Daten im Mittelpunkt.

### Definition: Personenbezogene Daten

*"personenbezogene Daten" alle Informationen, die sich auf eine identifizierte oder identifizierbare natürliche Person […] beziehen; als identifizierbar wird eine natürliche Person angesehen, die direkt oder indirekt, insbesondere mittels Zuordnung zu einer Kennung wie einem Namen, zu einer Kennnummer, zu Standortdaten, zu einer Online-Kennung oder zu einem oder mehreren besonderen Merkmalen, die Ausdruck der physischen, physiologischen, genetischen, psychischen, wirtschaftlichen, kulturellen oder sozialen Identität dieser natürlichen Person sind, identifiziert werden kann;* (Art. 4 Nr. 1 DSGVO)

Bei der prototypischen Entwicklung der Insassenidentifizierung ist es von besonderer Bedeutung, personenbezogene Daten durch korrekte Authentisierung zu schützen und sicherzustellen, dass die Autorisierung angemessen erfolgt.

## Forschungsfrage

Mit dem obigen Wissenstand ist es jetzt möglich eine Forschungsfrage zu deferieren, welche mit der prototypischen Umsetzung beantwortet werden kann. 

**Wie kann die Insassenidentifizierung unter Berücksichtigung von Datenschutz, Nutzbarkeit und Funktionalität mithilfe moderner Technologien prototypisch umgesetzt werden?**

Die Forschungsmethodik umfasst die Implementierung eines Prototyps für die Insassenidentifizierung unter Verwendung moderner Technologien. Die Evaluierung erfolgt durch eine Nutzerstudie, bei denen die Probanden die Effektivität, Sicherheit und Benutzerfreundlichkeit der Implementierung bewerten. Der beigefügte Fragebogen im Anhang dient als Instrument zur systematischen Datenerhebung und Auswertung der Studie. Die Ergebnisse der Nutzerstudie werden im Rahmen der Arbeit ausführlich analysiert und diskutiert.

## Aufbau der Arbeit

Diese Bachelorarbeit ist zweigeteilt und widmet sich der innovativen Insassenerkennung in Fahrzeugen. 

Der theoretische Teil der Arbeit konzentriert sich auf die Erforschung der Umsetzung von Insassenidentifikation im Fahrzeug. Dabei werden verschiedene Technologien untersucht und eine Bestandsaufnahme der aktuellen Lösungen auf dem Markt vorgenommen. Der Schwerpunkt liegt dabei auf der Bewertung ihrer Vor- und Nachteile sowie ihrer Anwendbarkeit im Fahrzeugkontext. Die umfassende Recherche gibt einen fundierten Überblick über den Stand der Forschung und die vorhandenen Lösungen in diesem Bereich.

Im zweiten Teil der Arbeit geht es um die prototypische Umsetzung einer ausgewählten Methode. Die Auswahl erfolgt auf der Grundlage der im theoretischen Teil gewonnenen Erkenntnisse. Die Implementierung wird durchgeführt, um die praktische Anwendbarkeit und Wirksamkeit der ausgewählten Methode zu erproben. Die Wirksamkeit des Prototyps wird in umfangreichen Nutzerstudien untersucht.

Die Ergebnisse der theoretischen Forschung und der empirischen Studie werden in einem ganzheitlichen Kontext betrachtet. Mögliche Implikationen für die weitere Entwicklung und Anwendung der Insassenidentifikation in Fahrzeugen werden diskutiert. Die Arbeit schließt mit einem Ausblick auf mögliche Richtungen für weitere Forschungsprojekte auf diesem vielversprechenden Gebiet.
