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

## Konzeption der Architektur

TODO

![Architektur der Implementierung \label{Architektur}](source/diagrams/Architektur.png){ width=100% }

## Auswahl der Hardware

TODO

## Softwarekomponenten

TODO

### Frontend

TODO

### Backend

TODO

### Machine Learning Backend

TODO

### Incar Komponente

TODO

## Zusammensetzung und Schnittstellen

TODO
