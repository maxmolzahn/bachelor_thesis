# Grundlagen

In diesem Kapitel werden die Grundlagen für die Identifizierung von Insassen in Fahrzeugen erläutert. Dabei wird eine aktuelle Marktanalyse durchgeführt um den Stand der Technologie bei Fahrzeugen der BMW Group zu ermitteln, als auch ein Vergleich zu anderen OEMs zu ziehen.

## Definitionen und Begriffserklärungen

Zunächst werden einige zentrale Begriffe definiert, die im Kontext der Insassenidentifizierung von Bedeutung sind. Diese Begriffserklärungen dienen als Grundlage für das Verständnis der folgenden Kapitel.

### Identifizierung

Die Identifikation einer Person ist ein komplexer Prozess, der verschiedene Aspekte umfasst und insbesondere im Hinblick auf Datenschutz von entscheidender Bedeutung ist. 

Identifizierung: „jemanden/etwas meist an bestimmten Merkmalen (wieder)erkennen.“ [@definition_identifizierung]

Hierbei spielen Begriffe wie Authentisierung, Authentifizierung und Autorisierung eine Schlüsselrolle, welche auch häufig verwechselt werden.

### Authentisierung, Authentifizierung und Autorisierung

Im Rahmen einer Authentisierung erbringt eine Person einen Beweis dafür, dass sie ist, wer sie zu sein vorgibt. Im Alltag geschieht dies z. B. durch die Vorlage des Personalausweises. In der IT wird hierfür häufig ein Passwort in Kombination mit einem Benutzernamen genutzt.

Authentifizierung ist der spezifischere Prozess der Überprüfung der Identität eines Subjekts, normalerweise durch die Verwendung von Anmeldeinformationen wie Benutzername und Passwort, Fingerabdruck, RFID-Karte oder andere biometrische Merkmale.

Autorisierung bezieht sich auf den Prozess der Festlegung von Berechtigungen oder Rechten für eine authentifizierte Entität. Nach erfolgreicher Authentifizierung legt die Autorisierung fest, welche Aktionen oder Ressourcen die authentifizierte Entität nutzen kann. [@definition_authentisierung_authentifizierung_autorisierung]

### Personenbezogene Daten

*[…] "personenbezogene Daten" alle Informationen, die sich auf eine identifizierte oder identifizierbare natürliche Person […] beziehen; als identifizierbar wird eine natürliche Person angesehen, die direkt oder indirekt, insbesondere mittels Zuordnung zu einer Kennung wie einem Namen, zu einer Kennnummer, zu Standortdaten, zu einer Online-Kennung oder zu einem oder mehreren besonderen Merkmalen, die Ausdruck der physischen, physiologischen, genetischen, psychischen, wirtschaftlichen, kulturellen oder sozialen Identität dieser natürlichen Person sind, identifiziert werden kann;* (Art. 4 Nr. 1 DSGVO)

Bei der prototypischen Entwicklung der Insassenidentifizierung ist es von besonderer Bedeutung, personenbezogene Daten durch korrekte Authentisierung zu schützen und sicherzustellen, dass die Autorisierung angemessen erfolgt.

### Fahrerprofil

Fahrerprofile sind personalisierte Einstellungen, die auf die individuellen Präferenzen und Bedürfnisse des Fahrers zugeschnitten sind. Diese Einstellungen können verschiedene Aspekte des Fahrzeugs umfassen, wie z. B. die Sitzposition, die Klimaeinstellungen, die Radiosender oder die Navigationseinstellungen. Die Verwendung von Fahrerprofilen ermöglicht es, das Fahrerlebnis zu personalisieren und den Komfort zu erhöhen. [@BMW_i4_bordliteratur]

In den folgenden Kapiteln wird erläutert, wie verschiedene OEMs Fahrerprofile einbinden.

### Biometrische Identifikation

Biometrische Identifikation bezieht sich auf die Verwendung biometrischer Merkmale zur Überprüfung der Identität einer Person. Biometrische Merkmale können physische Eigenschaften wie Fingerabdrücke, Gesichtsmerkmale, Iris- oder Netzhautmuster, Handgeometrie oder Stimme umfassen. Die Verwendung biometrischer Merkmale zur Identifizierung bietet eine genaue und zuverlässige Methode zur Überprüfung der Identität einer Person.

### Schlüsselbasierte Identifikation

Bei der schlüsselbasierten Identifikation wird die Identität einer Person anhand eines physischen Schlüssels oder einer Karte überprüft. Dieser Ansatz ist in der Automobilindustrie weit verbreitet und ermöglicht eine einfache und effektive Identifizierung des Fahrers. Die Verwendung von Schlüsseln zur Identifizierung ist ein bewährtes Verfahren, das sich durch Zuverlässigkeit und Benutzerfreundlichkeit auszeichnet.

### Maschinelles Lernen

Maschinelles Lernen (ML) ist ein Teilgebiet der künstlichen Intelligenz, bei dem Computer anhand von Eingabedaten und einer Reihe von Regeln, die ihnen zur Verfügung gestellt werden, lernen und sich in einer bestimmten Aufgabe verbessern. Um dies zu ermöglichen, werden spezielle Algorithmen, die auf mathematischer Optimierung und Rechenstatistik basieren, in einem komplexen System kombiniert. [@application_of_ai]

Im Zusammenhang mit der Implementierung in Kapitel 5, wird eine nähere Erläuterung von ML gegeben.

## Identifizierungstechnologien bei Fahrzeugen der BMW Group

BMW-Kunden, die Fahrzeuge mit dem Betriebssystem "Operating System 7" oder einer neueren Version besitzen, haben Zugriff auf die Funktion der Fahrerprofile, die sogenannten BMW IDs. [@BMW_ID_FAQ_1] Diese Funktion ermöglicht es dem Fahrer, verschiedene Einstellungen zu synchronisieren, um ein individuelles Fahrerlebnis zu schaffen. Zu den synchronisierbaren Einstellungen gehören:

* Profilbild
* Navigation (letzte Ziele, Heimatadresse, Karteneinstellungen)
* Medien (gespeicherte Radiosender)
* iDrive (Konfiguration des Hauptmenüs, Sprache, Einheiten)
* Sprachassistent (Vorschläge, Aktivierungswort)
* Außenbelichtung
* Sitzposition und Klimaeinstellungen
* Datenschutz Einstellungen. [@BMW_i4_bordliteratur]

Diese Funktionalität bietet Fahrern die Möglichkeit, das Fahrzeug an die persönlichen Vorlieben anzupassen, selbst wenn mehrere Nutzer das Fahrzeug teilen. Für das „Operating System 7“ können bis zu drei Fahrerprofile gespeichert werden. Im neueren „Operating System 8“ kann ein Hauptnutzer und bis zu sechs zusätzliche Mitnutzer ihre individuellen Fahrerprofile speichern. [@BMW_ID_FAQ_2]

Trotz der Vorteile dieser Funktion stellt sich die Frage nach der Aktivierung einer BMW ID im Fahrzeug, insbesondere bezüglich der Datensicherheit, da es sich dabei durchaus um personenbezogene Daten handeln kann. Es stellt sich auch die Frage, ob die BMW ID auf den Fahrer beschränkt ist oder ob auch andere Insassen diese Funktion nutzen können.

### Identifizierungsmethoden für den Fahrer

Die Aktivierung von Fahrerprofilen erfolgt durch eine Kopplung mit dem Fahrzeugschlüssel. Sobald die BMW ID mit einem spezifischen Fahrzeugschlüssel verknüpft ist, wird bei Verwendung dieses Schlüssels das entsprechende Fahrerprofil automatisch ausgewählt. Diese Verknüpfung ermöglicht ein personalisiertes Fahrerlebnis, ohne dass der Fahrer manuell eingreifen muss.

Eine weitere Möglichkeit Fahrerprofile zu aktivieren und zu ändern, während eine andere Person das Fahrzeug benutzt, bietet das iDrive-System. Dieser Vorgang erfordert jedoch eine zusätzliche Sicherheitsebene, da das iDrive-System eine PIN-Eingabe für Profiländerungen anfordert. Diese Sicherheitsmaßnahme stellt sicher, dass nur autorisierte Benutzer Fahrerprofile ändern und auf persönliche Einstellungen zugreifen können. [@BMW_i4_bordliteratur]

Trotz der sorgfältigen Konzeption dieses Systems gibt es diverse Herausforderungen, insbesondere wenn das Fahrzeug im Rahmen von Carsharing oder in familiärer Umgebung gemeinsam genutzt wird. In diesen Fällen kann die nahtlose Identifizierung und automatische Auswahl des Fahrerprofils beeinträchtigt werden.

### Identifizierungsmethoden für die Insassen

Die BMW ID bietet ein personalisiertes Fahrerlebnis für den Fahrer. Allerdings gibt es eine Einschränkung bei der Authentifizierung von weiteren Insassen. Im aktuellen System ist es nicht möglich, dass sich Beifahrer oder weitere Insassen mit ihren individuellen Identitäten authentifizieren.

Die Authentifizierung bleibt primär auf den Fahrer beschränkt, der das Fahrzeug mit seinem gekoppelten Schlüssel entsperrt. Dies bedeutet, dass die personalisierten Einstellungen und Präferenzen nur auf den Fahrer zugeschnitten sind, der das Fahrzeug aktiv nutzt. Für Mitfahrer, die in das Fahrzeug einsteigen, besteht gegenwärtig keine Möglichkeit, eigene Profile zu aktivieren oder spezifische Einstellungen vorzunehmen.

Diese Beschränkung kann in bestimmten Szenarien als herausfordernd wahrgenommen werden, besonders wenn mehrere Fahrzeuginsassen unterschiedliche Präferenzen haben. Die fortlaufende Entwicklung der Fahrzeugtechnologie könnte jedoch zukünftig neue Möglichkeiten für erweiterte Authentifizierungsfunktionen auch für Mitfahrer hervorbringen.

### Bewertung der vorhandenen Identifizierungsmethoden

Das Konzept der Fahrerprofile in BMW Fahrzeugen mit einem bekannten Fahrerkreis und deren Verknüpfung mit dem Fahrzeugschlüssel ist eine gut durchdachte und effektive Lösung. Die Verknüpfung mit einem physischen Schlüssel sorgt für eine automatische Authentifizierung des Fahrers und damit für ein individuelles Fahrerlebnis. Dies ist besonders vorteilhaft für Familien oder begrenzte Gruppen von Nutzern, die regelmäßig dasselbe Fahrzeug verwenden.

Jedoch ergibt sich eine gewisse Einschränkung dieses Konzepts, wenn das Fahrzeug ausgeliehen wird, insbesondere bei Carsharing-Modellen, bei denen verschiedene Fahrer unterschiedliche Fahrzeuge nutzen wollen. Das vorliegende Konzept ist in solchen Szenarien weniger flexibel und zu Komplikationen führen.

Die nicht gegebene Möglichkeit für weitere Fahrzeuginsassen, sich zu authentifizieren, ist eine klare Limitierung. Bei der Nutzung durch verschiedene Personen bleibt das System primär auf den individuellen Fahrer beschränkt, der in das Fahrzeug mit seinem persönlichen Schlüssel einsteigt.

### Fazit

Insgesamt zeigt sich, dass die BMW ID mit etablierten Fahrern und Schlüsselkopplung für bestimmte Nutzungsszenarien effektiv ist. Sie bietet ein personalisiertes und komfortables Fahrerlebnis. Allerdings können alternative Lösungen oder Anpassungen des Konzepts für die Insassenidentifikation in Sonderfälle wie Carsharing erforderlich sein, wo Flexibilität gefragt ist. Die Möglichkeit, auch Mitfahrer zu authentifizieren und ihre individuellen Einstellungen zu berücksichtigen, könnte das Fahrerlebnis weiter verbessern und künftige Anforderungen an die Fahrzeugpersonalisierung erfüllen.


## Identifizierungstechnologien bei Fahrzeugen anderer Automobilhersteller

Die Automobilindustrie hat in den letzten Jahren rasante Fortschritte bei innovativen Technologien gemacht. Diese haben das Ziel das Fahrerlebnis weiter verbessern. Neue Technologien spielen eine entscheidende Rolle bei der personalisierten Fahrzeugnutzung und tragen zu mehr Komfort und Sicherheit bei. Dieses Kapitel wirft einen Blick auf Identifikationstechnologien in Fahrzeugen anderer Hersteller und konzentriert sich dabei auf den Vergleich zwischen den OEMs und die zukünftige Bedeutung der Insassenidentifikation.

Die Automobilindustrie ist von Natur aus wettbewerbsorientiert, und die Rivalität zwischen den OEMs hat zu ständigen Innovationen geführt. Ein wichtiger Einflussfaktor in der Automobilindustrie ist der wachsende Einfluss der asiatischen OEMs. Unternehmen aus Asien, insbesondere aus China, sind zu wichtigen Akteuren auf dem Weltmarkt geworden. Ihr Engagement für innovative Fahrzeugtechnologien hat die Dynamik der Branche erheblich beeinflusst und trägt dazu bei, neue Standards für fortschrittliche Fahrzeugtechnologien zu setzen. [@automobilindustrie_und_mobilität_in_china]

### Auswertung der Recherche

Die Konkurrenz zwischen Automobilherstellern zwingt Entwickler neue Technologien voranzubringen, um an der Marktspitze mithalten zu können. In diesem Zusammenhang ist es von großem Interesse, die Ansätze verschiedener OEMs zu untersuchen und zu vergleichen. Diese Analyse verdeutlicht die Betrachtung von Insassenidentifizierungstechnologien und die wachsende Bedeutung dieses Bereichs für die Zukunft der Automobilbranche. Sie unterstreicht die Notwendigkeit weiterer Forschung zur Fahrzeugpersonalisierung.

**Tesla**, ein Pionier der Elektromobilität, bietet eine ähnliche Funktionalität wie BMW durch die Verknüpfung von Fahrerprofilen über einen physischen Schlüssel, in diesem Fall eine Schlüsselkarte. Allerdings bleibt die Identifikation auf den Fahrer beschränkt, ohne zusätzliche Insassenerkennung. [@tesla_recherche]

**Volkswagen** und dessen Tochterunternehmen setzten ebenfalls auf Fahrerprofile, um bestimmte Funktionen zu synchronisieren. (TODO AUDI auch Fingerabdrucksensor?)

**Mercedes-Benz** integriert in bestimmten Fahrzeugmodellen einen Fingerabdrucksensor, der Funktionen des Infotainmentsystems freischaltet. Diese in der Automobilbranche einzigartige Technologie unterstreicht die Bemühungen um die Entwicklung von Identifizierungstechnologien, die über die traditionellen Ansätze hinausgehen. [@mercedes_recherche]

**Subaru** setzt auf ein Gesichtserkennungssystem, jedoch ist die Funktionalität auf den Fahrer begrenzt. Mit der Gesichtserkennung können Fahrerprofile freigeschaltet werden und gleichzeitig auch Sicherheitssysteme wie Aufmerksamkeitswarner verwendet werden. [@subaru_recherche] 

Die Tech-Giganten **Apple** und **Amazon** betreten die Automobilbranche mit innovativen Ansätzen zur Insassenidentifizierung. Apple patentierte "Comfort Profiles", das auf die Erkennung von Personen im Fahrzeug abzielt, auch mittels kamera-basierter Technologien. Die Absicht des Unternehmens, Fahrerprofile für das autonome Fahren zu schaffen, unterstreicht die Beteiligung der Identifizierung an der künftigen Entwicklung autonomer Fahrzeuge. [@apple_patent]

Auch **Amazon** verfolgt einen innovativen Ansatz mit einem Patent zur Erstellung von Fahrgastprofilen, das verschiedene Sensoren, einschließlich der Fingerabdruckerkennung, integriert. Dies unterstreicht das Engagement der Tech-Giganten, die traditionelle Automobilindustrie mit fortschrittlichen Technologien zu verändern. [@amazon_patent]

(TODO: mehr Recherche über Chinesische Autobauer: BYD, Geekly und zsl. vllt Hyundai und Toyota)

Insgesamt verdeutlichen diese unterschiedlichen Ansätze den intensiven Wettbewerb und die Vielfalt bei der Integration von Identifikationstechnologien zwischen verschiedenen traditionellen Automobilherstellern und Tech-Giganten.

### Bewertung und Vergleich

Die Evaluierung der verschiedenen Insassenidentifizierungstechnologien in der Automobilbranche verdeutlicht eine Vielzahl von Ansätzen, um die Fahrzeugpersonalisierung zu verbessern. Die Verwendung unterschiedlicher Technologien bietet sowohl Chancen als auch Herausforderungen, die es zu berücksichtigen gilt.

Eine gemeinsame Charakteristik, die sich durch die untersuchten Insassenidentifizierungstechnologien zieht, ist die Fokussierung auf den Fahrer als Hauptnutzer. Sowohl die schlüsselbasierte Identifizierung als auch biometrische Technologien wie Fingerabdrucksensoren und Gesichtserkennung konzentrieren sich primär auf die Authentifizierung des Fahrers. Diese Ausrichtung spiegelt die aktuelle Praxis wider, bei der die personalisierte Erfahrung hauptsächlich auf die Bedürfnisse und Präferenzen des Fahrers basiert.

 * Die **schlüsselbasierte Identifizierung** stellt eine bewährte und effektive Methode dar, welche einfach und effektiv ist. Die Identifizierung ist auf den Fahrer beschränkt und kann eine Herausforderung darstellen, wenn das Fahrzeug mit mehreren Personen geteilt wird.
 * **Biometrische Technologien** wie Fingerabdrucksensoren und Gesichtserkennung repräsentieren eine fortschrittlichere und vielseitigere Methode der Insassenidentifizierung. Im Gegensatz zur schlüsselbasierten Identifizierung können biometrische Technologien auf mehrere Insassen erweitert werden, was eine umfassendere Personalisierung ermöglicht. Trotz ihrer Effektivität und Präzision sind jedoch technische Herausforderungen zu überwinden. Unterschiedliche Lichtverhältnisse können die Leistung beeinträchtigen, und die nahtlose Integration solcher Technologien in Fahrzeuge erfordert sorgfältige Planung und Umsetzung.

Die aktuelle Ausrichtung auf den Fahrer als zentrale Person zur Identifizierung verdeutlicht die Notwendigkeit, zukünftige Entwicklungen in der Insassenidentifizierungstechnologie dahingehend zu erforschen, damit auch die Bedürfnisse und Präferenzen der weiteren Insassen effektiver berücksichtigt werden können. Eine Weiterentwicklung dieser Technologien könnte dazu beitragen, die Personalisierung im Fahrzeug auf ein neues Niveau zu heben.

