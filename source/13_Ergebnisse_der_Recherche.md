# Ergebnisse der Recherche

Im Folgenden werden die Ausgewählten Identifizierungstechnologien vorgestellt und untersucht. Ziel ist es, ein Verständnis für die vielfältigen Ansätze zur Insassenidentifizierung zu schaffen und diese zu evaluieren.

## Mobile App & Authentifizierungsportal

Mobile Apps haben in den letzten Jahren eine eindrucksvolle Entwicklung durchlaufen und sind zu einem festen Bestandteil des digitalen Alltags geworden. Allein in Deutschland lag der Anteil der Smartphone-Nutzer im Jahr 2022 bei 81,1 % und wird Prognosen zufolge bis 2027 auf 86,3 % steigen. [@statista_smartphone_anteil] Insbesondere die Verknüpfung von mobilen Apps mit dem Unterhaltungssektor hat zu innovativen Nutzererlebnissen geführt. Dieses Potential könnte auch für die Nutzung der Insassenidentifizierung von großer Bedeutung sein.

### Grundlagen

Im Kontext der Insassenidentifikation eröffnen mobile Apps eine innovative Perspektive, gestützt durch ihre vielfältigen Schnittstellenfunktionen. Die heutigen Mobilgeräte sind mit leistungsfähiger 5G-Technologie ausgestattet, die eine wichtige Rolle bei der Anbindung an das Backend spielt. Darüber hinaus ermöglichen weitere Kommunikationstechnologien wie Bluetooth oder WLAN die direkte Vernetzung mit dem Fahrzeug in unmittelbarer Nähe.

Im BMW-Kontext ist die **Headunit** das Hauptbedienelement für das Infotainmentsystem. Sie ist mit einem eingebetteten System, Display und Bedienelementen ausgestattet. Die Kommunikation mit anderen Steuergeräten im Fahrzeug erfolgt über diverse Bussysteme. Eine Verbindung zu externen Geräten wie Smartphones wird über Bluetooth oder WLAN hergestellt und die Anbindung an BMW-Backend-Server erfolgt über das Mobilfunknetz.

BMW stellt seinen Kunden bereits heute bewährte Apps wie die MyBMW [@mybmw_app] oder MINI App [@mini_app] zur Verfügung, mit denen Nutzer Einblicke in den Zustand ihres Fahrzeugs sowie der Fahrdaten erhalten können. Die Nutzung dieser etablierten Apps als Plattform für die Insassenerkennung könnte eine überzeugende Lösung sein, da die Nutzer bereits mit der Benutzeroberfläche und der Umgebung vertraut sind.

Durch die Einbeziehung von Smartphones als Identifikationsmittel entfällt die Notwendigkeit spezifisch verbauter Hardware. Moderne BMW-Fahrzeugmodelle sind bereits mit den notwendigen Komponenten über die Headunit ausgestattet, um eine Verbindung zu Mobilgeräten herzustellen.

Ein weiterer Vorteil ist die Adaptivität der mobilen Apps, die durch regelmäßige Updates neue Funktionen und Verbesserungen nahtlos integrieren können. Diese kontinuierliche Optimierung ermöglicht eine flexible Anpassung an veränderte Anforderungen und technologische Fortschritte im Bereich der Insassenidentifikation.

### Konzeptionierung

Für die Umsetzung der Insassenidentifikation mit Smartphones bieten sich verschiedene Ansätze. Wesentlich ist die Nutzung der bestehenden BMW ID, die jedoch so erweitert werden sollte, dass sie nicht nur fahrerspezifisch ist, sondern auch für andere Insassen des Fahrzeugs genutzt werden kann. Diese Erweiterung ermöglicht einen umfänglichen Datensatz über mögliche Insassen und schafft die Grundlage für personalisierte Einstellungen.

Ein möglicher Ansatz basiert auf einem effizienten Kommunikationsmechanismus mit Bluetooth Low Energy (BLE). Sobald die Insassen ihre Position im Fahrzeug einnehmen, wählen sie ihre individuelle Sitzposition über die Handy-App aus, bei der die Insassen bereits mit ihrer BMW ID angemeldet sind. Über die BLE-Schnittstelle erfährt das Fahrzeug, welcher Insasse sich auf welchem Platz befindet. Die Verbindung über BLE sorgt für eine energiesparende und zuverlässige Übertragung der Identifikationsdaten zwischen der App und dem Fahrzeug und gewährleistet eine nahtlose Integration in das bestehende System.

Eine zweite Variante setzt auf die Identifizierung mit einem QR-Code, was für die Insassen eine intuitive Methode ist. Beim Einsteigen in das Fahrzeugs wird ein Startbildschirm auf der Headunit angezeigt, der die Insassen auffordert, sich mit ihrem Konto anzumelden. Durch das Scannen des Codes öffnet sich ein Anmeldeportal, in dem sich die Insassen mit ihrer individuellen BMW ID anmelden können. Jeder Insasse kann dann seine Sitzposition auswählen. Die eingegebenen Informationen werden über ein Backend an das Fahrzeug übermittelt, so dass das Fahrzeug darüber informiert ist, welche Insassen auf welcher Position im Fahrzeug sitzen. Dieser Ansatz ist vorteilhaft für Nutzer, die nur ungern eine spezifische Anwendung herunterladen, ist aber auch wesentlich vom Mobilfunknetz abhängig und daher nicht immer in der Lage, eine Verbindung herzustellen, beispielsweise in Tiefgaragen.

Eine aussichtsreiche Strategie könnte darin bestehen, beide Ansätze zu kombinieren.

### Vorteile

Die Notwendigkeit, zusätzliche Hardware-Komponenten in das Fahrzeug einzubauen, wird durch die Implementierung des Handy-Ansatzes eliminiert. Dadurch entsteht eine kosteneffiziente Lösung, die den Umfang der Hardware im Fahrzeug minimiert und gleichzeitig eine zuverlässige Identifizierung der Insassen gewährleistet. Darüber hinaus ermöglichen Over-the-Air-Updates (OTA) die Aktualisierung und Erweiterung der Identifikationsfunktionalitäten. Diese Funktion ermöglicht die Aufrüstung der Insassenidentifikation in bestehenden Fahrzeugen, ohne dass das Fahrzeug physisch verändert werden muss. Dies erhöht die Anpassungsfähigkeit des Systems erheblich und trägt zu langfristiger Effizienz und Modernität bei.

Durch die Integration in die App ist es auch möglich, sitzplatzabhängige Infotainment-Einstellungen über die App vorzunehmen. So können zum Beispiel Fahrzeitinformationen, Musiksteuerung und Klimaeinstellungen bequem und persönlich über das Mobilgerät gesteuert werden.

Auch im Hinblick auf den Datenschutz ist dieser Ansatz ansprechend, da nur begrenzt Daten für die BMW ID benötigt werden. Im Vergleich zu anderen Identifizierungsmethoden, bei denen möglicherweise sensible persönliche Informationen, gesammelt werden könnten, bspw. Biometrie Daten, beschränkt sich die Identifizierung mittels Smartphone auf relevante und anonymisierte Daten.

### Herausforderungen

Die oben genannten Vorteile beschreiben nicht das gesamte Konstrukt, da der komplexe Ansatz eine Reihe von Herausforderungen mit sich bringt.

Eine zentrale Herausforderung besteht darin, die Position der Insassen zu erfassen, ohne dass diese selbst aktiv eingreifen müssen. Die Bereitschaft der Nutzer, diesen Zwischenschritt zu machen, wirft Fragen zur Nutzerakzeptanz und Freiwilligkeit auf. Es ist zu klären, ob die Insassen bereit sind, ihre Position aktiv anzugeben, um eine Identifizierung der Insassen zu ermöglichen.

Die Identifizierung wird durch die Dynamik während der Fahrt beeinflusst. Kurze Ausstiege, Sitzwechsel oder das Hinzukommen neuer Insassen können die Genauigkeit der Erkennung beeinträchtigen. Eine mögliche Lösung besteht darin, die Erkennung zu aktivieren, wenn sich jemand hinsetzt, mittels der Sensortechnologie, die bereits für Sicherheitsgurtwarnungen verwendet wird. 

Die Abhängigkeit vom Mobiltelefon wirft ebenfalls Fragen auf, insbesondere wenn die Insassen in das Fahrzeug einsteigen, ihre mobilen Geräte aber ausgeschaltet sind oder keine ausreichende Batterieleistung haben. Außerdem können Kinder oder andere Personen, die möglicherweise kein eigenes Mobilgerät besitzen, von dieser Identifizierungsmethode ausgeschlossen werden. 

Diese Szenarien erfordern alternative Lösungen, um eine zuverlässige Identifizierung der Insassen zu gewährleisten, unabhängig von der Verfügbarkeit und Funktionalität der mobilen Geräte.

## Gesichtserkennung

Im Rahmen der Marktanalyse in Kapitel 3.2 wird deutlich, dass die Gesichtserkennung bereits erfolgreich bei Subaru, eingesetzt wird – sowohl im Bereich der Sicherheit als auch zur Fahreridentifikation. Angesichts dieser Anwendung stellt sich die Frage, inwiefern die Gesichtserkennungstechnologie auf die weiteren Insassen erweitert werden kann. 

### Grundlagen

Die Gesichtserkennungstechnologie hat in den letzten Jahren erhebliche Fortschritte gemacht und wird zunehmend in verschiedenen Bereichen eingesetzt. Durch den Einsatz von ML und diverser Sensortechnologien wird unterstrichen, dass sehr präzise Ergebnisse erzielt werden können. [@face_segmentation] Bekannte Beispiele für die Integration dieser Technologie in den Alltag sind die Face ID Funktionen in Mobilgeräten von Apple wie dem iPhone, die die Zuverlässigkeit und Präzision der Gesichtserkennungstechnologie demonstrieren. [@apple_patent_faceid] Diese Technologie ermöglicht es iPhone-Nutzern, ihr Gerät zu entsperren, automatisch Passwörter einzugeben und sogar Zahlungen vorzunehmen.

Die Implementierung der kamerabasierten Gesichtserkennung hat sich, bezüglich des Rechenaufwandes als sehr effizient erwiesen. *"Mit einer single core Intel CPU mit 2,2 GHz [...] läuft DeepFace mit 0,33 Sekunden pro Bild, wenn man die Bilddekodierung, […] und die endgültige Klassifizierungsausgabe berücksichtigt."* Das oben erwähnte DeepFace ist ein von Facebook entwickelter Gesichtserkennungsalgorithmus, der Gesichter mit einer Genauigkeit von 97,35 % ($\pm$ 0,25 %) erkennen kann. Das ist fast so genau wie die menschliche Gesichtserkennung, die dem Paper zufolge bei über 97,5 % liegt. [@deepface]

Der Einsatz von ML beweist, dass die Erkennung von Gesichtern auf der Grundlage verschiedener Merkmale die Genauigkeit der Identifizierung verbessert. Dies kann auch angewendet werden, wenn mehrere Personen auf dem Bild zu sehen sind.

### Konzeptionierung

Bei der Erkennung der Insassen mittels Gesichtserkennungstechnologie im Fahrzeug wird eine zentrale Kamera in den Dachhimmel des Fahrzeugs integriert. Je nach verwendetem Algorithmus können auch mehrere Sensoren im Fahrzeug angebracht werden, um eine eindeutige Erkennung aller Sitze zu ermöglichen. Diese Technologie ermöglicht die Identifizierung von Insassen, unabhängig davon, ob eine bestehende BMW ID vorhanden ist oder nicht, da die Klassifizierung einer bereits erfassten Person nicht unbedingt mit einem Kundenkonto verknüpft sein muss.

Es ist erwähnenswert, dass BMW-Fahrzeuge, die mit autonomem Fahren ausgestattet sind, bereits über eine Gesichtserkennungstechnologie verfügen, die unter anderem dazu dient, die Aufmerksamkeit des Fahrers beim autonomen Fahren zu erkennen. Sie wird auch eingesetzt, um die Augenposition des Fahrers zu erfassen und einen Spurwechsel einzuleiten. [@autonomous_driving_gesichterkennung] Diese Technologie könnte möglicherweise in eine zentrale Kamera integriert werden, um verschiedene Anwendungen in einem System zu kombinieren.

Durch die Verwendung von vordefinierten Segmenten im Bild kann die genaue Positionierung der Insassen und die Bestimmung der Sitzposition ermöglicht werden. Wichtig ist, dass die zentrale Kamera jede beliebige Position im Fahrzeug erfassen kann, wobei es beu verschiedenen Fahrzeugbauarten zu Variationen kommen kann.

### Vorteile

Die Gesichtserkennungstechnologie hat gegenüber der Verwendung einer mobilen App eine Reihe von Vorteilen.

Die Insassen müssen keine manuellen Eingriffe vornehmen, sie müssen sich lediglich in das Fahrzeug setzen. Ebenso ist für die Gesichtserkennung keine Verknüpfung mit einem zuvor angelegten Insassenkonto wie der BMW ID erforderlich. Somit wird eine bedienerfreundliche Erfahrung ermöglicht, da die Insassen nach erfolgreicher Einrichtung ohne zusätzlichen Aufwand identifiziert werden können. Dieser Ansatz ist jedoch nur in einem Familienkontext mit einer begrenzten Anzahl an möglichen Insassen von Vorteil, da ansonsten die Fahrerprofile aus einem Backend, z.B. im Fall von Carsharing, übernommen werden müssen.

Ein weiterer Vorzug ist die Einfachheit und Schnelligkeit des Einrichtungsprozesses. Ein anschauliches Beispiel für die Effizienz ist die Einrichtung von Face ID auf einem iPhone, die in einer selbst getesteten Umgebung weniger als zwei Minuten dauerte. (TODO: Selbstexperiment... vllt. Quelle finden)

Dieses unkomplizierte und benutzerfreundliche Konzept trägt erheblich zur Attraktivität der Gesichtserkennungstechnologie für die Identifizierung von Fahrzeuginsassen bei.

### Herausforderungen

Es gibt jedoch viele Herausforderungen und offene Fragen bei der Gestaltung dieser Technologie im Fahrzeugkontext.
Ein wichtiger Aspekt ist der Datenschutz, denn biometrische Daten gehören zu den besonderen Kategorien nach DSGVO Art. 9 Abs. 1. Die Verordnung schreibt vor, dass diese Daten prinzipiell nicht verarbeitet werden dürfen. Dies wirft Bedenken hinsichtlich der Sicherheit und des Umgangs mit diesen Daten auf, da die Verarbeitung dieser Daten nur unter Rechtmäßigkeitsvoraussetzungen möglich ist.

Ein weiterer Aspekt sind die Lichtverhältnisse im Fahrzeug, bei denen herkömmliche Bilderkennungssysteme oft Schwierigkeiten haben. Moderne Sensortechnologien, wie beispielsweise bei Face ID, funktionieren auch bei völliger Dunkelheit sehr gut, erfordern aber besondere Vorkehrungen bei der Implementierung im Fahrzeugkontext, um optimale Ergebnisse zu erzielen. Eine solche Vorkehrung ist bespielsweise die Einhaltung des Abstands zwischen Sensor und Gesicht.

Die Positionierung der Kamera und der Sensoren in verschiedenen Fahrzeugformen ist ebenfalls ein entscheidender Faktor. Die Vielfalt der Fahrzeugdesigns erfordert eine flexible Anpassung der Sensorplatzierung, um eine optimale Erkennung von Gesichtern auf allen Sitzen zu gewährleisten. Es kann zu Verzerrungen aufgrund von Kamerawinkeln kommen, was den Einsatz von Bildverarbeitungsfiltern erfordert, um diese Herausforderung zu bewältigen.

Hinzu kommt der Aspekt des wechselnden Erscheinungsbildes der Insassen. Die Gesichtserkennungstechnologie muss in der Lage sein, Personen unabhängig von ihrer Kleidung, Frisur oder Brille zu erkennen.

## Stimmerkennung

Die Stimmerkennungstechnologie (oder auch Stimmenerkennung) ist zwar noch nicht weit verbreitet, findet aber bereits Anwendung bei Kundendienst-Hotlines und Sprachassistenten wie Alexa, wo sie zur Authentifizierung der Identität einer Person eingesetzt wird, bevor personenbezogene Daten freigegeben werden. [@azure_speaker_recognition] [@amazon_speaker_recognition] Diese Technologie hat das Potenzial, eine innovative Lösung zur Identifizierung von Fahrzeuginsassen zu bieten, durch die Nutzung individueller Stimmmerkmale. Angesichts dieser Informationen stellt sich die Frage, ob die Stimmerkennungstechnologie ihren Weg in die Fahrzeuginsassenidentifikation finden kann.

### Grundlagen

Vergleichbar mit der Gesichtserkennung, nutzt die Stimmerkennung biometrische Daten der Stimme, um mithilfe von ML verschiedene charakteristische Merkmale zu identifizieren. Dabei werden Mikrofone als primäre Erfassungsgeräte verwendet, um die Stimme zu erfassen und zu klassifizieren und so ein individuelles Stimmprofil zu erstellen, das auf einzigartigen Sprach- und Aussprachemerkmalen basiert.

In BMW-Fahrzeugen werden bereits Mikrofone für Freisprecheinrichtungen und für die Nutzung von Sprachassistenten eingesetzt. Diese bestehende Infrastruktur bietet eine solide Basis für die Integration einer Stimmerkennungstechnologie in den Fahrzeugkontext. Darüber hinaus wird die Position der Stimme bereits erkannt.

Die Stimmerkennung funktioniert am besten, wenn nur eine kleine Datenmenge Klassifiziert werden muss. Eine Studie zeigt, dass bei zwei Sprechern eine Genauigkeit von 98 % erreicht wurde. Allerdings ist zu vermerken, dass die Erkennung bei einer Datenbasis von 20 Sprechern eine Genauigkeit von 90,2 % erreicht. [@speaker_recognition_paper] Auch wenn diese Ergebnisse zunächst nicht sehr präzise erscheinen, wäre es durchaus aufschlussreich, eine mögliche Integration in das Fahrzeug zu untersuchen.

Der Einsatz der Stimmerkennungstechnologie zur Insassenidentifikation eröffnet somit die Möglichkeit, ein alternatives biometrisches Identifikationsverfahren im Fahrzeug zu etablieren.

### Konzeptionierung

Auch hier sind Parallelen zur Gesichtserkennung zu erkennen, wobei die Kamera durch ein- oder mehrere Mikrofone ersetzt wird. ML wird genutzt, um eine Stimmerkennung durchzuführen, die den Insassen identifiziert, der gerade spricht. Dazu muss das ML-Modell zunächst trainiert werden, was voraussetzt, dass die Insassen identifizierbare Stimmprofile erstellen, indem sie eine Reihe von Sätzen sprechen, die vom Modell aufgenommen und klassifiziert werden. Beim Carsharing kann das Training über eine mobile App mit Anbindung an ein Backend erfolgen, welches nach dem Training die Stimmprofile über alle Poolfahrzeuge synchronisiert. Im familiären Kontext kann das Training lokal im Fahrzeug stattfinden, was auch ohne die Verwendung einer BMW ID Synchronisierung erfolgen kann und somit keine Backend-Anbindung benötigt.

Zur Lokalisierung des Insassen, während der Stimmerkennung können verschiedene Methoden eingesetzt werden. Durch die Verwendung eines Mikrofons pro Sitzplatz kann beispielsweise ein Dezibel-Schwellenwert verwendet werden, um die lauteste Stimme zu isolieren, die gerade an diesem Platz gesprochen wird. Alternativ kann mit Hilfe der Mikrofontriangulation, bei der drei Mikrofone zum Einsatz kommen, die genaue Position der Stimme bestimmt werden. [@microphone_triangulation]

Diese innovative Herangehensweise eröffnet die Möglichkeit, die Stimmerkennung effektiv für die Insassenidentifizierung zu nutzen und dabei auf die bereits vorhandenen Infrastrukturen in modernen Fahrzeugen zurückzugreifen.

### Vorteile

Diese Technologie weist eine Reihe von Vorteilen auf, die ihre Attraktivität für die Fahrzeugintegration unterstreichen. Einer der herausragenden Vorteile ist, dass die Stimmerkennung, wie auch die Gesichtserkennung, keine aktive Beteiligung der Insassen erfordert. Die Insassen müssen keine manuellen Tätigkeiten unternehmen, sondern können sich ganz natürlich im Fahrzeug unterhalten, ohne ihre Identität aktiv bestätigen zu müssen.

Ein weiterer erheblicher Vorteil liegt in der kostengünstigeren Hardware im Vergleich zur Gesichtserkennung. Mikrofone, sind in der Regel wesentlich kosteneffizienter als Kameras und Sensoren, die bei der Gesichtserkennung zum Einsatz kommen. Diese Kostenersparnis könnte ein entscheidender Faktor bei der Implementierung dieser Identifikationsmethode sein. Die Flexibilität bei der Platzierung von Mikrofonen ist ein weiterer Vorteil. Töne sind leichter zu erfassen als Bilder, da Schallwellen Hindernissen umgehen können, während Licht und visuelle Signale im Allgemeinen einer geraden Linie folgen. Im Gegensatz zu Kameras lassen sich Mikrofone leicht und unauffällig im Fahrzeuginnenraum verstecken. Dies ermöglicht eine diskrete Integration, ohne das Design oder den Komfort zu beeinträchtigen.

Zusammenfassend bieten die genannten Vorteile der Stimmerkennungstechnologie eine vielversprechende Grundlage für ihre Anwendung als effektive und benutzerfreundliche Methode zur Insassenidentifikation in Fahrzeugen.

### Herausforderungen

Dennoch ergeben sich bei der Integration dieser Technologie in das Fahrzeug mehrere Komplikationen. Eines der Hauptprobleme betrifft den Schutz der Privatsphäre. Die Stimme eines Menschen wird als biometrisches Mittel auch zu den besonderen Kategorien eingestuft und ist unter Rechtmäßigkeitsvoraussetzungen zu verarbeiten.

Ein weiteres Szenario, das die Stimmerkennung vor eine Herausforderung stellt, kommt zur Geltung, wenn die Insassen schweigen oder der Fahrer sich allein im Fahrzeug befindet. Konträr dazu Situationen, in denen mehrere Insassen gleichzeitig sprechen. Hintergrundgeräusche, sei es durch Fahrgeräusche, Musik oder andere akustische Elemente, können die Stimmerkennung beeinträchtigen. Diese Situationen erfordern fortschrittliche Algorithmen, um Zuverlässigkeit und Präzision zu gewährleisten.

Verschiedene Stimmlagen, die durch Stimmungsschwankungen oder gesundheitsbedingte Veränderungen entstehen, sind ebenfalls zu berücksichtigen, sowie die Ähnlichkeit von Stimmen, insbesondere bei Geschwistern oder Personen mit ähnlichen stimmlichen Merkmalen. 

Insgesamt erfordert die erfolgreiche Integration eine ganzheitliche Berücksichtigung dieser Herausforderungen und eine kontinuierliche Weiterentwicklung der Technologie, um ihre Wirksamkeit in unterschiedlichen Szenarien zu gewährleisten.

## Ultrabreitband

TODO

## Kombinierung verschiedener Technologien

TODO: Replay Attacken bei Biometrische verfahren.
