## Motivation

Die Idee, einen Prozess über Releasemanagement zu machen, kam mir einfach als Bestandteil meiner Arbeit und vor allem, weil es notwendig war, einen Prozess zu modellieren und implementieren, der allen Anweisungen entsprach, die im Rahmen der Durchführung dieses Projekts erteilt wurden.

## Prozessabgrezung
## Prozessbeschreibung
Nach dem Kauf einer Software kommt es sehr oft vor, dass ein Kunde der SAW-AG auf ein Problem stößt, das technisch oder funktional sein kann. Unabhängig davon, ob es sich um das eine oder andere handelt, sendet der Kunde seinen Wunsch durch Ausfüllen eines elektronischen Ticketmanagementsystems. Dieses Ticket geht beim Kundendienst ein, der den Inhalt des Tickets überprüft. Es kann vorkommen, dass der Kunde bei dieser Überprüfung eine E-Mail mit dem Vorbehalt der Stornierung seines Tickets sendet.
Je nach Inhalt (Zweck des Tickets) entscheidet der Mitarbeiter, ob es sich um ein technisches Problem (Bug) oder ein direkt lösbares Problem handelt. Im letzteren Fall muss der Mitarbeiter eine Lösung finden, indem er entweder sein eigenes Wissen einsetzt, die Datenbank des Unternehmens abfragt oder im Internet recherchiert. Danach sendet er die Lösung per E-Mail an den Kunden. Falls es sich um einen Bug handelt, wird das Ticket an die Entwicklungsabteilung geschickt. Falls es sich um einen Bug handelt, wird das Ticket an die Entwicklungsabteilung geschickt. Bevor der „Bug“ behoben wird, schreibt dieser Service das „User Story“ (Feature Freeze) und führt gleichzeitig die Lokalisierung des Bugs. Danach wird der Bug bestimmen und dann kann den Testfall anfangen. Für die Bestimmung bzw. die Priorisierung des Testfalls benötigt der Entwickler folgende Input-Daten: Der Kundenstatus und die von der Kunde benützte Release-Version. Kunde wurden in Drei Kategorien abgebildet:

- 	„gold“: Kunde, die zu dieser Kategorie gehören werden mit der Priorität 1 unabhängig von anderen Bedingungen behandelt.
- 	„silver“: Die Priorität in dieser Kategorie hängt von der von den Kunden verwendeten Release-Version ab. Falls die Release-Version kleiner als 11 ist wird die Priorität 2 angesetzt. Im anderen Fall wird der Bug mit der Priorität 2 behandeln. 
- 	„bronze“: Kunde, die zu dieser Kategorie gehören werden mit der Priorität 3 unabhängig von anderen Bedingungen behandelt. 

Nach der Priorisierung wird der Bug gefixt und an die QA-Abteilung gesendet. Diese Abteilung beschäftigt sich mit dem Schreiben des Test-designs, die Bestimmung und die Durchführung des Testfalls. Alle diese Tasks werden nacheinander durchgeführt.

Für die Bestimmung des Testfalls müssen folgende Input-Daten angewendet werden:
- 	Die Häufigkeit
- 	Das Testdauen (sprint)
- 	Die Bugtypes.

Danach wird der Test-Round durchgeführt. Nachdem der Test-Round abgeschlossen ist wird die Testvollständigkeit geprüft. Falls alles nicht gut ist wird ein Changset geschrieben und an die Entwicklungsabteilung gesendet und wird der Bug nochmal gefixt und zurück an die QA-Abteilung geschickt. Falls alles gut ist wird einen Fehlernachtest durchgeführt und am Ende die neue Release an der Kunde geschickt. 

## BPMN- / DMN-Modellierung

Die Modellierung wurde mit Camunda-Modeler und Camunda-DMN durchgeführt. Um die Prozess-Kommunikation zwischen das Unternehmen SAW-AG zu implementieren, wurde diese Kommunikation anhand Postman durchgeführt. Für die Automatisierung des Prozesses wird Camunda-Engine angewendet.
Die folgenden Abbildungen stellen die modellierten Prozesse dar:

### Hauptprozess: ReleaseManagement.bpmn
![image](https://user-images.githubusercontent.com/50373209/60469104-e043af80-9c5b-11e9-88e3-ac5cd6a2bc84.png)

### Bug_Bestimmen.dmn
![Bug_Bestimmen](https://user-images.githubusercontent.com/50373209/60469335-927b7700-9c5c-11e9-86af-bdc998178b2e.png)

 

### Sub-Prozess: Test_Durchführen.bpmn
### TestFall_Bestimmen.dmn
