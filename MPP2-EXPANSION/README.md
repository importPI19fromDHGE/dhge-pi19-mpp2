MPP2 - Themenkatalog
====================

<!-- md2apkg ignore-card -->

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<!--pagebreak-->

# Präambel

Diese File beinhaltet überwiegend Inhalte der letzten beiden Semester zur Vorbereitungen für die zweite mündlichen Praxisprüfung. Es sollte stets gemeinsam mit den [Vorbereitungen zur ersten Praxisprüfung](../BASE-PACK/README.md) betrachtet werden.

Als größtenteil irrelevant betrachtete Themen:
> **ToDo**
>
> - manche WPM II und III
>   - Herbst Unity
>   - Medienkram Turtenwald
>   - **ToDO**
> - Graphische Datenverarbeitung - (GDV) - Herbst
> <!--über die folgenden müssen wir noch diskutieren-->
> - neuronale Netze und maschinelles Lernen - (ML) - Feldmann (**ToDo**)
> - Forensik - (PRO) - Strassburg (**ToDo**)
> - e-Commerce - (WEB) - Müller (**ToDo**)
> - Consulting - (CONS) - Müller (**ToDo**)
> - ABWL 1&2 - Leder (Ausnahmen)

<!-- md2apkg ignore-card -->

# Hardwarenahe Programmierung

> **ToDo**
>
> - Intel vs. AVR?
> - Application Binary Interface (ABI)
> - Register
> - Stack
> - Heap
> - Flags
> - Timer
> - Watchdog

<!-- md2apkg ignore-card -->

# Systemprogrammierung

> **ToDo**
>
> - Parallele Programmierung
> - Kritischer Abschnitt [DONE]
> - Atomare Operation
> - Exklusive Ressource
> - Fork [DONE]
> - Interprozesskommunikation [DONE]
>   - Sockets (lokal, rechnerübergreifend) [DONE]
>   - Shared Memory [**ToDO**]
> - Signale?! <!-- Steht nur in der Übersicht am Anfang des Moduls und taucht dann nicht nochmal auf-->

<!-- md2apkg ignore-card -->
<!-- Deadlock -->

## Wie lautet das Philosophenproblem?

- 5 Philosophen mit 5 Stäbchen an rundem Tisch
- Aktion: Denken oder Essen;
- Essen benötigt zwei Stäbchen (Nicht genug Ressourcen für alle)
- gleichzeitiger Zugriff
- Deadlock kann entstehen

## Was ist ein Deadlock?

- **Allgemein**
  - Situation, in der sich beide Alternativen eines Dilemmas gegenseitig blockieren **oder**
  - in der die Handlungspartner nicht zu Kompromissen zur Lösung einer solchen Situation bereit sind, wodurch die Situation ausweglos wird.
- **Informatik**
  - Gegenseitige Blockade mehrere Prozesse, weil sie auf die Freigabe von Betriebsmitteln warten, die ein anderer beteiligter Prozess bereits exklusiv belegt hat

## Wie werden Deadlocks verhindert oder aufgelöst?

- ggf. auch über Pipes (Implementierung notwendig)
- Sockets benutzen
<!-- ToDo Erklärung für Pipes, Sockets, Factcheck, sind Semaphoren gemeint?-->
- Semaphoren
- Reboot
- Auf Ressource verzichten (Signale an Prozess senden)
- Prozess beenden, Signal SIGTERM/SIGKILL

<!-- Fork -->

## Zweck, Wirkweise fork()

- es wird eine exakte Kopie des Aufrufers als Kindprozess erzeugt
- Kindprozess übernimmt Code, Daten inkl. Befehlszähler, Dateideskriptoren, ...
<!-- Sempahore -->

## Rückgabewerte fork

- `>0`: die PID des Kindprozesses
- `0`: es wurde eben geforkt und wir sind das Kind
- `-1`: Fehler

<!-- Interprozesskommunikation IPC -->

## Motivation Interprozesskommunikation

- Verhinderung von
  - gleichzeitigen Schreibzugriffen
  - Verhungern von Prozessen
  - Deadlocks

### Wie können Sie bidirektionale Interprozesskommunikation ermöglichen?

- Pipe umdrehen, ggf. mit Zugriffskonzept (Semaphore), BAD Practice
- 2 Pipes verwenden
- Sockets

<!-- Semaphore -->

## Was sind Semaphoren und wozu werden Sie eingesetzt?

- Mittel der Interprozesskommunikation zu Verwaltung von (exklusivem) Zugriff auf Ressourcen
- Deadlock vermeiden

## Was ist der kritische Abschnitt im Kontext Sempahoren?

- Es ist ein Codebereich, der nur in einer definierten Anzahl von Prozessen gleichzeitig zur Verfügung steht (stehen sollte)
- Entwickler müssen im Programm dafür Sorge tragen und den kritischen Abschnitt definieren
- Semaphor Operation P, Passieren, Vor dem kritischen Abschnitt LOCK - Ressourcen blockieren
- Semaphor Operation V, Verlassen, Nach dem kritischen Abschnitt UNLOCK - Ressourcen freigeben

<!-- Pipes -->

## Was sind Pipes im Kontext Interprozesskommunikation? Unterscheiden Sie zwei Arten von Pipes

- unidirektionaler Datenstrom zwischen zwei Prozessen: Puffer/Warteschlange nach dem FIFO-Prinzip
- namenlose Pipes: Kommunikation zwischen verwandten Prozessen (vgl. fork())
- benannte Pipes: Zugriff durch alle Prozesse mit Zugriffsrecht möglich

## Welche Operationen auf einer Pipe kennen Sie? Beschreiben Sie deren Funktion

- `write(pipefd[1],buffer)`
  - Write: Aus Programmbuffer auf die Pipe schreiben, in den Kernelbuffer
  - Daten sind gepuffert bis sie gelesen werden
- `read(pipefd[0],buffer)`
  - Read: Aus Kernelbuffer in Programmbuffer schreiben; aus Sicht des Programms von Pipe lesen
  - Lesen verbraucht Daten der Pipe

<!-- Socket -->

## Addressfamilien Socket

- POSIX local inter-process communication sockets/Unix Domain Socket/IPC Socket (AF_UNIX,AF_LOCAL)
- Internet-Domain (AF_INET und AF_INET6)
- diverse andere, viele veraltet
  - AF_IRDA
  - AF_BLUETOOTH

## Arten Socket

- Verbindungslos (SOCK_DGRAM) 
- vollduplex, verbindungsorientiert (SOCK_STREAM)

außerdem

- SOCK_RAW nur für Developer, Root-User, Zugriff auf L3,L2-Felder --> eigenes L4-Protokoll entwickeln
- SOCK_SEQPACKET (nur UNIX, besseres SOCK_STREAM)

## Unterschied Pipe Socket

- Pipes
  - Unix-Domaine exklusiv, d.h. gleiches Rechensystem
  - unidirektional
- Socket
  - Unix/Internetdomäne
  - bidirektional

# Entwicklung von Webanwendungen

> **ToDo**
>
> - HTML
> - CSS
>   - Selektoren
> - Javascript
> - PHP?!

<!-- md2apkg ignore-card -->

# IT-Sicherheit/-Recht/-Infrastrukturen

> **ToDo**
>
> - IT-Sibe
> - ISO 27001
> - BSI 200er kennen
> - IT-Grundschutz-Kompendium und Bausteine einordnen

<!-- md2apkg ignore-card -->

# Rechnernetze und Verteilte Systeme

> **ToDo**
>
> - VLAN
> - OSPF
> - BGP
> - Architekturen
> - CAP-Theorem <!--?-->

<!-- md2apkg ignore-card -->

# Allgemeine Betriebswirtschaftslehre

> **ToDo**
>
> - Kalkulation <!--Günther-->
> - Angebotsarbeit <!--Günther-->

<!-- md2apkg ignore-card -->

# Entwicklerwerkzeuge

> **ToDo**
>
> - Dokumentationsgeneratoren
> - Builds-Tools
> - Versionsverwaltung
> - Debugger
> - Speicherzugriffsanalyse
> - Profiling
> - Unit-Tests

<!-- md2apkg ignore-card -->

# Compilerbau

> **ToDo**
>
> - Parser
> - Lexer
> - Compiler-Compiler

<!-- md2apkg ignore-card -->

# Computerforensik

> **ToDo**

<!-- md2apkg ignore-card -->

# IT-Consulting

> **ToDo**

<!-- md2apkg ignore-card -->

# Wissenschaftliches Arbeiten

> **ToDo**
>
> - Problemdefinition <!--Günther-->
> - Lösungsansatz <!--Günther-->
> - Anforderungsanalyse

<!-- md2apkg ignore-card -->
