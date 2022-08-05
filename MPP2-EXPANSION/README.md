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
> - Kritischer Abschnitt
> - Atomare Operation
> - Exklusive Ressource
> - Semaphore
> - Deadlock
> - Interprozesskommunikation
>   - Pipes (uni/bidirektional, named)
>   - Sockets (lokal, rechnerübergreifend)
>   - Shared Memory
> - Signale?! <!-- Steht nur in der Übersicht am Anfang des Moduls und taucht dann nicht nochmal auf-->

<!-- md2apkg ignore-card -->

# Entwicklung von Webanwendungen

> **ToDo**
>
> - HTML
> - CSS
>   - Selektoren
> - Javascript
> - PHP
> - REST-APIs

<!-- md2apkg ignore-card -->

# IT-Sicherheit/-Recht/-Infrastrukturen

> **ToDo**
>
> - IT-Sibe
> - ISO 27001
> - BSI 200er kennen
> - IT-Grundschutz-Kompendium und Bausteine einordnen
> - Schutzziele
> - Anonymisierung, Pseudonomisierung

<!-- md2apkg ignore-card -->

# Rechnernetze und Verteilte Systeme

> **ToDo**
>
> - Verteiltes System (Definition)
> - Namens- und Verzeichnisdienste
> - ACID vs. BASE
> - sync. vs. async (Replikation)
> - Microservices
> - VLAN
> - OSPF
> - BGP
> - Architekturen
> - Firewalls
> - CAP-Theorem

<!-- md2apkg ignore-card -->

# Allgemeine Betriebswirtschaftslehre

> **ToDo**
>
> - Kalkulation <!--Günther-->
>   - Break-Even-Analyse
>   - Teil- vs. Vollkostenrechnung
>   - statische Amortisationsrechnung
> - Angebotsarbeit <!--Günther-->
> - Unternehmen/Betrieb/Firma (Defintionen)
> - Rechtsformen (Überblick)
> - Produkt-/Preis-/Kommunikations-/Distributions-Politik <!--?-->
> - SWOT <!--?-->
> - Projekt (Definition, Phasen)
> - Klassische Qualitätssicherung vs. TQM <!--?-->
<!-- Kompetenz !!!-->

<!-- md2apkg ignore-card -->

# Entwicklerwerkzeuge

> **ToDo**
>
> - Dokumentationsgeneratoren (Vorteile)
> - Builds-Tools (Make)
> - Versionsverwaltung
> - Debugger (Arten)
> - Speicherzugriffsanalyse (statisch/dynamisch)
> - Profiling
> - Unit-Tests

<!-- md2apkg ignore-card -->

# Compilerbau

> **ToDo**
>
> - Parser
>   - Top-Down-Parser
>   - Shift-Reduce-Parser
> - Lexer
> - Compiler-Compiler

<!-- md2apkg ignore-card -->

# Computerforensik

> **ToDo**
>
> - Definition: Digitale Forensik
> - Datenschutzvorfall
> - Bereiche
> - Spuren
> - Post-Morem vs. Live-Forensik

<!-- md2apkg ignore-card -->

# IT-Consulting

> **ToDo**
>
> - DevOps
> - Virtualiserung vs. Containerisierung

## DevOps

- Kofferwort aus "Development" und "Operations"
- bezeichnet Entwicklung und Betrieb einer Software durch dasselbe Team, untrennbar
  - im ferneren Sinne auch QA
- oft in Verbindung mit Lean Management, agilen Methoden und CI/CD

### Ein paar Bestandteile der Entwicklung

- Programmieren der Software
- Tests
- Artefakte erzeugen (Kompilate / Archive)
- Auslieferung
- Doku für Kunde

### Ein paar Bestandteile des Betriebs (Ops)

- Bereitstellung der Hardware
- Installation der Software und Abhängigkeiten
- Monitoring
- Updates
- Wartung der Komponenten (z.B. pflegen der Datenbank)

### Vorteile von DevOps

- keine _Wall of Confusion_ / Silodenken zwischen Teams
- beschleunigt Entwicklungsprozess
- verhindert _"works on my machine"_

### Methode: Infra as Code (IaC)

- Infrastruktur wird maschinenlesbar abgebildet
- Nutzung von Auszeichnungssprachen (JSON, YAML)
- versionierbar
- hoher Automatisierungsgrad
- Bsp.: Ansible, Terraform, Chef, Puppet

### Blue/Green Deployment

- Minimierung der Ausfallzeit bei Updates
- zwei Instanzen einer Anwendung hinter Reverse Proxy, laufen parallel
- produktiv schalten der neuen Version durch Änderung der Reverse Proxy Konfiguration $\rightarrow$ minimale Downtime

### A/B Testing

- testen experimenteller Änderungen an kleinem Prozentsatz von Nutzern
- messen der Hypothesen, Vergleich der Reaktionen zwischen den Varianten

### Canary Releases

- ähnlich zu A/B, aber mit dem Zweck, Fehler in neuen Versionen zu finden
- alte und neue Instanz laufen hinter Reverse Proxy, kleiner Prozentsatz Nutzer wird auf neue, zu testende Version der Anwendung geleitet

## Vorteile von Monolithen

- einfaches Modell für Entwickler
- einheitliche Code-Basis und Build-Umgebung
- einfache **vertikale** Skalierbarkeit, d.h. mehr Ressourcen für Instanz zuweisen

## Nachteile von Monolithen

- Code-Basis wird riesig und unüberschaubar
- Überlastete Tools bei Refactoring, Builds, ...
- Skalierung ist Ressourcen-intensiv
- Deployment erfordert Stopp des gesamten Systems
- **horizontale** Skalierbarkeit schwierig

## Vorteile von Schichten-Architekturen

- einfach hinsichtlich Abhängigkeiten, Deployment, Skalierungsmodell

## Nachteile von Schichten-Architekturen

- Codebasis wächst mit jeder Schicht
  - und damit auch die Entwicklungs- / Betriebs-Prozesse
- Skalierung besser, aber weiterhin begrenzt
- technische Zerlegung $\rightarrow$ Silodenken

## REST

> Definition?

<!-- md2apkg split -->

- **Re**presentational **S**tate **T**ransfer
- Maschine-zu-Maschine Kommunikation auf Basis von HTTP als weit verbreitetes und gut unterstütztes Datenübertragungsprotokoll
- Client-Server-Prinzip
- zustandslos
- Caching möglich
- Nachrichten sind selbstbeschreibend, da Ressourcen über URI adressiert
- unterstützt verschiedene Repräsentationen für Daten, z.B. JSON, XML

### CRUD-Operatoren

- was bedeutet CRUD?
- was sind die Operatoren?

<!-- md2apkg split -->

- Create, Read, Update, Delete
- POST, GET, PUT, DELETE

## Microservice-Architektur

> Skizzieren Sie eine Microservice-Architektur und erläutern sie diese

<!-- md2apkg split -->

![Microservice-Architektur](assets/ms-arch.png)<!--width=600px-->

- erledigt nur eine Aufgabe, siehe UNIX-Philosophie
- arbeitet mit anderen Microservices via universeller Schnittstelle (z.B. REST)
- $\rightarrow$ Modularisierung (fachlich), funktionieren unabhängig voneinander
- keine gemeinsamen Zustände
- Vorschlag: Ein MS durch 5 bis 7 Entwickler realisierbar
- Betrieb in VMs oder Containern

### Vorteile von Microservices

- getrennte, überschaubare Code-Basen
- schnellere Entwicklung, CI/CD mit kürzeren Durchlaufzeiten
- geringe Kopplung
- Erweiterbarkeit durch einheitliche Schnittstellen
- horizontal und vertikal skalierbar
- Updates im laufenden Betrieb möglich

### Nachteile von Microservices

- empfindlich gegenüber Netzwerk-Störungen
- komplizierteres Modell
- höherer Overhead (Rechenressourcen und Kommunikation via HTTP)
- Datenkonsistenz wird aufwändiger
- Logging, Monitoring und Testen wird aufwändiger

<!-- md2apkg ignore-card -->

# Wissenschaftliches Arbeiten

> **ToDo**
>
> - Problemdefinition <!--Günther-->
> - Lösungsansatz <!--Günther-->
> - Anforderungsanalyse

<!-- md2apkg ignore-card -->
