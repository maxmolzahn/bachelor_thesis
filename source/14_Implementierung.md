# Implementierung

Das folgende Kapitel liefert einen Einblick in die implementierte Identifizierungslösung. Es ist zu beachten, dass die Umsetzung im Fahrzeugkontext einen anderen Ansatz als bei herkömmlichen Lösungen erfordert. Die Konzeptionierung der vorgestellten Lösungsansätze in der Recherche dient als Leitfaden für die anschließende Implementierung. Aufgrund der Vielschichtigkeit erfolgt die Ausarbeitung des Konzeptes im Verlauf der Implementierung.

## Auswahl der Identifizierungstechnologie

Als Implementierungsmethode wurde die Stimmerkennung gewählt, die speziell von der ODM-Abteilung von BMW gefordert wurde. Diese Entscheidung resultierte aus der Tatsache, dass dieser Ansatz bisher noch nicht im Fahrzeugkontext betrachtet wurde. Diese Technologie besitzt ein ungenutztes Potenzial für einen innovativen Ansatz im Fahrzeugbereich.

Die Stimmerkennungstechnologie, wie in Kapitel 3.3.3 beschrieben, präsentiert klare Vorzüge im Vergleich zu bestehenden Lösungen wie der Gesichtserkennung. Dies ist insbesondere auf die bereits im Fahrzeug vorhandenen Mikrofone zurückzuführen, was zu weniger Veränderungen in der Fahrzeugarchitektur führt.

Es ist von Interesse, die Zuverlässigkeit dieser Technologie in verschiedenen Situationen zu bewerten. Die beschriebenen Herausforderungen werden im Anschluss sorgfältig ausgewertet und analysiert.

## Anforderungen

Die Anforderungen an die Implementierung beruhen auf den ersten Forschungsergebnissen und sollen als Leitfaden für die weitere Entwicklung dienen. Die Implementierung ist als Proof of Concept ausgelegt und zielt nicht auf eine endgültige Lösung ab. Sie soll die Umsetzbarkeit der Stimmerkennung in einem Fahrzeugkontext demonstrieren und als Grundlage für weitere Entwicklungen dienen.

Einerseits sollte die Anwendung für den Einsatz im Fahrzeug optimiert sein, andererseits aber auch übertragbar sein, um in verschiedenen Umgebungen getestet werden zu können. Diese Vielseitigkeit ermöglicht eine ausführliche Evaluierung der Technologie in verschiedenen Szenarien.

Ein Hauptkriterium ist die Erkennung von bis zu fünf Personen und deren Sitzposition. Dieser Aspekt ist entscheidend für den praktischen Einsatz der Stimmerkennung im Fahrzeugumfeld. Darüber hinaus ist es wichtig auf Benutzerfreundlichkeit zu achten, um die Durchführung von Versuchen zu erleichtern.

Effiziente Ressourcennutzung ist ein weiteres Anforderungskriterium. Die Implementierung sollte in der Lage sein, vorhandene Ressourcen optimal zu nutzen, um eine Funktionalität bei begrenzter Rechenleistung im Fahrzeug sicherzustellen.

## Entwurf der Architektur

Es wurde eine vierstufige Architektur gewählt, bei der jede Komponente eine bestimmte Funktion erfüllt. Dieses Design ähnelt einer Microservices-Struktur, da es ihre Aufgaben auf verschiedene Systeme verteilt. Im Gegensatz zu einem Monolithen ist dies einfacher zu testen und einzusetzen. Auch die Skalierbarkeit einer Microservice-Architektur ist wesentlich simpler, da sie bei Bedarf angepasst werden kann. [@development_docker]

Im Fahrzeug selbst sind fünf Mikrofone installiert. Als Ersatz für die Headunit wird eine Incar-Komponente eingesetzt, die der begrenzten Rechenleistung des Systems entgegenkommt. Aus diesem Grund leitet die Incar-Komponente die Sprachdaten nur weiter und führt selbst keine Klassifizierung durch. 

Ein Backend-Server ist für die umfassende Verarbeitung aller Informationen zuständig. Die übrigen Komponenten kommunizieren ausschließlich mit dem Backend, wo sie dann verarbeitet und weitergeleitet werden.

Die direkte Nutzerschnittstelle ist eine Frontend Webapp, über die der Anwender sämtliche Funktionen im Backend ausführen kann. Hierzu zählt die Verwaltung von Sprechern, das Training des Modells und das Einsehen der Ergebnisse der Klassifizierung. 

Außerdem gibt es eine separate Backendkomponente, das so genannte GPU-Backend, das für das Training des Modells verwendet wird. Die Trennung ergibt sich aus den Kosten für eine grafikkartenbeschleunigte Instanz, die nur dann aktiviert wird, wenn das Training erforderlich ist. Die Klassifizierungen laufen über das normale Backend, da diese weniger rechenintensiv sind. Diese Struktur gewährleistet eine effiziente Nutzung der Ressourcen und eine Kostenoptimierung.

![Architektur der Implementierung \label{architektur_abbildung}](source/diagrams/Architektur.png){ width=100% }

Abbildung \ref{architektur_abbildung} veranschaulicht die beschriebene Architektur, die einer Sternarchitektur entspricht, was für die Abkapselung einzelner Komponenten vorteilhaft ist. So können Komponenten wie das GPU-Backend abgeschaltet werden, um Kosten zu sparen. In der Praxis würde das System auch dann weiterlaufen, wenn die Incar-Komponente nicht angeschlossen ist oder aufgrund eines schwachen Mobilfunknetzes ausfällt.

Für die Implementierung im Rahmen dieser Bachelorarbeit werden diese Komponenten aus verschiedenen Gründen mittels Docker containerisiert. Unter anderem überzeugt eine Abstraktionsschicht, bei der Code und Abhängigkeiten in einem Container zusammengeführt werden. Dies erleichtert die Entwicklung auf einer Plattform und die Bereitstellung in der Cloud, was die Produktivität erhöht. [@development_docker]

## Auswahl der Hardware

Die gewählte Hardware ermöglicht eine fahrzeugnahe Umsetzung im BMW-Kontext. Zum Einsatz kommen fünf Lavaliermikrofone der Firma AGPTEK mit einem 3,5mm Klinkenanschluss. Es sollten fünf identische Mikrofone verwendet werden, um mögliche Abweichungen bei den Ergebnissen zu vermeiden.

Der Einfachheit halber wurden externe Mikrofone gewählt, da der Anschluss an die bereits im Fahrzeug verbauten Mikrofone in Entwicklungsfahrzeugen nur unter bestimmten Bedingungen möglich ist. Die gewählte Lösung ist daher auch für Tests unter wechselnden Bedingungen besser geeignet, nämlich für Tests außerhalb des Fahrzeugs.

Die Incar-Komponente kann auf unterschiedlichen Systemen laufen. Für diese Implementierung wird ein Apple MacBook Pro 13 Zoll mit vier Thunderbolt 3 Anschlüssen und einem Klinkenanschluss der 2020er Generation verwendet. Ein Mikrofon wird direkt über eine 3,5-mm-Klinkenbuchse angeschlossen und die restlichen Mikrofone mittels eines Apple USB-C auf Klinkenadapters angeschlossen. Nach mehreren Fehlversuchen war dies die am besten funktionierende Lösung. Der ursprüngliche Ansatz mit fünf USB-A-Mikrofonen, die über einen USB-Hub angeschlossen waren, erwies sich als nicht erfolgreich, da die Mikrofone eines Herstellers die gleiche Geräte-ID im USB-Bus besitzen. Das bedeutet, dass nur die zuletzt angeschlossenen Mikrofone angesprochen werden konnten.

Eine Amazon Web Services (AWS) Elastic Compute Cloud (EC2) Instanz wird für die Backend- und Frontend-Komponenten eingesetzt. Diese wird durch BMW bereitgestellt, um eine flexible und skalierbare Lösung für die Durchführung von Tests im Fahrzeug zu bieten. Es wurde eine 'EC2-t4g.large' Instanz gewählt, die durch ihr Preis-Leistungs-Verhältnis bei allgemeinen Arbeitslasten überzeugt. Sie ist mit zwei virtuellen ARM-basierten Prozessorkernen und 8GiB Arbeitsspeicher ausgestattet. Diese Konfiguration ist für die Entwicklung und den mäßigen Einsatz zu Test- und Evaluierungszwecken gedacht und kann bei Bedarf skaliert werden. [@aws_ec2]

Das GPU-Backend läuft zunächst lokal auf einem GPU-beschleunigten Computer. Dieser verfügt über einen Intel i7 4790K, 16GiB RAM und eine Nvidia GTX 970 mit 4GiB Grafikspeicher. Durch die Verwendung der 1664 CUDA-Recheneinheiten [@nvidia_gtx_970] konnten die Trainingszeiten im Vergleich zur t4g-Instanz deutlich reduziert werden.

In Zukunft soll das ML-Backend auch auf einer AWS EC2-Instanz laufen, die GPU-beschleunigt ist. Das gesamte System wäre dann lediglich über einen Amazon Simple Storage Server (S3) Bucket [@aws_s3] mit dem Backend verknüpft, was die Speicherung von, in diesem Fall ML-Modelle, zwischen verschiedenen Komponenten vereinfacht.

## Softwarekomponenten

Die einzelnen Komponenten werden im Folgenden erläutert. Es wird unter anderem gezeigt, welche Anforderungen sie zu erfüllen haben und wie verschiedene Problemstellungen gelöst wurden. Durch die Verwendung von UML-Diagrammen und einzelnen Codeblöcken wird die Implementierung und bestimmte entscheidende Faktoren erläutert.

Der Vollständigkeit halber ist es wichtig zu erwähnen, dass Sockets für die Kommunikation verwendet werden. Die genauen Schnittstellen und Kommunikationsprozesse werden im Verlauf der Implementierung erläutert.

### Frontend

Die Frontend-Komponente ist zweigeteilt: Ein Nginx-Reverse-Proxy und eine React-App, die mit JavaScript gebaut wurde.

Für die Entwicklung der React-App wurden zunächst Mocks erstellt. Die Benutzeroberfläche wurde auf der Grundlage dieser Mocks entworfen. Es sei darauf hingewiesen, dass bei diesem Prozess keine besondere Rücksicht auf UX/UI genommen wurde, da das Hauptziel darin besteht, den Benutzer, in diesem Fall den Entwickler, beim Testen zu unterstützen und keine endgültige Lösung zu liefern.

Der Startbildschirm der Web-App besteht aus fünf Feldern, die die identifizierten Insassen und ihre Position anzeigen. Außerdem gibt es eine Navigationsleiste am oberen Rand des Bildschirms, die einen Menüreiter enthält, über den der Benutzer verschiedene Funktionen ausführen kann. Darüber hinaus gibt es eine Start-/Stop-Taste, mit der die Insassenerkennung im Fahrzeug aktiviert bzw. deaktiviert wird. Die Navigationsleiste ist persistent und kann auf jeder Seite der Web-App gefunden werden. Am unteren Rand des Bildschirms befindet sich eine Statusleiste, die den aktuellen Verbindungsstatus mit dem Backend, dem GPU-Backend und der Incar-Komponente anzeigt. Das aktuell ausgewählte ML-Modell wird ebenfalls angezeigt. Die Statusleiste ist auch persistent.

Über das Menü kann der Benutzer auf die Seite "View Speakers" zugreifen, auf der alle aktuell aufgezeichneten Sprecher oder, in Bezug auf ML, die Identifizierungsklassen für die Klassifizierung aufgelistet sind. Hier ist es möglich, Sprecher zu entfernen.

Ein weiterer Menüpunkt ist "Add Speaker", wo ein Sprecher hinzugefügt werden kann. Der Nutzer hat die Möglichkeit, einen beliebigen Artikel als Lesematerial zu wählen. Über eine Taste werden die Mikrofonberechtigungen vom Browser erteilt und die Aufnahme kann erfolgen. Im Anschluss kann die Aufzeichnung nochmals angehört und ein Sprechername eingegeben werden. Die Daten können nun an das Backend gesendet werden.

Der Ablauf der Aufzeichnung des Mikrofons ist in den folgenden Codeabschnitten dargestellt. Die MediaStream Recording API wird verwendet, um auf das Mikrofon des Geräts zuzugreifen. 

Die Methode `getUserMedia()` gibt ein Promise-Objekt zurück, das ein MediaStream-Objekt enthält, welches die angeforderten Mediengeräte darstellt, in diesem Fall den Mikrofon-Datenstrom. [@media_recording_api]

```javascript
const stream = await navigator.mediaDevices.getUserMedia({
    audio: true,
    video: false,
});
```

Die Aufzeichnung wird mit folgendem Codeausschnitt gestartet. Es wird ein MediaRecorder-Objekt erzeugt, das den Datenstrom des Mikrofons aufzeichnet. Die Audiodaten werden in einem Array gespeichert.


```javascript
const startRecording = async () => {
    // Erstellt eine neue Media-Recorder-Instanz mit dem Stream
    const media = new MediaRecorder(stream, { type: "audio/wav" });
    // Setzt die MediaRecorder-Instanz auf die Referenz
    mediaRecorder.current = media;
    // Startet den Aufnahmeprozess
    mediaRecorder.current.start();
    let localAudioChunks = [];
    // Fügt die Audiodaten in ein Array ein
    mediaRecorder.current.ondataavailable = (event) => {
        if (typeof event.data === "undefined") return;
        if (event.data.size === 0) return;
        localAudioChunks.push(event.data);
    };
    // Speichert das Array für die Audiodaten
    setAudioChunks(localAudioChunks);
};
```

Mit dem folgenden Code-Snippet wird die Aufnahme gestoppt und zur Verfügung gestellt. Die Audiodaten werden in ein Blob-Objekt konvertiert, das versendet werden kann, sowie in eine URL, die im Frontend abgespielt werden kann.

```javascript
const stopRecording = () => {
    setRecordingStatus("inactive");
    // Stoppt die Aufnahmeinstanz
    mediaRecorder.current.stop();
    mediaRecorder.current.onstop = () => {
        // Erzeugt ein Blob-Objekt aus den Audiodaten
        const audioBlob = new Blob(audioChunks, { type: "audio/wav" });
        setAudioBlob(audioBlob); // speichert das Blob-Objekt zum versenden
        // Erzeugt eine URL aus den Audiodaten zum abspielen
        const audioUrl = URL.createObjectURL(audioBlob);
        // Leert das Array für die nächsten Aufnahmen
        setAudioChunks([]);
    };
};
```

Die Seite "Train Model" ermöglicht es dem Benutzer, das Training auf dem GPU-Backend zu starten. Hier kann auch die Anzahl der Epochen für das Training festgelegt werden, wobei 100 Epochen voreingestellt sind. Ein Icon zeigt den Status des Trainingsprozesses an, bei erfolgreichem Training wird ein grüner Haken angezeigt und das neue Modell in der Statusleiste am unteren Rand angezeigt.

Einige Bildschirmaufnahmen des beschriebenen Frontends sind in Anhang 1 zu finden. Um das Frontend funktional im Browser darzustellen, wurde ein Reverse Proxy mit Nginx verwendet. Somit können ebenfalls Anfragen direkt an das Backend weitergeleitet werden. Außerdem wird der Datenverkehr über HTTPS umgeleitet, da einige Browser eine Mikrofonberechtigung nur über eine SSL-Terminierung zulassen.

Im Folgenden sind die wichtigsten Konfigurationseinstellungen für den Nginx-Reverse-Proxy aufgeführt:

```nginx
http {
    # Datenverkehr über HTTPS umleiten
    server {
        listen 80;
        server_name [...];
        return 301 https://[...]$request_uri;
    }
}
server {
    # HTTPS-Konfiguration
    listen 443 ssl;
    server_name [...];

    ssl_certificate [...];
    ssl_certificate_key [...];

    # Für die Kommunikation mit dem Backend
    client_max_body_size 40MB; # maximale Größe der Anfrage 
                               # kann bis zu 40MB sein

    location / {
        [...]
    }

    # API-Endpunkt für die Kommunikation mit dem Backend
    location /api {
        proxy_pass http://backend:5005;
        [...]
    }
}
```

### Backend

Das Backend wurde in Python 3.11.6 implementiert. Wie bereits erwähnt, ist das Backend für die Steuerung und Verarbeitung aller Anfragen der Komponenten zuständig. Python wurde als Sprache gewählt, da es ein schnelles prototypisches Erstellen und Entwickeln ermöglicht, was sich für ein solches 'Proof of Concept' anbietet. Außerdem bietet die Sprache umfangreiche Bibliotheken und wird häufig im Zusammenhang mit ML verwendet.

#### Zustand des Backends

Globale Variablen werden definiert, um den aktuellen Zustand des Systems zu verfolgen und um Fehler abzufangen, zum Beispiel wenn eine Komponente nicht läuft. Insbesondere zeigen die Booleans `recognition_status` an, ob die Identifizierung im Fahrzeug aktiv ist, `connected_incar` signalisiert eine bestehende Verbindung zur Incar-Komponente und `connected_ML` gibt an, ob eine Verbindung zum GPU-Backend besteht. 

Für die Verwaltung der Zustände der Sprecher, der gespeicherten Modelle und der identifizierten Sprecher, die im Frontend angezeigt werden, werden JSON-Objekte verwendet. Der Vorteil von JSON-Objekten ist, dass dieses Format plattformunabhängig ist und von jeder Komponente gelesen werden kann. Die Unterstützung von Arrays in JSON-Objekten ist ebenfalls nützlich, um pro Objekt unterschiedliche Daten zu speichern. Der folgende Auszug aus der Datei `speaker.json` zeigt ein Beispiel:

```json
[
    {
      "id": 0,
      "name": "Peter",
      "storing_date": "24-02-2024_13:21:34",
      "success": "true"
    },
    {
      "id": 1,
      "name": "Manfred",
      "storing_date": "24-02-2024_13:24:11",
      "success": "true"
    },
    [...]
]
```

Die Verwendung von JSON-Objekten ermöglicht eine standardisierte und plattformübergreifende Datenrepräsentation, die die Kompatibilität zwischen verschiedenen Systemkomponenten sicherstellt.

Eine Flask-Anwendung aus der Flask-Bibliothek wird zur Verarbeitung von REST-Anfragen verwendet, wobei Sockets für die Kommunikation zwischen den Komponenten genutzt werden. Die Socket-Kommunikation erfolgt über Namespaces, die in separaten Klassen definiert sind, um die Anfragen der verschiedenen Komponenten getrennt zu behandeln.

```python
class Webapp(Namespace):
    # Wird aufgerufen, wenn die Webapp eine Verbindung herstellt
    def on_connect(self):
        print('Webapp connected')
        get_status()
        get_speakers()
    
    # Wird aufgerufen, wenn die Webapp die Verbindung trennt
    def on_disconnect(self):
        print('Webapp disconnected')
```

Der obige Codeausschnitt verdeutlicht, wie eine Verbindung zur Webanwendung hergestellt wird. Diese Verbindung wird im Normalfall nicht unterbrochen. Um sicherzustellen, dass die Daten immer aktuell sind, wird sofort der aktuelle Status mit der Methode `get_status()` und der aktuelle Status der Sprecher mit `get_speakers()` übertragen. Diese Methoden werden auch aufgerufen, wenn sich die Daten ändern, zum Beispiel wenn neue Sprecher identifiziert, hinzugefügt oder entfernt werden oder wenn eine Verbindung zum GPU-Backend hergestellt wird.

#### Trainingsprozess

Nachdem alle Sprecherdaten erfasst und die Sprecherliste gepflegt wurde, kann das Modell trainiert werden.

Alle im `speakers.json` vermerkten Sprecher werden zusammen mit der Anzahl der Epochen über den Socket an das GPU-Backend gesendet und dort verarbeitet. Das Frontend wird informiert, dass die Daten gesendet wurden. Wenn das GPU-Backend das Training beendet hat, wird das Modell an das Backend zurückgesendet, wobei zu beachten ist, dass ein Modell in der Regel ca. 40 MB groß ist und daher in kleinere Pakete aufgeteilt und gesendet wird. Diese werden vom Backend mit einer ACK bzw. Nachricht bestätigt. Nachdem das letzte Paket gesendet wurde, erhält das Backend alle Informationen zu diesem Modell, die in einem JSON-Objekt gespeichert sind.

Wenn das Modell in der Validierung eine Genauigkeit von mehr als 95% und einen Verlust von weniger als 10% hat, wird es als neues Modell verwendet. In diesem Fall wird dem Frontend ebenfalls mitgeteilt, dass das Modell erfolgreich trainiert wurde und nun das neue Modell zur Verfügung steht.

#### Klassifikationsverfahren

Die Klassifizierung wird vom Backend angesteuert. Dies erfordert einen gut durchdachten Algorithmus, um die Sprecher korrekt zu identifizieren. Wenn im Frontend die "Start Recognition" Taste betätigt wird, sendet das Backend eine Nachricht an die Incar-Komponente und das aktuelle Modell wird mittels Keras geladen. Vorausgesetzt ist dass die Incar-Komponente verbunden ist. Ab diesem Zeitpunkt sendet die Incar-Komponente die Audiodaten an das Backend. Diese Audiodaten werden in einem temporären Verzeichnis gespeichert und indiziert. In Anhang 2 befindet sich ein UML-Sequenzdiagramm der Schnittstelle zwischen dem Backend und der Incar-Komponente. 

### GPU-Backend

Die GPU-beschleunigte Backend-Infrastruktur ist ebenfalls in Python implementiert und wird innerhalb der Implementierung als ML-Backend bezeichnet. Auf eine Containerisierung mittels Docker wurde bewusst verzichtet, um einen direkten Zugriff auf die GPU zu gewährleisten. Es sei jedoch darauf hingewiesen, dass die Nutzung der GPU in Verbindung mit Docker unter Umständen ebenfalls realisierbar wäre.

#### Vorbereitung der Trainingsdaten

Das Backend sendet alle Audiodaten, die trainiert werden sollen, und erstellt eine neue Verzeichnisstruktur für den Datensatz, in der alle gesendeten Audiodaten abgelegt werden. Mit Hilfe der "Pydub"-Bibliothek [@pydub] und des Werkzeugs "FFmpeg" [@ffmpeg] werden aus den Audiodaten AudioSegment-Objekte erzeugt, die eine nachträgliche Anpassung der Samplerate auf 16000 Hz ermöglicht. FFmpeg ist eine leistungsfähige Softwarelösung zur Bearbeitung von Multimediadaten. Es ermöglicht die Konvertierung von Dateiformaten, die Anpassung von Sampleraten und bietet eine Vielzahl von Funktionen zur Audio- und Videobearbeitung. In diesem Fall werden die Audioaufnahmen in Segmente mit einer Länge von jeweils einer Sekunde aufgeteilt. In der Praxis bedeutet dies, dass eine Audiodatei mit einer Länge von einer Minute in 60 einzelne Audiosegmente zerlegt wird. Diese einzelnen Segmente werden als WAV-Dateien in einem eigenen Verzeichnis pro Sprecher gespeichert.

Im nächsten Schritt werden Hintergrundgeräusche für das Training präpariert, indem sie mit den Trainingsdaten überblendet werden, um mögliche Störgeräusche bei der Erkennung zu minimieren. Bei diesen Hintergrundgeräuschen handelt es sich sowohl um weißes Rauschen als auch um Fahrgeräusche, die beispielsweise durch das Überfahren von Bodenwellen oder das Abspielen leiser Musik im Hintergrund entstehen. Mit der Methode `add_noise()` werden die Geräusche verhältnismäßig zu den Audiosegmenten hinzugefügt.
Die Integration von Hintergrundgeräuschen erhöht die Robustheit des Modells, da es dadurch besser in der Lage ist, relevante Sprachmerkmale auch unter schwierigen akustischen Bedingungen zu erkennen. Dieser Ansatz erweitert nicht nur den Trainingsdatensatz, sondern trägt auch dazu bei, die Varianz der Daten zu erhöhen und Overfitting zu vermeiden. Overfitting bedeutet, dass ein Modell während des Trainings zu stark an die spezifischen Merkmale und Muster der Trainingsdaten angepasst wird. Das Modell passt sich so genau an die Trainingsdaten an, dass es Schwierigkeiten hat, verallgemeinerbare und zuverlässige Vorhersagen für neue, noch nicht gesehene Daten zu machen. [@deep_learning_projects]

Der Datensatz wird nun für das Training vorbereitet, wobei 10% der Audiodaten für die Validierung reserviert werden, während der Rest für das eigentliche Training verwendet wird. Die Sprecher-IDs, die vom Backend zur Verfügung gestellt werden, werden für die Erstellung der Klassifikations-Labels verwendet.

Nach diesen Vorbereitungen ist der Datensatz einsatzbereit und kann für das Training verwendet werden.

#### Aufbau des Modells

Die Modellentwicklung erfolgt mit Hilfe der Keras-Bibliothek, einer Open-Source Deep-Learning-Bibliothek, die als High-Level-API offiziell in TensorFlow eingebunden ist. Keras ermöglicht es Entwicklern, neuronale Netze effizient zu entwerfen, zu trainieren und zu evaluieren. Das hier verwendete Modell wurde von Fadi Badine in der Keras-Dokumentation als Beispiel vorgestellt. [@keras_speaker_recognition]

Dieses spezifische Modell unterstützt die Klassifizierung von Sprechern auf der Grundlage der Frequenzbereichsdarstellung von Sprachaufnahmen, die durch die Verwendung der Fast Fourier Transform (FFT) gewonnen wird. Das Modell selbst wird durch ein eindimensionales Konvolutionsnetzwerk mit Residualverbindungen erzeugt, welches speziell auf die Anforderungen der Audio-Klassifikation zugeschnitten ist.

![Aufbau des ML-Modells \label{modell_abbildung}](source/diagrams/Modell_Uebersicht.png){ width=100% }

Die Abbildung \ref{modell_abbildung} wurde mit Hilfe der Visualisierungsbibliothek "visualkeras" erstellt und illustriert die Struktur des Modells, insbesondere den Aufbau der verschiedenen Schichten. Eine detailliertere Version des Modells ist in Anhang 3 zu finden.

Bei der Implementierung kommt ein Convolutional Neural Network (CNN) zum Einsatz, das auf den so genannten "residual blocks" basiert. Diese speziellen Blöcke wurden in Residual Networks (ResNet) eingeführt, um das Problem des verschwindenden Gradienten während des Trainings zu lösen. [@deep_learning_projects] Jeder Residualblock besteht aus einer Shortcut-Verbindung und mehreren Faltungsebenen. Die Shortcut-Verbindung ermöglicht die direkte Ausbreitung des Gradienten und erleichtert somit das Training tiefer Netzwerke.

Die Eingabeschicht besteht aus einem $1*8000$ Tensor, da für das Training die positiven Frequenzen der FFT verwendet werden, also $16000/2$. Die Architektur des Modells besteht aus mehreren Aufrufen der Methode `residual_block()`. Anfangs werden Residualblöcke mit verschiedenen Filtergrößen und Faltungsschichten verwendet. Nach den Residualblöcken wird eine Average Pooling Schicht mit einer Poolinggröße von 3 und einem Stride von 3 verwendet. Diese Schicht reduziert die räumliche Dimension der Daten, indem die Werte in jedem Pooling-Fenster gemittelt werden. Darauf folgt eine Flattening-Schicht, der die Ausgabe in einen eindimensionalen Vektor umwandelt, um die Daten für die nachfolgenden Dense-Schichten vorzubereiten.

Durch die Dense-Schichten ist es dem Modell möglich, komplexe Merkmale zu extrahieren, wo bis zu 256 Neuronen zum Einsatz kommen. Auf die Ausgabe dieser Schicht wird die Aktivierungsfunktion "relu" (Rectified Linear Unit) angewendet, um nichtlineare Aspekte in das Modell zu integrieren und die Fähigkeit des Netzes zur Mustererkennung zu verbessern. Schließlich wird eine DenseSchicht mit einer Softmax-Aktivierungsfunktion verwendet, um die Klassifikation durchzuführen. Diese wandelt die Ausgabe in eine Wahrscheinlichkeitsverteilung über die Klassen um, wodurch die Klasse mit der höchsten Wahrscheinlichkeit als Sprechervorhersage bestimmt wird. Diese Schichten arbeiten zusammen, um eine robuste und leistungsfähige Klassifikationsarchitektur zu bilden.

Das Modell verwendet den Adam-Optimierer, einen adaptiven Algorithmus, der die Effizienz des Trainings tiefer neuronaler Netze verbessert. Dieser passt die Lernraten auf der Grundlage vergangener Gradienten an. Die begleitende "Sparse Categorical Crossentropy"-Verlustfunktion (Loss) misst die Differenz zwischen den vorhergesagten und den tatsächlichen Klassenlabels. Zusammen ermöglichen diese Komponenten eine effiziente Optimierung und Training für Klassifikationsaufgaben.

Zum besseren Verständnis des oben beschriebenen Modells wurde das Buch “Deep Learning Projects Using TensorFlow 2” von Vinita Silaparasetty als Literaturhilfe herangezogen. [@deep_learning_projects]

#### Trainingsprozess

Für das Training des Datensatzes wird die Funktion `model.fit()` verwendet. Dabei wird ein "Early Stopping Callback" verwendet, um Rechenressourcen zu sparen und das Training frühzeitig zu beenden, wenn keine weiteren Verbesserungen zu erwarten sind. Gleichzeitig wird ein "Model Checkpoint"-Mechanismus eingesetzt, um das beste Modell während des Trainings zu speichern und so sicherzustellen, dass die leistungsfähigste Version erhalten bleibt. Die Anzahl der Epochen wird vom Benutzer im Frontend festgelegt und hier eingestellt, aber durch den "Early Stopping Callback" ist es möglich, dass weniger Epochen durchlaufen werden, wenn das Modell bereits konvergiert ist.

```python
[...]
earlystopping_cb = keras.callbacks.EarlyStopping(
    patience=10, restore_best_weights=True)
mdlcheckpoint_cb = keras.callbacks.ModelCheckpoint(
    f"models/[...]", monitor="val_acc", save_best_only=True)

history = model.fit(
    training,
    validation_data=validation,
    epochs=epochs,
    callbacks=[earlystopping_cb, mdlcheckpoint_cb],
)
[...]
```

Nach Abschluss des Trainings wird das Modell mit der Dateiendung `.keras` gespeichert und zusätzlich werden alle Informationen zum Modell im JSON-Format angehängt. Anschließend wird das Modell zusammen mit den Informationen an das Backend gesendet. Dieser Vorgang wurde bereits in Kapitel 4.5.2.2 beschrieben.

### Incar Komponente

Die Incar-Komponente, die sich im Fahrzeug befindet, ist ebenfalls in Python geschrieben. Hier soll der Ressourcenverbrauch geringgehalten werden.

#### Kalibrierung der Mikrofone

Beim Start der Komponente wird zunächst eine Liste aller angeschlossenen Ein- und Ausgabegeräte angezeigt. Diese werden mit Hilfe der „Sounddevice“-Bibliothek aufgelistet, die auch für die Aufzeichnung der Audiodaten verwendet wird. Aus dieser Liste wählt der Benutzer die Mikrofone aus, die für die Erkennung im Fahrzeug verwendet werden sollen. Im nächsten Schritt werden die Mikrofone auf ihre Position im Fahrzeug kalibriert. Dazu wird für jedes Mikrofon ein Dezibel-Graph angezeigt, der zur Identifizierung der Mikrofone verwendet werden kann. In der Praxis kann der Benutzer die Mikrofone berühren und den Pegel während des Kalibrierungsprozesses beobachten. Die Positionen setzen aus den in Tabelle \ref{positions_kuerzel} aufgeführten Kürzeln zusammen.

-----------------------------------------------
Positionskürzel         Position im Fahrzeug
------------------      ----------------------- 
`d`                     Fahrer

`p`                     Beifahrer

`bl`                    hinten links

`br`                    hinten rechts

`bm`                    hinten mittig

-----------------------------------------------
Table: Positionskürzel für die Kalibrierung der Mikrofone \label{positions_kuerzel}

Es ist möglich, eine beliebige Anzahl an Mikrofonen zu kalibrieren, da dies beim Testen nützlich ist, jedoch werden die abweichenden Positionskürzeln vom Backend nicht berücksichtigt. Bei erfolgreicher Kalibrierung wird eine sogenannte „device_map“ ausgegeben, die eine Geräte-ID mit ihrer Position verknüpft. Diese kann angegeben werden, wenn die Komponente startet, um den Kalibrierungsprozess zu überspringen, falls keine Änderungen vorliegen.

In Anhang 4 ist der Kalibrierungsprozess mit drei Mikrofone dargestellt.

#### Aufnahme und Verarbeitung der Audiodaten

Nach der Kalibrierung wird eine Verbindung zum Backend hergestellt und ein Thread erzeugt, der für die Audioaufnahme verantwortlich ist. Dieser Thread startet eine Endlosschleife, die darauf wartet, dass ein "recognition_event" als Ereignis ausgelöst wird, welches im unteren Codeabschnitt zu sehen ist. Dieses Ereignis wird vom Backend ausgelöst, wenn der Anwender die Sprecher Identifizierung aktiviert.

```python
def recognition():
    while True:
        recognition_event.wait()
        record(duration=2)
        global audio_file_index # laufende Nummer der Aufnahmen
        audio_file_index += 1
        sleep(3)
```

Bei der Aufnahme der Sprachdaten ist zu beachten, dass alle kalibrierten Mikrofone gleichzeitig aufgenommen werden. Dies ermöglicht die individuelle Isolierung von Stimmen anhand des Vergleichs der Dezibel Werte.

Für die Aufnahme der einzelnen Mikrofone werden weitere Aufnahme-Threads verwendet, die parallele Aufnahmen ermöglichen. Die Bibliothek "Sounddevice" stellt einen Datenstrom vom Mikrofon zur Verfügung und ein weiterer Thread speichert den Datenstrom in eine WAV-Datei. Nach der Aufnahme aller Mikrofone werden die gesicherten Daten per Socket an das Backend gesendet, zusammen mit einer fortlaufenden Nummer, die es ermöglicht, den Stand im Fahrzeug mit dem Stand im Backend zu vergleichen.

Die Aufzeichnung der Mikrofone erfolgt in festgelegten Zeitintervallen, welche in Kapitel 5.1.2 untersucht werden. Diese gestaffelte Aufzeichnung stellt sicher, dass das Backend genügend Zeit hat, die Audiodaten zu verarbeiten, bevor der nächste Zyklus von der Incar-Komponente gesendet wird. Eine Erweiterung besteht darin, den Zyklus dynamisch an die Verbindungsgeschwindigkeit des Mobilfunknetzes anzupassen. Dadurch kann eine Überlastung des Netzes vermieden werden.

## Zusammensetzung und Schnittstellen

Die implementierte Lösung besteht aus verschiedenen Komponenten, die mit dem Backend kommunizieren und teilweise gleichzeitig Daten austauschen. Die Abbildung \ref{adding_speakers_training} liefert einen Überblick über die Schritte, die notwendig sind, um Sprecher hinzuzufügen und das Modell zu trainieren. Sie veranschaulicht, wie die Komponenten miteinander interagieren und welche Schritte notwendig sind, um das System zu nutzen. Wie bereits erläutert, erfolgt die Kommunikation hauptsächlich über Sockets. 

![Schritte zum Hinzufügen von Sprechern und zum Trainieren des Modells \label{adding_speakers_training}](source/diagrams/Adding_speaker_training.png){ width=80% }

![Dokumentation der Schnittstellen \label{schnittstellen_abbildung}](source/diagrams/Schnittstellen.png){ width=80% }

Sockets ermöglichen eine Echtzeitkommunikation zwischen den einzelnen Komponenten, was insbesondere in Anwendungsfällen wie der Incar-Komponente von entscheidender Bedeutung ist. Dort ist eine schnelle und effiziente Datenübertragung mit geringer Latenz erforderlich. Durch die Möglichkeit der Full-Duplex-Kommunikation können Nachrichten in beide Richtungen gleichzeitig ausgetauscht werden, was die Leistungsfähigkeit und Reaktionsschnelligkeit der Gesamtsystemarchitektur erhöht. Ein weiterer Vorteil von Sockets ist, dass sie plattformunabhängig sind und somit zuverlässig in verschiedenen Komponenten eingesetzt werden können. [@sockets]

Die Abbildung \ref{schnittstellen_abbildung} zeigt die Schnittstellen zwischen den einzelnen Komponenten. In der Tabelle \ref{schnittstellen_tabelle} wird die Kommunikation zwischen den Komponenten detailliert beschrieben.

| Von     | Nach    | Nachricht    | Payload |
|---------|---------|--------------|---------|
| Frontend | Backend | `get_speakers` | - |
| Frontend | Backend | `add_speaker` | `{speaker_name, audio_blob}` |
| Frontend | Backend | `remove_speaker` | `speaker_ID` |
| Frontend | Backend | `start_training` | `epochs` |
| Frontend | Backend | `startStop` | - |
| Frontend | Backend | `get_status` | - |
| Backend | Frontend | `status` | `{conn_incar, conn_ML, rec_status, rec_speakers, current_model}` |
| Backend | Frontend | `speakers` | `speakers.json` |
| Backend | Frontend | `training_progress` | `progress` (in %) |
| Backend | Frontend | `speaker_added` | `speaker_name` |
| GPU-Backend | Backend | `model_chunk` | `{chuncks[], filename}` |
| GPU-Backend | Backend | `trained_model` | `modelinfo.json` |
| Backend | GPU-Backend | `initiat_training` | `{epochs, audio_files[]}` |
| Backend | GPU-Backend | `model_chunk_ack` | - |
| Incar   | Backend | `audio_file` | `{index, audio: {d, p, bl, bm, br}}` |
| Backend | Incar | `toggle_recognition` | `recognition_status` |

Table: Kommunikationsschnittstellen Beschreibung \label{schnittstellen_tabelle}
