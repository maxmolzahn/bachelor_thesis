# Implementierung

Das folgende Kapitel liefert einen Einblick in die implementierte Identifikationslösung. Zu beachten ist, dass die Umsetzung im Fahrzeugkontext einen anderen Ansatz als bei herkömmlichen Lösungen erfordert. Insbesondere ist die Rechenleistung der Headunit im Fahrzeug auf die für ihre vordefinierten Funktionen erforderliche Leistung beschränkt, und muss bei der Implementierung berücksichtigt werden.

Die Implementierung zeigt weitere Herausforderungen bei der Gestaltung einer fahrzeugorientierten Architektur auf und setzt einen gängigen Lösungsansatz um.

## Auswahl der Identifizierungstechnologie

Die für die Umsetzung gewählte Methode ist die Stimmerkennung, die speziell von der ODM-Abteilung von BMW gefordert wurde. Diese Entscheidung resultierte aus der Tatsache, dass diese Herangehensweise bisher noch nicht in einem Fahrzeugkontext betrachtet wurde. Die Technologie verfügt über ein ungenutztes Potenzial für einen innovativen Ansatz im Fahrzeugbereich.

Die Stimmerkennungstechnologie, wie in Kapitel 5.3 dargelegt, präsentiert klare Vorzüge im Vergleich zu bestehenden Lösungen wie der Gesichtserkennung. Dies ist insbesondere auf die bereits im Fahrzeug vorhandenen Mikrofone zurückzuführen, was zu weniger Veränderungen in der Fahrzeugarchitektur führt.

Außerdem ist es von Interesse, die Zuverlässigkeit dieser Technologie in verschiedenen Situationen zu bewerten. Die in Kapitel 5.3.4 beschriebenen Herausforderungen werden dann sorgfältig ausgewertet und analysiert.

## Anforderungen

Die Anforderungen an die Implementierung beruhen auf den ersten Forschungsergebnissen und sollen als Leitfaden für die Entwicklung dienen. Die Implementierung ist als ‚Proof of Concept‘ (engl. Wirksamkeitsnachweis) ausgelegt und zielt nicht auf eine endgültige Lösung ab. Sie soll die Umsetzbarkeit der Stimmerkennung in einem Fahrzeugkontext demonstrieren und als Grundlage für weitere Entwicklungen dienen.

Einerseits sollte die Anwendung für den Einsatz im Fahrzeug optimiert sein, andererseits aber auch übertragbar sein, um in verschiedenen Umgebungen getestet werden zu können. Diese Vielseitigkeit ermöglicht eine ausführliche Evaluierung der Technologie in verschiedenen Szenarien.

Ein Hauptkriterium ist die Erkennung von bis zu fünf Personen und deren Sitzposition. Dieser Aspekt ist entscheidend für den praktischen Einsatz der Stimmerkennung im Fahrzeugumfeld. Darüber hinaus wird ein hoher Wert auf Benutzerfreundlichkeit gelegt, um die Durchführung von Nutzerstudien zu erleichtern.

Effiziente Ressourcennutzung ist ein weiteres Anforderungskriterium. Die Implementierung sollte in der Lage sein, vorhandene Ressourcen optimal zu nutzen, um eine Funktionalität bei begrenzter Rechenleistung sicherzustellen.

## Entwurf der Architektur

Die gewählte Architektur basiert auf einer vierstufigen Architektur, bei der jede Komponente eine bestimmte Funktion erfüllt. Dieses Design ähnelt einer Microservices-Struktur, da es seine Aufgaben auf verschiedene Systeme verteilt. Im Gegensatz zu einem Monolithen ist dies einfacher zu testen und einzusetzen. Auch die Skalierbarkeit einer Microservice-Architektur ist wesentlich simpler, da sie bei Bedarf angepasst werden kann. [@development_docker]

Im Fahrzeug selbst sind fünf Mikrofone installiert. Als Ersatz für die Headunit wird eine Incar-Komponente eingesetzt, die der begrenzten Rechenleistung des Systems entgegenkommt. Aus diesem Grund leitet die Incar-Komponente die Sprachdaten nur weiter und führt selbst keine Inferenzen durch. Im Sinne des Datenschutzes wäre es besser, die Sprachdaten lokal im Fahrzeug zu verarbeiten, aber im Rahmen dieser Implementierung findet die Inferenz im Backend statt.

Ein Backend-Server ist für die umfassende Verarbeitung aller Informationen zuständig. Die übrigen Komponenten kommunizieren ausschließlich mit dem Backend, wo sie dann verarbeitet und weitergeleitet werden.

Die direkte Nutzerschnittstelle ist eine Frontend Webapp, über die der Anwender sämtliche Funktionen im Backend ausführen kann. Hierzu zählt die Verwaltung von Sprechern, das Training des Modells und das Einsehen der Ergebnisse der Klassifizierung. 

Außerdem gibt es eine separate Backendkomponente, das so genannte GPU-Backend, das für das Training des Modells verwendet wird. Die Trennung ergibt sich aus den Kosten für eine grafikkartenbeschleunigte Instanz, die nur dann aktiviert wird, wenn das Training erforderlich ist. Die Inferenzprozesse laufen über das normale Backend, da diese weniger rechenintensiv sind. Diese Struktur gewährleistet eine effiziente Nutzung der Ressourcen und eine Kostenoptimierung.

![Architektur der Implementierung \label{architektur_abbildung}](source/diagrams/Architektur.png){ width=100% }

Abbildung \ref{architektur_abbildung} veranschaulicht die beschriebene Architektur, die einer Sternarchitektur entspricht, was für die Abkapselung einzelner Komponenten vorteilhaft ist. So können Komponenten wie das GPU-Backend abgeschaltet werden, um Kosten zu sparen. Das System läuft auch dann weiter, wenn die Incar-Komponente nicht angeschlossen ist oder aufgrund eines schwachen Mobilfunknetzes ausfällt.

Für die Implementierung im Rahmen dieser Bachelorarbeit werden diese Komponenten aus verschiedenen Gründen dockerisiert. Unter anderem überzeugt eine Abstraktionsschicht, bei der Code und Abhängigkeiten in einem Container zusammengeführt werden. Dies erleichtert die Entwicklung auf einer Plattform und die Bereitstellung in der Cloud, was die Produktivität erhöht. [@development_docker]

## Auswahl der Hardware

Die gewählte Hardware ermöglicht eine fahrzeugnahe Umsetzung im BMW-Kontext. Zum Einsatz kommen fünf Lavaliermikrofone der Firma AGPTEK mit einem 3,5mm Klinkenanschluss. Es sollten fünf identische Mikrofone verwendet werden, um mögliche Abweichungen bei den Ergebnissen zu vermeiden.

Der Einfachheit halber wurden externe Mikrofone gewählt, da der Anschluss an die bereits im Fahrzeug verbauten Mikrofone in Entwicklungsfahrzeugen nur unter bestimmten Bedingungen möglich ist. Die gewählte Lösung ist daher auch für Tests unter anderen Bedingungen besser geeignet, nämlich für Tests außerhalb des Fahrzeugs.

Die Incar-Komponente kann auf unterschiedlichen Systemen laufen. Für diese Implementierung wird ein Apple MacBook Pro 13 Zoll mit vier Thunderbolt 3 Anschlüsse und einem Klinkenanschluss der 2020er Generation verwendet. Ein Mikrofon wird direkt über eine 3,5-mm-Klinkenbuchse angeschlossen und die restlichen Mikrofone mittels eines Apple USB-C auf Klinkenadapters angeschlossen. Nach vielen Fehlversuchen war dies die am besten funktionierende Lösung. Die erste Lösung mit fünf USB-A-Mikrofonen, die über einen USB-Hub angeschlossen waren, erwies sich als nicht erfolgreich, da die Mikrofone eines Herstellers die gleiche Geräte-ID im USB-Bus besitzen. Das bedeutet, dass nur die zuletzt angeschlossenen Mikrofone angesprochen werden konnten.

(TODO: Für weitere Entwicklungen könnte der Einsatz eines Raspberrypis zu einsatz kommen...)

Eine Amazon Web Services (AWS) Elastic Compute Cloud (EC2) Instanz wird für die Backend- und Frontend-Komponenten eingesetzt. Diese wird durch BMW bereitgestellt, um eine flexible und skalierbare Lösung für die Durchführung von Tests im Fahrzeug zu bieten. Es wurde eine 'EC2-t4g.large' Instanz gewählt, die durch ihr Preis-Leistungs-Verhältnis bei allgemeinen Arbeitslasten überzeugt. Sie ist mit zwei virtuellen ARM-basierten Prozessorkernen und 8GiB Arbeitsspeicher ausgestattet. Diese Konfiguration ist für die Entwicklung und den mäßigen Einsatz zu Test- und Evaluierungszwecken gedacht und kann bei Bedarf skaliert werden. [@aws_ec2]

Das GPU-Backend läuft zunächst lokal auf einem GPU-beschleunigten Intel-basierten Computer. Dieser verfügt über einen Intel i7 4790K, 16GiB RAM und eine Nvidia GTX 970 mit 4GiB Grafikspeicher. Durch die Verwendung der 1664 CUDA-Recheneinheiten [@nvidia_gtx_970] konnten die Trainingszeiten im Vergleich zur t4g-Instanz deutlich reduziert werden.
 (Diagramm zeigen) 
In Zukunft soll das ML-Backend auch auf einer AWS EC2-Instanz laufen, die GPU-beschleunigt ist. Das gesamte System wäre dann lediglich über einen Amazon Simple Storage Server (S3) Bucket [@aws_s3] mit dem Backend vernüpft, was die Speicherung von, in diesem Fall ML-Modelle, zwischen verschiedenen Komponenten vereinfacht.

## Softwarekomponenten

Die einzelnen Komponenten werden im Folgenden erläutert. Es wird unter anderem gezeigt, welche Anforderungen sie zu erfüllen haben und wie verschiedene Problemstellungen gelöst wurden. Durch die Verwendung von UML-Diagrammen und einzelnen Codeblöcken wird die Implementierung und bestimmte entscheidende Faktoren erläutert.

Der Vollständigkeit halber ist es wichtig zu wissen, dass Sockets für die Kommunikation verwendet werden. Die genauen Schnittstellen und Kommunikationsprozesse werden erst in Kapitel 6.6 erläutert.

### Frontend

Die Frontend-Komponente ist zweigeteilt: Ein Nginx-Reverse-Proxy und eine React-App, die mit JavaScript gebaut wurde.

Für die Entwicklung der React-App wurden zunächst Mocks erstellt. Die Benutzeroberfläche wurde auf der Grundlage dieser Mocks entworfen. Es sei darauf hingewiesen, dass bei diesem Prozess keine besondere Rücksicht auf UX/UI genommen wurde, da das Hauptziel darin besteht, den Benutzer, in diesem Fall den Entwickler, beim Testen zu unterstützen und keine endgültige Lösung zu liefern.

Der Startbildschirm der Web-App besteht aus fünf Feldern, die die identifizierten Insassen und ihre Position anzeigen. Außerdem gibt es eine Navigationsleiste am oberen Rand des Bildschirms, die einen Menüreiter enthält, über den der Benutzer verschiedene Funktionen ausführen kann. Darüber hinaus gibt es eine Start-/Stop-Taste, mit der die Insassenerkennung im Fahrzeug aktiviert bzw. deaktiviert wird. Die Navigationsleiste ist persistent und kann auf jeder Seite der Web-App gefunden werden. Am unteren Rand des Bildschirms befindet sich eine Statusleiste, die den aktuellen Verbindungsstatus mit dem Backend, dem GPU-Backend und der Incar anzeigt. Das aktuell ausgewählte ML-Modell wird ebenfalls angezeigt. Die Statusleiste ist ebenfalls persistent.

Über das Menü kann der Benutzer auf die Seite "View Speakers" zugreifen, auf der alle aktuell aufgezeichneten Sprecher oder, in Bezug auf ML, die Identifikationsklassen für die Inferenz aufgelistet sind. Hier ist es möglich, Sprecher zu entfernen.

Ein weiterer Menüpunkt ist "Add Speaker", wo ein Sprecher hinzugefügt werden kann. Der Nutzer hat die Möglichkeit, einen beliebigen Artikel als Lesematerial zu wählen. Über eine Taste werden die Mikrofonberechtigungen vom Browser erteilt und die Aufnahme kann erfolgen. Im Anschluss kann die Aufzeichnung nochmals angehört und ein Sprechername eingegeben werden. Die Daten können nun an das Backend gesendet werden.

Die Mikrofonberechtigungen werden mit dem folgenden Codeschnipsel erhalten. Die WebRTC-API wird für den Zugriff auf Mediengeräte verwendet. Die Methode "getUserMedia" gibt ein Promise-Objekt zurück, das ein MediaStream-Objekt enthält, das die angeforderten Mediengeräte darstellt, in diesem Fall den Mikrofon-Datenstrom.

```javascript
const streamData = await navigator.mediaDevices.getUserMedia({
    audio: true,
    video: false,
});
setStream(streamData);
```

Die Aufnahme wird gestartet mit folgenden Codeschnipsel:

```javascript
const startRecording = async () => {
    setRecordingStatus("recording");
    //create new Media recorder instance using the stream
    const media = new MediaRecorder(stream, { type: "audio/wav" });
    //set the MediaRecorder instance to the mediaRecorder ref
    mediaRecorder.current = media;
    //invokes the start method to start the recording process
    mediaRecorder.current.start();
    let localAudioChunks = [];
    mediaRecorder.current.ondataavailable = (event) => {
        if (typeof event.data === "undefined") return;
        if (event.data.size === 0) return;
        localAudioChunks.push(event.data);
    };
    setAudioChunks(localAudioChunks);
};
```

Die Aufnahme wird gestoppt und bereitgestellt mit folgenden Codeschnipsel:

```javascript
const stopRecording = () => {
    setRecordingStatus("inactive");
    //stops the recording instance
    mediaRecorder.current.stop();
    mediaRecorder.current.onstop = () => {
        //creates a blob file from the audiochunks data
        const audioBlob = new Blob(audioChunks, { type: "audio/wav" });
        setAudioBlob(audioBlob);
        //creates a playable URL from the blob file.
        const audioUrl = URL.createObjectURL(audioBlob);
        setAudio(audioUrl);
        setAudioChunks([]);
    };
};
```

(TODO Relevant???)

Die Seite "Train Model" ermöglicht es dem Benutzer, das Training auf dem GPU-Backend zu starten. Hier kann auch die Anzahl der Epochen für das Training festgelegt werden, wobei 100 Epochen voreingestellt sind. Ein Icon zeigt den Status des Trainingsprozesses an, bei erfolgreichem Training wird ein grüner Haken angezeigt und das neue Modell in der Statusleiste am unteren Rand angezeigt.

Die Bildschirmaufnahmen des beschriebenen Frontends sind im Anhang 1 zu finden. Um das Frontend funktional im Browser darzustellen, wurde ein Revrse Proxy mit Nginx verwendet. Somit können ebenfalls Anfragen direkt an das Backend weitergeleitet werden. Außerdem wird der Datenverkehr über HTTPS umgeleitet, da einige Browser eine Mikrofonberechtigung nur über eine SSL-Terminierung zulassen.

Im folgenden sind die Wichtigsten Konfigurationseinstellungen für den Nginx-Reverse-Proxy aufgeführt:

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

TODO

### Machine Learning Backend

TODO

### Incar Komponente

TODO

## Zusammensetzung und Schnittstellen

TODO
