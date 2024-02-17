# Einleitung

## Rahmung der Arbeit

Diese Arbeit stellt einen konzeptionellen Ansatz dar und verfolgt nicht das Ziel eines direkten Produktentwurfs. Die Abteilung On-Demand-Mobilität der BMW Group entwickelt kontinuierlich neue Konzepte, um die Zukunft der Mobilität aktiv zu gestalten. Ein wichtiger Beobachtungspunkt ist der rückläufige Trend des Fahrzeugbesitzes in Großstädten[@staedtevergleich], wobei alternative Lösungen wie Carsharing oder Fahrzeug-pools zunehmend an Bedeutung gewinnen[@carsharing_entlastet_umwelt_verkehr]. Das übergeordnete Ziel besteht darin, BMW optimal auf die Herausforderungen der zukünftigen Mobilität vorzubereiten, indem innovative Konzepte entworfen werden, die unter anderem das Teilen von Fahrzeugen erleichtern.

Im Zuge dieser Arbeit werden verschiedene Methoden der Identifikation außerhalb der Automobilindustrie beleuchtet. Ein Vergleich mit anderen Automobilherstellern dient der Kontextualisierung und ermöglicht die Ableitung von Best Practices. Die Präsentation von fünf ausgewählten Identifikationsmethoden sowie die prototypische Implementierung und Testung einer dieser Methoden bilden die Schwerpunkte dieser Untersuchung.

Die vorliegende Arbeit hebt somit nicht nur auf die Herausforderungen und Möglichkeiten der Identifikation im Fahrzeug ab, sondern integriert auch Erkenntnisse aus angrenzenden Branchen und den Erfahrungen anderer Automobilhersteller. Der Fokus liegt dabei darauf, innovative Lösungsstrategien zu entwickeln, um BMW als Vorreiter in der sich wandelnden Mobilitätslandschaft zu positionieren.

## Hintergrund und Kontext

Die Integration von Insassenidentifizierungssystemen in Fahrzeugen eröffnet zahlreiche Anwendungsmöglichkeiten für ein personalisiertes Fahrerlebnis. Diese Technologie ermöglicht es, die individuellen Bedürfnisse und Vorlieben der Fahrzeuginsassen zu erkennen und entsprechende Anpassungen vorzunehmen. 

Ein praktisches Beispiel hierfür ist die gemeinsame Nutzung eines Fahrzeugs durch eine vierköpfige Familie. Angenommen, die Mutter nimmt auf dem Beifahrersitz Platz – die Insassenidentifizierung könnte automatisch die Klimaautomatik auf ihre bevorzugte Temperatur einstellen. Sobald der Sohn das Steuer übernimmt, passt das System die Fahrzeugleistung an, um den Fahrstil eines jungen und weniger erfahrenen Fahrers zu berücksichtigen. Gleichzeitig kann das Unterhaltungssystem im Fond des Fahrzeugs auf die Interessen der Tochter auf der Rückbank abgestimmt werden. Bei Fahrten, bei denen nur die Eltern anwesend sind, könnte das System sogar automatisch die passende Musik auswählen, um eine angenehme Atmosphäre zu schaffen.

Ebenso bietet die Insassenidentifikation einen praktischen Vorteil für häufige Nutzer von Mietfahrzeugen. Steigt ein regelmäßiger Nutzer in ein beliebiges Pool-Fahrzeug ein, wird sofort sein individuelles Fahrerprofil aktiviert. Dadurch werden persönliche Einstellungen wie Sitzposition, gespeicherte Reiseziele und bevorzugte Klimaeinstellungen automatisch angepasst. 

Damit wird deutlich, dass die Insassenidentifikation nicht nur das Fahrerlebnis personalisiert, sondern auch den gesamten Fahrzeuginnenraum intelligent auf die Bedürfnisse der Insassen abstimmt. Dies geht über den Komfortaspekt hinaus und trägt zur Verbesserung der Fahrsicherheit und Effizienz bei. In einer Zeit, in der die Transformation der Mobilität im Mittelpunkt steht, könnten solche innovativen Ansätze einen wesentlichen Beitrag zur zukünftigen Gestaltung der Fahrzeugnutzung leisten.


## Problemstellung und Zielsetzung

Die Implementierung von Identifizierungsmethoden im Fahrzeugkontext geht zwangsläufig mit verschiedenen Herausforderungen einher. Ein zentraler Aspekt ist der Datenschutz, da die Verarbeitung personenbezogener Daten sensible Informationen betrifft. Die Gewährleistung einer sicheren und rechtskonformen Handhabung dieser Daten ist von essenzieller Bedeutung. Die Konsistenz der Identifizierungsergebnisse bildet ein weiteres Problemfeld, das insbesondere bei unterschiedlichen Umgebungsbedingungen oder variierenden Sprecherzuständen auftreten kann.

Nutzerfreundlichkeit stellt einen entscheidenden Faktor dar, da die Akzeptanz der Identifizierungsmethode maßgeblich von ihrer Einfachheit und Effizienz abhängt. Zu hoher Aufwand beim Trainieren oder Einrichten der Methode kann die Anwenderfreundlichkeit beeinträchtigen und den breiten Einsatz im Alltag behindern. Daher ist es von essenzieller Bedeutung, eine Identifizierungsmethode zu implementieren, die nicht nur innovativ ist, sondern auch eine Lösung für die genannten Probleme bietet.

Das Ziel liegt somit in der Entwicklung einer innovativen Identifizierungsmethode, die Datenschutzaspekte berücksichtigt, konsistente Ergebnisse liefert, nutzerfreundlich gestaltet ist und gleichzeitig einen minimalen Aufwand beim Trainieren und Einrichten erfordert. Eine solche Methode wäre nicht nur technologisch fortschrittlich, sondern auch praxisorientiert und im Einklang mit den Anforderungen an Datenschutz und Benutzerakzeptanz im Fahrzeugkontext.


## Definition: Identifizierung

Die Identifikation einer Person ist ein komplexer Prozess, der verschiedene Aspekte umfasst und insbesondere im Hinblick auf Datenschutzthemen von entscheidender Bedeutung ist. 

Identifizierung: „jemanden/etwas meist an bestimmten Merkmalen (wieder)erkennen.“[@definition_identifizierung]

Hierbei spielen Begriffe wie Authentisierung, Authentifizierung und Autorisierung eine Schlüsselrolle.

### Definition: Authentisierung

Im Rahmen einer Authentisierung erbringt eine Person einen Beweis dafür, dass sie ist, wer sie zu sein vorgibt. Im Alltag geschieht dies z. B. durch die Vorlage des Personalausweises. In der IT wird hierfür häufig ein Passwort in Kombination mit einem Benutzernamen genutzt.

### Definition: Authentifizierung

Authentifizierung ist der spezifischere Prozess der Überprüfung der Identität eines Subjekts, normalerweise durch die Verwendung von Anmeldeinformationen wie Benutzername und Passwort, Fingerabdruck, RFID-Karte oder andere biometrische Merkmale.

### Definition: Autorisierung

Autorisierung bezieht sich auf den Prozess der Festlegung von Berechtigungen oder Rechten für eine authentifizierte Entität. Nach erfolgreicher Authentifizierung legt die Autorisierung fest, welche Aktionen oder Ressourcen die authentifizierte Entität nutzen kann.[@definition_authentisierung_authentifizierung_autorisierung]

Diese Begrifflichkeiten spielen eine entscheidende Rolle bei der Insassenidentifizierung, insbesondere im Kontext von personenbezogenen Daten.

### Definition: Personenbezogene Daten

*"personenbezogene Daten" alle Informationen, die sich auf eine identifizierte oder identifizierbare natürliche Person […] beziehen; als identifizierbar wird eine natürliche Person angesehen, die direkt oder indirekt, insbesondere mittels Zuordnung zu einer Kennung wie einem Namen, zu einer Kennnummer, zu Standortdaten, zu einer Online-Kennung oder zu einem oder mehreren besonderen Merkmalen, die Ausdruck der physischen, physiologischen, genetischen, psychischen, wirtschaftlichen, kulturellen oder sozialen Identität dieser natürlichen Person sind, identifiziert werden kann;* (Art. 4 Nr. 1 DSGVO)


Bei der prototypischen Entwicklung der Insassenidentifizierung ist es von besonderer Bedeutung, personenbezogene Daten durch korrekte Authentisierung zu schützen und sicherzustellen, dass die Autorisierung angemessen erfolgt.


## Forschungsfrage

Mit dem obigen Wissenstand ist es jetzt möglich eine Forschungsfrage zu deferieren, welche mit der prototypischen Umsetzung beantwortet werden kann. 
Frage: Wie kann die Insassenidentifizierung unter Berücksichtigung von Datenschutz, Nutzbarkeit und Funktionalität mithilfe moderner Technologien prototypisch umgesetzt werden?

Die vorliegende Bachelorarbeit befasst sich mit der Entwicklung und Evaluation eines Prototyps für die Insassenidentifizierung in Fahrzeugen. Der Fokus liegt dabei auf der Integration moderner Technologien, wobei Aspekte wie Datenschutz, Nutzbarkeit und Funktionalität im Mittelpunkt stehen.

Die Forschungsmethodik umfasst die Implementierung eines Prototyps für die Insassenidentifizierung unter Verwendung zeitgemäßer Technologien. Die Evaluierung erfolgt durch Nutzerstudien, bei denen die Probanden die Effektivität, Sicherheit und Benutzerfreundlichkeit der Implementierung bewerten.

Der beigefügte Fragebogen im Anhang dient als Instrument zur systematischen Datenerhebung und Auswertung der Nutzertests.


## Aufbau der Arbeit

Die vorliegende Bachelorarbeit ist zweigeteilt und widmet sich der innovativen Insassenidentifizierung in Fahrzeugen. 

Der theoretische Teil der Arbeit fokussiert auf die Forschung zur Realisierung der Insassenidentifizierung unter Einbeziehung verschiedener Technologien sowie einer Bestandsaufnahme aktueller Lösungen auf dem Markt. Hier werden unterschiedliche Ansätze und Technologien zur Insassenidentifizierung beleuchtet. Dabei liegt der Schwerpunkt auf der Evaluierung ihrer Anwendbarkeit, Sicherheitsaspekte und Datenschutzbestimmungen. Eine umfassende Literaturrecherche ermöglicht einen fundierten Überblick über den Stand der Forschung und die bereits existierenden Lösungen in diesem Bereich.

Im zweiten Teil der Arbeit erfolgt die prototypische Umsetzung einer ausgewählten Methode. Die Auswahl erfolgt auf Basis der im theoretischen Teil gewonnenen Erkenntnisse. Die Implementierung wird durchgeführt, um die praktische Anwendbarkeit und Effektivität der ausgewählten Methode zu überprüfen. Die Wirksamkeit des Prototyps wird durch umfassende Nutzerstudien untersucht.

Die Ergebnisse der theoretischen Recherche und der empirischen Untersuchung werden in einem ganzheitlichen Kontext betrachtet. Mögliche Implikationen für die Weiterentwicklung und Anwendung der Insassenidentifizierung in Fahrzeugen werden diskutiert. Die Arbeit schließt mit einem Ausblick auf potenzielle Richtungen für weitere Forschungsvorhaben auf diesem vielversprechenden Gebiet.

