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
> - Governance vs. Compliance [DONE]
> - Geltende Gesetze
> - Schutzziele [DONE]
> - DSGVO
>   - Personenbezogene Daten [DONE]
>   - Besondere Datenkategorien [DONE]
>   - Grundsätze der Verarbeitung [DONE]
> - Anonymisierung, Pseudonomisierung

<!-- md2apkg ignore-card -->

## Schutzziele

- Verfügbarkeit
- Vertraulichkeit
- Integrität

erweitert:

- Verbindlichkeit
- Authentizität
- Zurechenbarkeit

## IT-Grundschutz-Kompendium

- beinhaltet Einführung in die IT-Grundschutz-Methodik, Modellierung, Bausteine, Elementare Gefährdungen

- Prozess-Bausteine: ISMS (Sicherheitsmanagement), ORP (Organisation und Personal), CON (Konzeption und Vorgehensweise), OPS (Betrieb, vier Teilschichten: Eigener IT-Betrieb, Betrieb von Dritten, Betrieb für Dritte und Betriebliche Aspekte), DER (Detektion und Reaktion)
- System-Bausteine: APP (Anwendungen), SYS (IT-Systeme), IND (Industrielle IT), NET (Netze und Kommunikation), INF (Infrastruktur)
## Governance / Compliance

- **Governance:** Einhaltung von Richtlinien wird **empfohlen**
- **Compliance:** Einhaltung von Richtlinien ist **verpflichtend**

## Geltende Gesetze

<!-- ToDo: unvollständig -->

- DSGVO
- Telemediengesetz
- Urheberrecht
- E-Government-Gesetz
- klassisches IT-Recht besitzt nur vereinzelt besondere Gesetze ($\uparrow$)
- relevante Normen größtenteils über viele verschiedene Rechtsquellen verteilt
- u.a.: Zivil- und Urheberrechts; kartell- und strafrechtliche Regelungen; Normen aus AWG, DSGVO, Dual-Use VO, GeschGehG, HGB, InsO, KWG, ...

## DSGVO

### Personenbezogene Daten

> alle Informationen, die sich auf eine identifizierte oder identifizierbare lebende Person beziehen.

### Besondere Datenkategorien (Art. 9)

- Gesundheits- und biometrische Daten
- Politische Meinungen
- Religion
- Ethnie
- Gewerkschaftsangehörigkeit

> Diese sensiblen Daten besitzen einen **hohen Schutzbedarf** und benötigen **besondere technisch-organisatorische Maßnahmen**

### Grundsätze der Verarbeitung (Art. 5)

- Verarbeitung muss **rechtmäßig** und **zweckgebunden** erfolgen
- **Datenminimum**
- **Richtigkeit** der Daten
- **Integrität** und **Sicherheit** mit TOMs
- **Rechenschaftspflicht** (Verarbeitungsübersicht, SiKo)

## BSI-Standards des IT-Grundschutz (200-x)

- `BSI-Standard 200-1`: Aufbau eines Informationssicherheitsmanagementsystems
- `BSI-Standard 200-2`: Vorgehensweisen nach IT-Grundschutz
- `BSI-Standard 200-3`: Risikoanalyse
- `BSI-Standard 200-4`: Business Continuity Management

### `BSI-Standard 200-1`: Managementsysteme für Informationssicherheit

- Was: Erfolgsfaktoren beim Mgmt von Informationssicherheit
- Wie: Steuerung und Überwachung des Sicherheitsprozesses vom verantwortlichen Mgmt
- Wie: Entwicklung von Sicherheitszielen und angemessener Sicherheitsstrategie
- Wie: Auswahl Sicherheitsmaßnahmen und Erstellung Sicherheitskonzepte
- Wie: Erhalten und Verbessern eines erreichten Sicherheitsniveaus

- kontinuierlicher Verbesserungsprozess (PDCA)

### `BSI-Standard 200-2`: Vorgehensweisen nach IT-Grundschutz

- Anleitungen zu:
 - Aufgaben des IT-Sicherheitsmanagements
 - Etablierung einer IT-Sicherheitsorganisation
 - Erstellung eines IT-Sicherheitskonzepts
 - Auswahl angemessener IT-Sicherheitsmaßnahmen
 - IT-Sicherheit aufrecht erhalten und verbessern

- Basis-, Kern- oder Standard-Absicherung
- Standard-Absicherung ermöglicht ISO 27001 Zertifizierung

#### Standard-Absicherung

1. Strukturanalyse
2. Schutzbedarfsfeststellung
3. Modellierung
4. IT-GS-Check
5. ggf. Risikoanalyse
6. Konsolidierung
7. IT-GS-Check
8. Realisierung der Maßnahmen

- immer währenddessen: Aufrechterhaltung und kontinuierliche Verbesserung
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

<!-- md2apkg ignore-card -->

# Wissenschaftliches Arbeiten

> **ToDo**
>
> - Problemdefinition <!--Günther-->
> - Lösungsansatz <!--Günther-->
> - Anforderungsanalyse

<!-- md2apkg ignore-card -->
