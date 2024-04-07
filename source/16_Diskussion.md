# Diskussion und Ausblick

Im Rahmen der folgenden Diskussion soll erörtert werden, ob die Stimmerkennung als geeignete Methode zur Identifizierung von Fahrzeuginsassen eingesetzt werden kann. Dabei wird die Forschungsfrage beantwortet und ein Ausblick gegeben.

## Akzeptanz der Nutzer

Die Akzeptanz der Stimmerkennung wird stark von Datenschutzbedenken beeinflusst. Die Nutzer sind zunehmend besorgt über die mögliche Verletzung ihrer Privatsphäre und die unsachgemäße Verarbeitung persönlicher Daten durch solche Systeme. Ein wichtiger Punkt ist das Bewusstsein der Nutzer, dass das System permanent aktiv ist und ihre Stimme aufzeichnet. Dies kann zu einem verstärkten Unsicherheitsgefühl führen, da das Gefühl einer ständigen Überwachung entsteht. Im Gegensatz dazu bieten Spracherkennungssysteme wie Alexa oder Siri ein gewisses Maß an Kontrolle, da sie nur aktiviert werden, wenn ein bestimmtes Schlüsselwort verwendet wird.

Darüber hinaus ist es wichtig zu betonen, dass Nutzer nur bereit sind, eine Stimmerkennung zu verwenden, wenn es einen erheblichen Mehrwert bietet. Wenn der Trainingsprozess zu langwierig ist oder der resultierende Nutzen zu gering erscheint, werden die meisten Nutzer voraussichtlich auf die Einrichtung des Systems verzichten. Der Aufwand, den die Nutzer in den Trainingsprozess investieren müssen, muss in einem angemessenen Verhältnis zu dem entstehenden Mehrwert liegen. Wird dieses Gleichgewicht nicht erreicht, kann dies zu einer geringen Akzeptanz und Nutzung des Systems führen, selbst wenn Datenschutzbedenken ausgeräumt sind.

In der Zusammenfassung ist zu erkennen, dass die Akzeptanz und Nutzung von Stimmerkennung stark von verschiedenen Faktoren abhängig ist. Einerseits sind Datenschutzbedenken ein zentrales Anliegen der Nutzer und erfordern klare Richtlinien und Transparenz. Andererseits ist es entscheidend, dass sich die weitere Forschung auf die Schaffung eines signifikanten Mehrwerts für die Nutzer konzentriert, um die Akzeptanz zu fördern. Die derzeitige Umsetzung der Insassenidentifizierung mittels Stimmerkennung mag nicht die optimale Lösung darstellen, bietet aber als Proof of Concept Möglichkeiten für weitere Untersuchungen.

## Einsatzgebiete

Im Folgenden werden die beiden wichtigsten Einsatzgebiete, die in der Einleitung beschrieben wurden, sowie mögliche neue Einsatzgebiete, die sich im Laufe der Arbeiten ergeben haben, hinsichtlich ihrer Umsetzung und ihrer Ergebnisse bewertet.

Wie die Versuche gezeigt haben, ist die Umsetzung der Insassenidentifizierung mittels Stimmerkennung in einem Familienfahrzeug vorteilhaft. Insbesondere in einem Szenario, in dem die Anzahl der möglichen Insassen überschaubar ist, erscheint diese Implementierung attraktiv. Eine lokale Lösung, bei der die Klassifizierung auf der im Fahrzeug verbauten Hardware stattfindet, könnte vorteilhaft sein, insbesondere wenn das Fahrzeug über eine leistungsfähige Hardware verfügt, wie sie beispielsweise bei autonomen Fahrsystemen zum Einsatz kommt.

Andererseits ist zu berücksichtigen, dass bei einer begrenzten Anzahl von Fahrgästen möglicherweise einfachere Lösungen zur Verfügung stehen. Eine manuelle Auswahl über ein Menü in der Headunit des Fahrzeugs oder über eine App könnte eine Alternative darstellen, die die Entwicklungskosten für die Stimmerkennung oder andere Identifizierungstechnologien möglicherweise nicht rechtfertigt.

Die Anwendung in Carsharing und Fahrzeugpools konnte im Rahmen der durchgeführten Versuche nicht umfassend behandelt werden. Es ist jedoch offensichtlich, dass der Nutzen hier besonders groß ist, vor allem für den Fahrer, der sich die Zeit sparen könnte, sich jedes Mal in ein geliehenes Fahrzeug einzurichten. In diesen Szenarien wäre die Verwendung eines Backends zur Synchronisierung der Sprecher zwischen mehreren Pool-Fahrzeugen unerlässlich.

Ein Nachteil der Insassenidentifizierung mittels Stimmerkennung ist, dass, wenn sich nur ein Fahrer im Fahrzeug befindet, die für diese Implementierung notwendigen natürlichen Gespräche fehlen. Dies gilt beispielsweise für Firmenfahrzeugpools, in denen sich häufig nur ein Insasse, der Fahrer, sich befindet.

Insgesamt ist es wichtig, die Implementierung sorgfältig auf die Einsatzgebiete abzustimmen. Während die Stimmerkennung in bestimmten Szenarien wie Familienfahrzeugen durchaus sinnvoll sein kann, müssen auch einfachere Alternativen in Betracht gezogen werden, insbesondere wenn sie kosteneffektiver und benutzerfreundlicher sind. Eine umfassende Bewertung der Technologien und ihrer Anwendbarkeit in realen Anwendungsszenarien ist daher unerlässlich.

## Zusätzliche Einsatzgebiete

Die Identifizierung von Fahrzeuginsassen mit Hilfe von Stimmerkennung bietet auch Potenzial für weitere Einsatzgebiete. Ein wichtiges Anwendungsgebiet ist das Führen eines Fahrtenbuches, welches für den Fahrzeugbesitzer bzw. Fahrzeugvermieter nützlich sein kann. Auch für Versicherungsunternehmen könnte es von Bedeutung sein, zu verstehen, wer sich wo im Fahrzeug befand, wer gefahren ist und ob sich Kinder im Fahrzeug befanden. Diese Informationen, in Kombination mit anderen Datenquellen, könnten dazu beitragen, Konflikte im Straßenverkehr zu lösen. Die Implementierung ist dafür gut geeignet, da die Genauigkeit der Ergebnisse mit der Fahrzeit zunimmt.

Ein weiteres Einsatzgebiet könnte für OEMs von Interesse sein. In einer Welt, in der immer mehr Daten gesammelt werden, könnten Informationen darüber, wie die Kunden ihre Fahrzeuge nutzen, von Vorteil sein, um die Bedürfnisse der Kunden besser zu verstehen und gezielte Anpassungen an den Fahrzeugen vornehmen zu können.

Selbstverständlich müssen diese Anwendungsbereiche im Hinblick auf Datenschutz und Sicherheit sorgfältig geprüft werden. Dennoch könnten sie von den Vorteilen der Stimmerkennung profitieren und neue Möglichkeiten zur Verbesserung von Fahrzeugen und Dienstleistungen eröffnen.

## Beantwortung der Forschungsfrage

Die in Kapitel 1.4 formulierte Forschungsfrage kann nun mit Hilfe der prototypischen Umsetzung und der diskutierten Ergebnisse beantwortet werden. Die Implementierung der Stimmerkennung als Proof of Concept liefert zwar einen ersten Ansatz zur Insassenidentifizierung, stellt aber keine eindeutige Antwort auf die Forschungsfrage dar.

Datenschutzrechtliche Aspekte konnten im Rahmen der prototypischen Umsetzung nicht abschließend untersucht werden, jedoch wurden in Kapitel 5.2.1 Methoden diskutiert, wie datenschutzrechtlich relevante Themen ausgearbeitet werden können. Hinsichtlich der Benutzerfreundlichkeit konnte festgestellt werden, dass die Stimmerkennung als Mittel zur Insassenidentifizierung im Fahrzeug nicht ohne Einschränkungen geeignet ist, wie in der Auswertung der Versuche in Kapitel 5.2.2 beschrieben.

Es ist anzumerken, dass diese Arbeit einen breiten Themenbereich der Insassenidentifizierung abdeckt. Die Beantwortung der Forschungsfrage erfolgt durch die Analyse der implementierten Lösung und die darauf aufbauende Diskussion der Ergebnisse. Es wurden auch Rückschlüsse für die weitere Entwicklung der Technologie gezogen, wobei eine sinnvolle Eingrenzung der Themenbereiche möglicherweise weitere Entwicklungen bringen kann. Eine stärkere Fokussierung auf einzelne Komponenten der Insassenidentifizierung könnte für zukünftige Forschungsarbeiten von Vorteil sein, um detailliertere Einblicke und mögliche Fortschritte zu erhalten.

## Fazit

Die vorliegende Arbeit hat sich umfassend mit der Thematik der Insassenidentifizierung beschäftigt. Zunächst wurde eine Marktanalyse durchgeführt, um die vorhandenen Technologien zu erfassen. Anschließend wurden verschiedene Technologien untersucht, die sich für die Insassenidentifizierung eignen. Die Stimmerkennung wurde als vielversprechender Ansatz ausgewählt und prototypisch implementiert. Die Implementierung wurde evaluiert und durch verschiedene Versuche validiert, um die verschiedenen Einsatzgebiete zu untersuchen. Abschließend wurden die Ergebnisse ausführlich diskutiert und bewertet.

Die Evaluation der Implementierung zeigt, dass die Stimmerkennung unter optimalen Bedingungen funktional ist. Allerdings nimmt die Genauigkeit der Identifizierung in Situationen mit Hintergrundmusik oder anderen Tonlagen der Sprecher deutlich ab. Dies führt zu relativ ungenauen Ergebnissen, die für eine zuverlässige Authentifizierung und insbesondere für die Freigabe personenbezogener Daten nicht ausreichend sind.

Die Ergebnisse dieser Arbeit betonen, dass trotz der nicht eindeutig positiven Implementierungsergebnisse, ein Potenzial für die Stimmerkennung als Methode zur Identifizierung von Insassen im Fahrzeugkontext besteht. Es bedarf jedoch weiterer Optimierungen, wie die Berücksichtigung von Umwelteinflüssen, um eine zuverlässige und einsatzfähige Lösung zu gewährleisten.

## Ausblick und Zukünftige Arbeiten

Diese Arbeit stellt einen grundlegenden Ansatz dar, um die Insassenidentifizierungstechnologie weiterzuentwickeln und zu verbessern. Obwohl die Stimmerkennung nicht als optimale Lösung für dieses spezifische Einsatzgebiet identifiziert wurde, eröffnet sie dennoch interessante Möglichkeiten für zukünftige Forschungsansätze in der Industrie. Die prototypische Implementierung bietet wertvolle Einblicke in die Realisierbarkeit und Herausforderungen der Stimmerkennung im Fahrzeugkontext. Durch eine Weiterentwicklung und Verbesserung dieser Technologie können potenziell präzisere und zuverlässigere Lösungen entwickelt werden, die einen signifikanten Beitrag zur Sicherheit und Effizienz im Fahrzeugbereich leisten können. Weitere Forschungsarbeiten zur Insassenidentifizierung im Fahrzeugkontext könnten folgendermaßen beschrieben werden.

Eine mögliche Forschungsrichtung bezieht sich auf die Weiterentwicklung des verwendeten Modells von Fadi Badine aus der Keras-Dokumentation [@keras_speaker_recognition]. Obwohl das Modell funktionell ist, liefert es nicht immer nachvollziehbare Ergebnisse. Angesichts dieser Herausforderung wäre es interessant zu untersuchen, wie das ML-Modell speziell für diese Aufgabe optimiert werden kann.

In der Diskussion wurden diverse Ansätze für alternative Einsatzgebiete der Insassenidentifizierung im Fahrzeugkontext erörtert. Es wäre interessant zu untersuchen, wie diese Technologie auch in anderen Anwendungsbereichen eingesetzt werden könnte und welche neuen Geschäftsmodelle sich daraus ergeben könnten. Insbesondere aus Sicht von Versicherungsunternehmen könnten sich, wie bereits diskutiert, neue Möglichkeiten ergeben.

Eine weitere interessante Herausforderung wäre die Implementierung der Stimmerkennung auf der im Fahrzeug vorhandenen Hardware. Eine Untersuchung, inwieweit die Headunit im Fahrzeug für eine ähnliche Implementierung verwendet werden könnte, wäre von Interesse. Aus Gründen des Produktschutzes ist eine solche Aufgabe nur im OEM-Rahmen möglich.

Diese potenziellen Forschungsrichtungen könnten dazu beitragen, die Insassenidentifizierung im Fahrzeugkontext voranzutreiben und neue Möglichkeiten für die Anwendung und Entwicklung dieser Technologie aufzuzeigen.
