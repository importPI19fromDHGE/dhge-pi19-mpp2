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
> - Verteiltes System (Definition) [DONE]
> - CAP-Theorem [DONE]
> - Namens- und Verzeichnisdienste [DONE]
> - Caching vs. Replikation [DONE]
> - ACID vs. BASE [DONE]
> - sync. vs. async (Replikation)
> - Microservices
> - VLAN
> - OSPF
> - BGP
> - Architekturen
> - Firewalls

<!-- md2apkg ignore-card -->

## Verteiltes System

Ein verteiltes System ist ein System bestehend aus...

- mehreren Einzelkomponenten
- auf unterschiedlichen Rechnern
- kein gemeinsamen Speicher
- Kooperation mittels Nachrichtenaustausch (Netzwerk)
- gemeinsames Ziel

## CAP-Theorem

Ein verteiltes System kann zwei der folgenden Eigenschaften gleichzeitig erfüllen, jedoch nicht alle drei:

- **C**onsistency (Konsistenz)
- **A**vailability (Verfügbarkeit)
- **P**artition Tolerance (Ausfalltoleranz)

## Namens- vs. Verzeichnisdienste

- **Namensdienst:** Bilden Namen auf Adressen ab
  - Namen: standortunabhängige Bezeichnung einer Ressource
  - Adresse / Referenz: eindeutige, physikalische / ortsbezogene Bezeichnung
- **Verzeichnisdienst:** Finden von Kommunikationspartnern, Ressourcen, Attributen, ...
  - Erweiterung des Namensdienstes

### Caching vs. Replikation

**Caching**

- Speicherung von Teilen des Namensraums
- v.a. auf unteren Ebenen
- vollst. oder teilw. Namen
- *reaktiv*

**Replikation**

- v.a. auf unteren Ebenen
- höhere Fehlertoleranz
- *proaktiv* (geplant)

> Problem: Aktualität von Einträgen und Gewährleistung von Konsistenz

## ACID-Prinzip

> auf Konsistenz ausgelegt

- **Atomicity:** Entweder vollständige oder keine Ausführung
- **Consistency:** nur Übergänge von konsistentem Zustand zu konsistentem Zustand
- **Isolation:** keine Überlappung von Transaktionen, die sich gegenseitig beeinflussen können
- **Durability:** nach Abschluss einer Transaktion werden Daten garantiert dauerhaft in einer DB gespeichert

### ACID vs. BASE

> **BASE** = **B**asically **A**vailable, **S**oft state, **E**ventual consistency (BASE)

|                      | ACID                         | BASE                                             |
| -------------------- | ---------------------------- | ------------------------------------------------ |
| **Optimierungsziel** | Konsistenz                   | Verfügbarkeit (Konsistenz wird nicht garantiert) |
| **Zugriffe**         | isoliert (Commit-basiert)    | letzer Schreibzugriff "gewinnt"                  |
| **Implementation**   | komplex, begrenzt skalierbar | einfach implementier und skalierbar              |
| **Attribute**        | konservativ / pessimistisch  | aggressiv / optimistisch / best effort           |

# Allgemeine Betriebswirtschaftslehre

> **ToDo**
>
> - Kalkulation <!--Günther-->
>   - Break-Even-Analyse
>   - Teil- vs. Vollkostenrechnung
>   - statische Amortisationsrechnung [DONE]
> - Angebotsarbeit <!--Günther-->
> - Unternehmen/Betrieb/Firma (Defintionen) [DONE]
> - Rechtsformen (Überblick)
> - Produkt-/Preis-/Kommunikations-/Distributions-Politik <!--?-->
> - SWOT <!--?-->
> - Projekt (Definition, Phasen)
> - Klassische Qualitätssicherung vs. TQM <!--?-->
<!-- Kompetenz !!!-->

<!-- md2apkg ignore-card -->

## Unternehmen / Betrieb / Firma

- **Unternehmen:** ganzheitliche, rechtliche, finanzielle und wirtschaftliche Einheit des Betriebs
- **Betrieb:** Ort der Leistungserbringung
- **Firma:** Geschäftsbezeichnung eines Unternehmens inkl. Rechtsformzusatz

## BWL-Kalkulation

### Statische Amortisationsrechnung

> Berechnung der Zeitspanne bis zur vollständigen Tilgung einer Investition

$$\text{Amortisationszeit} = \frac{\text{Kapitaleinsatz}}{\text{Rückflüsse pro Jahr}}$$

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
> - Anforderungsanalyse [DONE]

## Anforderungsanalyse

- Erhebung, Analyse, Spezifikation und Bewertung von Anforderungen eines Auftraggebers (nach IEEE)
- Ergebnis der Analyse: Lastenheft oder Backlog

### Nicht-Funktionale Anforderungen

> Anforderungen an die Qualität und Anforderungen, die sich aus Randbedingungen ergeben.

- **Qualität (nach ISO / IEC 9126):**
  - Änderbarkeit
  - Benutzbarkeit
  - Effizienz
  - Funktionalität
  - Übertragbarkeit
  - Zuverlässigkeit
- **Randbedingungen:**
  - Gesetze
  - Normen
  - Organisatorisch (Standards, Vorgehensweisen, Termine, Kosten)

### Funktionale Anforderungen

> beschreiben die Funktionalitäten und das Verhalten des Produkts ($\rightarrow$ Produktspezifisch)


<!-- md2apkg ignore-card -->
