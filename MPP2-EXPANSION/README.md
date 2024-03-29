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
> - Application Binary Interface (ABI) [DONE]
> - C und Make siehe Kusche Entwicklerwerkzeuge
> - Register [DONE]
> - Stack [DONE]
> - Heap (relevant, aber in dem Modul nicht angesprochen) [DONE]
> - Grimm
> - Flags [DONE]
> - Timer [DONE]
> - Watchdog [DONE]
> - Interrupt [DONE]

<!-- md2apkg ignore-card -->

## Application Binary Interface (ABI)

- allgemein: Schnittstelle auf Maschinenebene (vgl. compilierte API)
- definierte Schnittstelle, die Assembler-Verarbeitung ermöglicht (vgl. Inline-Assembler)
- ermöglicht direkten Aufruf von Assembler-Routinen

## Register

- Datenregister zur Speicherung von Operanden und Ergebnisse
- Adressregister zur Adressierung von Operanden (Speichern von Adressen)
- Steuerregister

## Stack (Speicher)

- vgl Datenstruktur. Stapelspeicher, Kellerspeicher (push,pop), LIFO
- In Mikroprozessoren: Register Stackpointer
  - bei Aufruf eines Unterprogramms: Rücksprungadresse ablegen
  - Parameter und lokale Variablen leben im Stack (vgl. Pufferüberlauf)
  - beginnt i.d.R. bei hoher Adresse, wächst Richtung 0 "nach unten"

## Heap (Speicher)

- beliebig frei zuordnenbarer Speicherbereich
- in C: vgl. Objekte `malloc()` und co., `free()`
- ! nicht zu verwechseln mit Datenstruktur Heap

## AVR ATmega 8515L

### Flags

- Statusregister SREG enthält 1-Bit-Informationen (Flags)
- Zeigen Ereignisse an
  - Carry
  - Zero
  - Negative
  - Overflow
  - Interrupt
  - ...

### Timer

- Zusammenhang MicroController-Takt
- i.d.R. Teilung des Takt (Prescaler)
- Anwendungen:
  - periodische Interrupts als Zeitgeber
  - Zeitverzögerungen; Ersatz für Programmschleifen
  - Frequenzgenerator / -messer
- periodische Interrupts als Zeitgeber

### Watchdog

- häufigste Anwendung: Reset des Programms im Fehlerfall
- eigener Takt
- zählt hoch
- Erreichen Schwellwert führt zu Neustart
- Im Normalbetrieb Reset der gezählten Zyklen -> kein Neustart
- Brownout Detection (Erkennen, ob die Betriebsspannung einen bestimmten Wert unterschreitet)
  - tritt regelmäßig auf! $\rightarrow$ ohne Detection unvorhersehbares Verhalten

### Interrupt

- Anforderung zur Unterbrechung des aktuellen Programms durch definiertes Ereignis
- Interruptflag gesetzt
  - Program Counter (PC) automatisch auf Stack gspeichert, Statusregister manuell sichern!
- Behandlung des Interrupts: PC ruft Interrupt Service Routine (ISR) definiert in Interruptvektortabelle auf
- ...
- Mit PC vom Stack fortfahren

# Systemprogrammierung

> **ToDo**
>
> - Parallele Programmierung
> - Kritischer Abschnitt [DONE]
> - Atomare Operation
> - Exklusive Ressource
> - Fork [DONE]
> - Deadlock [DONE]
> - Semaphore [DONE]
> - Interprozesskommunikation [DONE]
>   - Pipes (uni/bidirektional, named) [DONE]
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
- Semaphoren
- Reboot
- Auf Ressource verzichten (Signale an Prozess senden)
- Prozess beenden, Signal SIGTERM/SIGKILL

<!-- ToDo Erklärung für Pipes, Sockets, Factcheck, sind Semaphoren gemeint?-->

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

- Mittel der Interprozesskommunikation zur Verwaltung von (exklusivem) Zugriff auf Ressourcen
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
> - HTML [DONE 90%]
> - CSS [DONE?]
>   - Selektoren [DONE]
> - Javascript
> - PHP

<!-- md2apkg ignore-card -->

## Geschichte des Internets

<!-- md2apkg ignore-card -->

- 1958: Gründung Advanced Research Projects Agency
- 1969: ARPAnet vernetzt 4 Großrechner in Kalifornien und Utah
- 1972: 37 Einrichtungen in USA angeschlossen
- 1974: Entwicklung TCP, später TCP/IP
- 1986: Top Level Domains werden ins Leben gerufen
- 1989: Timothy Berners-Lee entwickelt ersten "Browser" WorldWideWeb
- 1991: Berners-Lee veröffentlicht HTML sowie die erste WWW-Seite
- 1992: 1 Mio. Rechner im Internet
- 2001: Wikipedia geht online
- 2005: Youtube geht ins Netz
  - $\rightarrow$ erstmals von Web 2.0 gesprochen (Inhalte kommen primär von den Nutzern)

## Client-Technologien

- HTML 5 $\rightarrow$ Beschreibung der Struktur der Webseiten
- CSS 3 $\rightarrow$ Formatierung / Aussehen
- Java-/ECMA-Script $\rightarrow$ Interaktion
- DOM/Ajax $\rightarrow$ Manipulation des Seiteninhalts
- Flash $\rightarrow$ obsolet
- JSON, XML(SVG, MathML, RSS, GraphML, ...) $\rightarrow$ Datenaustausch

## Server-Technologien

- PHP
- NodeJS
- Ruby (on Rails)
- Java
- ASP.NET
- ColdFusion

## HTML

### HTML-Sytnax: Tags

- Auszeichnung von Textelementen durch Tags
- `<tag>Text</tag>`
- Öffnendes Tag  schließendes Tag  dazwischen Body
- schließende Tags können in einigen Fällen entfallen (z.B. `<img/>`)
- Tags können Attribute enthalten `<tag attribut="Wert">body</tag>`

### HTML Struktur: `<html>`

- `<html>` ist sogenanntes Wurzeltag
- Attribut "lang" gibt die Dokumentensprache an

### HTML Struktur: `<head>`

- Dateikopf, Metainformationen, keine Darstellungen
- Informationen werden durch Browser, Suchmaschinen und Crawler benutzt

### Beispielelemente in `<head>`

```html
  <head>
    <meta charset="utf-8" />
    <!--kann Funktion eines HTTP-Response-Headers erfüllen-->
    <meta http-equiv="x-ua-compatible" content="ie=edge" />
    <!--Größe der Darstellung auf Displaygröße des Devices anpassen-->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!--Seite stellt zwei Farbschemata zur Verfügung, bevorzugt hell -->
    <meta name="color-scheme" content="light dark">
    <title>Hier steht der Titel der Seite</title>
    <link rel="stylesheet" href="css/main.css" />
    <link rel="icon" href="images/favicon.png" />
    <meta charset="UTF-8">
    <meta name="description" content="Seite">
    <meta name="keywords" content="HTML, CSS">
    <meta name="author" content="John Doe">
    <title>Titel</title>
  </head>
```

### HTML Struktur: `<body>`

Hauptteil der Seite, Inhalt, angezeigte Elemente

### HTML Hyperlinks

- `a` $\rightarrow$ anchor aka Hyperlinks
- `href="dokument.html"` ODER `="#ziel"` ODER `="dokument#ziel"`
- `href=""` $\rightarrow$ Seite neuladen
- `href="#"` oder `href="#top"` $\rightarrow$ Seitenanfang
- `download` $\rightarrow$ bei href angegebene Datei soll heruntergeladen werden
- `target` $\rightarrow$ wo Linkziel öffnen

### HTML Tabellen

```html
<table> <!-- Beginn einer Tabelle>
<tr> <!-- Tabellen Reihe>
<td> <!-- Tabellen Daten bzw. Spalte>
</td>
</tr>
</table>
```

### HTML Formulare

```html
<form>
 <label for="name">Name</label><!-- Beschriftung-->
 <input id="name" type="text"><!-- Eingabefeld-->
 <button type="submit">Absenden</button><!-- Button-->
   <label for="cars">Choose a car:</label>
  <select id="cars" name="cars"> <!-- Auswahlmenü-->
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
  </select>
</form>
```

- input type:
  - `text`
  - `password`
  - `color`
  - `checkbox`
  - `date`
  - `file`
  - `number`
  - `radio`
  - `range`

### HTML Listentypen

- sortiert $\rightarrow$ `ol` > `li`
- unsortiert $\rightarrow$ `ul` > `li`
- Beschreibungsliste $\rightarrow$ `dl` > `dt`, `dd`

### HTML 5: Verbesserungen

- Schwerpunkt auf Gliederung der Seite $\rightarrow$ bessere Übersicht bei vielen Elementen
- Suchmaschinen werten den Inhalt der Seite besser aus (mehr Semantik in der Syntax)
- Screenreader können flüssiger lesen
- weitere Neuerungen für Multimedia, Formulare

### HTML 5 Gliederungselemente

- ``<header>``
- ``<nav>``
- ``<main>``
- ``<article>``
- ``<section>``
- ``<footer>``
- ``<aside>``

### HTML Universalattribute

- `id` $\rightarrow$ eineindeutig
- `class` kann mehrmals vergeben werden
- `accesskey` (Taste zum Anspringen des Elementes)
- `contenteditable` (Inhalt kann verändert werden)
- `dir` (Schreibrichtung ltr oder rtl)
- `hidden`  (Element ausgeblendet)
- `draggable` (Kann Element gezogen werden?)
- `lang` (Sprache für Elemente überschreiben)
- `style` (inline-css)
- `title`

## CSS

### CSS einbinden

- inline CSS (`style="..."`)
- `<style></style>` im HTML-Header
- externes CSS einbinden (`<link rel="stylesheet" type="text/css" href="style.css">` im ``<head>``)

### Box-Model

- alle HTML-Elemente werden von Boxen umgeben (innen nach außen)
  - Content: Inhalt, Bilder, Texte
  - Padding: Bildet einen Puffer zwischen Content und Border, transparent
  - Border: Rand um das Padding, z.B. Linie mit eigener Breite, Farbe
  - Margin: Abstand zu anderen Elementen, transparent

## Selektoren

- Typselektor (HTML-Element)
- Universalselektor (*)
- Klassenselektor (beginnt mit `.`)
- ID-Selektor (beginnt mit `#`)
- Attributselektor `[Attributname]`
- Pseudoklassen (beziehen sich auf Eigenschaften der HTML-Elemente)
- Pseudoelemente (beginnen mit `::`) z.B. p :: before {content: ´+´}
- Verbundsselektoren (*.classname) bezieht sich auf Hierachie, benachbarte Elemente

## Javascript

### Anwendungen

- clientseitige Datenvalidierung
- Dialogfenster
- Nachladen von Daten ohne Reload der Seite
- Autovervollständigung/Suchvorschläge
- Manipulation von Websites per DOM

### Verwendung im Browser / mit HTML

- Einbinden von JavaScript Code in HTML mittels `<script>`-Tag
- inline im Tag oder mit `<script src="müll.js">`
- Ausführung im Browser mit bspw. Chromiums V8 oder Firefox' SpiderMonkey
- Ausführung auch unabhängig vom Browser mit Node (nicht Node.js)

### Typisierung JavaScript (static-dynamic)

dynamic

### Unterschied JavaScript & ECMA-Script

- ECMA-Script $\rightarrow$ Scripting Language Specification
- JavaScript (& andere Scriptsprachen) $\rightarrow$ setzen diesen Standard um

### DOM (Document Object Model)

- Programmierschnittstelle für HTML- und XML-Dokumente
- Dokumente als Baumstruktur
  - jeder Knoten ist ein Objekt im Dokument (Textabschnitte, Überschriften, Tabellen)
  - es existieren Eltern- und Kindknoten (hierarchischer Aufbau)
- Zugriff auf Objekte des Dokuments, Manipulation
- Unterscheidung zwischen:
  - Elementknoten $\rightarrow$ die hierarchisch miteiander verbundenen Knoten
  - Attributknoten $\rightarrow$ Eigenschaften von Elementknoten
  - Textknoten $\rightarrow$ Textinhalt eines Elementknotens

```javascript
document.getElementById(); // document.getElementById('div1')
document.getElementsByName(); // returnt viele
document.getElementsByTagName(); // returnt viele; Bsp.: <p> --> document.getElementsByTagName('p')
document.getElementsByClassName(); // returnt viele
document.querySelector(); // gibt erstes Element, das dem angegebenen CSS-Selektor entspricht, z.B.: document.querySelector('#franz');
document.querySelectorAll(); // gibt alle Elemente, die dem angegebenen CSS-Selektor entsprechen
```

## PHP

### Einbinden

```html
<?php

?>
```

### Anwendung

- Backend
- Datenbankzugriff
- Sessionverwaltung
- Autorisierung
- u.v.m

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

> beinhaltet Einführung in die IT-Grundschutz-Methodik, Modellierung, Bausteine, Elementare Gefährdungen

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

> immer währenddessen: Aufrechterhaltung und kontinuierliche Verbesserung

# Rechnernetze und Verteilte Systeme

> **ToDo**
>
> - Rechnernetzadministration Sem5 Barié
>   - VLAN
>   - Spanning Tree Protocol
>   - BGP
>   - SPOF
>   - Architekturen
> - verteilte Systeme Sem 6 Feldmann
>   - Verteiltes System (Definition) [DONE]
>   - CAP-Theorem [DONE]
>   - Namens- und Verzeichnisdienste [DONE]
>   - Caching vs. Replikation [DONE]
>   - ACID vs. BASE [DONE]
>   - sync. vs. async (Replikation)
>   - Architekturen
> - Firewalls

<!-- md2apkg ignore-card -->

## VLAN

- Unterscheidung physische Topologie, logische Topologie
- auf L2 angesiedelt (Ethernet)
- **portbasiert / untagged**: Zuordnung Ports zu VLAN auf Managed Switch
  - Endgerät weiß nichts von VLAN, normale Ethernet-Pakete
- **tag-basiert / tagged**: fügt ein [802.1q](https://de.wikipedia.org/wiki/IEEE_802.1Q) Feld im Ethernet-Header hinzu, welches VLAN ein Paket hat
  - mehrere VLANs pro Port möglich (oft "Trunk-Port")
  - erfordert Hardware mit VLAN-Support
- tagged VLAN auf unmanaged Switches: leiten korrekt weiter, können nicht tagged und untagged konvertieren

## Spanning Tree Protocol

- STP etabliert sich innerhalb des Netzes einen Spannbaum durch das Blockieren von Ports
- Spannbaum muss bei Ausfall physischer Links angepasst werden
- jedes VLAN benötigt seinen eigenen Spanning-Tree


## eBGP

- Kommunikation zwischen AS
- Border Router: gegenseitiges Peering mit fremden Border Router; Adresse muss bekannt sein
- Austausch Nachrichten: "Ich kenne den Weg zu Netz 123, die Wegkosten sind 456"


# Verteilte Systeme ToDo

## Verteiltes System (Definition)

Ein verteiltes System...

- besteht aus mehreren Einzelkomponenten auf unterschiedlichen Rechnern
- besitzt keinen gemeinsamen Speicher
- koordiniert und kooperiert mittels Nachrichtenaustausch (Netzwerk)
- hat ein gemeinsames Ziel
- tritt gegenüber Nutzenden als kohärentes System auf

## CAP-Theorem

Ein verteiltes System kann zwei der folgenden Eigenschaften gleichzeitig erfüllen, jedoch nicht alle drei:

- **C**onsistency (Konsistenz)
- **A**vailability (Verfügbarkeit)
- **P**artition Tolerance (Ausfalltoleranz)

## Namens- vs. Verzeichnisdienste (Definition)

- **Namensdienst:** Bilden Namen auf Adressen ab
  - Namen: standortunabhängige Bezeichnung einer Ressource
  - Adresse / Referenz: eindeutige, physikalische / ortsbezogene Bezeichnung
- **Verzeichnisdienst:** Finden von Kommunikationspartnern, Ressourcen, Attributen, ...
  - Erweiterung des Namensdienstes

## Caching vs. Replikation

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

## Architekturen

<-- Klausurersatzleistung, mehr? ToDo -->

### Dreistufige Architektur

- Präsentationsschicht - User Interface
- Verarbeitungsschicht - Applikationslogik
- Persistenzschicht - Datenbank

### Vorteile eine Einteilung der Architektur eines Verteilten Systems in Stufen

- Definition eindeutiger Schnittstellen
- unabhängige Modifikationen an den Stufen möglich
- Komplexität des Gesamtsystems wird durch Aufteilung reduziert

### Nachteile von Systemen mit zahlreichen (z.B. mehr als zehn) Stufen

- hoher Kommunikationsaufwand
- erschwert klare Zuordnung von Funktionen und Verantwortlichkeiten
- erhöhter administrativer Aufwand

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
> - Dokumentationsgeneratoren (Vorteile) [DONE]
> - Builds-Tools (Make) [DONE]
> - Versionsverwaltung [DONE]
> - Debugger (Arten) [DONE]
> - Speicherzugriffsanalyse (statisch/dynamisch) [DONE]
> - Profiling [DONE]
> - Unit-Tests [DONE]

<!-- md2apkg ignore-card -->

## Dokumentation

- Unterscheidung zw. **interner Doku (Entwickler-/Tester-Doku)** und **externer Doku (Endnutzer)**
- interne Doku wird durch Entwickler geschrieben und **direkt im Quellcode** festgehalten
  - **einfache Änderung**
  - direkte Einbindung in **Versionsverwaltung**
  - Unterstützung durch **IDE-Anbindung**
- Formate: `LaTeX`, `Docbook`, `AsciiDoc`, `Markdown`

### Dokumentationsgeneratoren

- Zweck: Erzeugung kommentierter Klassenreferenzen
- Extraktion der Doku aus dem Code und **speziellen Kommentaren im Source**
- *Spezielle Formatierung* von Funktionsparametern- und Returnwert-Doku
- Automatische Erzeugung von *Listen und Inhaltsverzeichnissen,* Abhängigkeitslisten, ...
- Beispiele: `doxygen`, `javadoc`, `robodoc`, ...

```cpp
/// this function does something
int someFunction(int par1, ///< parameter 1
                 int par2) ///< parameter 2
```

## Versionsverwaltung

- **Verwaltung und Archivierung aller Dateien** eines Software-Produkts **in Ständen**
- Buchführung über jede einzelne Änderung in jeder einzelnen Datei
  - optimierte Speicherung: **Nur die Deltas jeder Änderung,** nicht jedesmal die komplette Datei, und zwar **rückwärts** (aktuelle Version im Volltext)
  - organisiert Entwicklungszustände
  - alte Zustände sind wiederherstellbar
- koordiniert gemeinsamen Zugriff

> **Reproduzierbarkeit und Nachverfolgbarkeit**

## Builds-Tools (`make`)

- `make` automatisiert das **Kompilieren (großer) Projekte**
- erzeugt **intern Abhängigkeitsgraphen** der gewünschten Output-Files von den dazu notwendigen Input-Files
- baut nur genau das neu, was notwendig ist/geändert wurde
- `make` **arbeitet nur nach File-Datum** (greift nicht auf die File-Inhalte zu)
- erkennt Abhängigkeiten der Files $\rightarrow$ kann voneinander **Unabhängige parallel kompilieren**
- Konfiguration über `Makefile` $\rightarrow$ Targets und deren Abhängigkeiten

## Debugger

> Werkzeug zum **Diagnostizieren und Auffinden von Fehlern**

- Code muss mit **Debug-Symbolen** kompiliert worden sein
- Ansichten: Position im Source, Call-Stack (Funktionen + Argumente), Variablen (lokal + global)
- Funktionen: Breakpoints, Stepping, Watchpoints, Manipulation von Variablen, ...

### Betriebsmodi eines Debuggers

- **Post-mortem** Debugging: Analysieren einer "Leiche" (`core dump` laden)
- Anhängen an einen **bereits laufenden Prozess:** nützlich, wenn Programm erst nach langer Laufzeit Fehler zeigt
- **Starten einer Binary** mit Debugger: gängigste Methode in der Entwicklung

### Speicherfehler

- **Memory-Leaks:** Referenz auf dynamisch reservierten Speicher geht verloren $\rightarrow$ Speicherbedarf wächst bis zum Prozessabbruch
- **Memory-Fragmentation:** kein echter Programmfehler $\rightarrow$ ungünstige Speichernutzung
  - Folge unterschiedlich großer `malloc` und `free` Befehle $\rightarrow$ keine größeren Speicherblöcke mehr verfügbar

#### Speicherfehler-Tools

- **Adress Sanitizer:** über jedes Byte im gesamten Adressraum wird Buch geführt ob (un)gültig; jeder Pointerzugriff wird geprüft
- **Memory Sanitizer:** erkennt Lesezugriffe auf Speicherbereiche, die zuvor nicht initialisiert wurden
- **Leak Sanitizer:** liefert am Ende der Ausführung Liste dynamisch angelegter und nicht freigegebener Speicherstrukturen
- **Thread-Sanitizer:** erkennt Data Races (Zugriffe verschiedener Threads auf gemeinsamen Speicher $\rightarrow$ zufällig, Scheduler abhängig!)

## Profiling

> Untersuchung des zeitlichen Programmverhaltens

- Statistiken zu:
  - Anzahl der Funktionsaufrufe
  - Ausführungszeit von Codeabschnitten
  - Coverage (*Welcher `if`-Zweig nie/selten?*)
- **Instrumentierte Profiler:** Messcode für Code-Blöcke und Funktionen $\rightarrow$ exakte Messung, verändertes Zeitverhalten durch Overhead
- **Sampling Profiler:** *Code bleibt unverändert* $\rightarrow$ regelmäßiges Unterbrechen und Extrahieren von Debug-Infos (aber an manchen Stellen "blind")

### Ziele von Profiling

- **Hotspots** erkennen (stark frequentierte bzw. zeitintensive Codeblöcke) $\rightarrow$ größtes Potential für Optimierung
- **Feedback** für Optimierungen
- Abdeckungsgrad von Tests feststellen

## Unit Tests

> Tests von möglichst kleine Code-Stücken (z.B. Funktionen) auf konformes Verhalten

- Motivation: zeitnahe Fehlerfindung, gesamte Code-Abdeckung, genaue Lokalisierung
- laufen automatisch, erfordern Tooling
- hoher Einmal-Aufwand, geringer laufender Aufwand
- Positive Nebeneffekte: Prüfung der Spezifikation und des Feinentwurfes
- Ein Testfall pro Verhalten einer Funktion $\rightarrow$ ein Testfall pro Codefall
- Ein Testfall für jeden bekannten Bug
- Erstellung zeitnah/gleichzeitig zum Code (nicht durch QA $\rightarrow$ Betriebsblindheit)
- werden in der Versionsverwaltung mit eingecheckt

# Compilerbau

> **ToDo**
>
> - Lexer [DONE]
> - Parser [DONE]
>   - Top-Down-Parser
>   - Shift-Reduce-Parser
> - Compiler-Compiler

<!-- md2apkg ignore-card -->

## Lexer

> *"lexikalischer Analysator"*

- Verarbeitet Strom von Einagbezeichen in Token
- z.B. Zusammenfassen von Ziffer zu Zahlen oder Buchstaben zu Schlüsselworten

## Parser

> *"Syntaxanalysator"*

- Anwendung der Syntaxregeln zur Verarbeitung der Eingabe
- Ausgabe: Syntaxbaum oder direkte Ausführung
- Erkennung von Syntaxfehlern

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

### Git: Datei-Lebenszyklus

- **Untracked**: nicht eingecheckt
- **Unmodified**: eingecheckt, keine lokale Änderung
- **Modified**: eingecheckt, lokale Änderung
- **Staged**: modifizierte Datei ist in Änderungsmenge, diese Version ist zum Commit vorgemerkt (Änderungen nach Stage werden nicht committet)
- **Committed**: Datei-Version ist permanent in lokalem Repository
- **Pushed**: Version an externes Repository übertragen

### Git: Merge vs. Rebase

- **`git merge`**: Commits aus einer Branch in eine andere Branch übernehmen, die Änderungen _verschmelzen_
- **`git merge`**: schreibt einer Branch um, sodass sie auf einen neuen Commit der Parent Branch zeigen
  - Effekt: neue Änderungen an der Eltern-Branch werden in Child-Branch übernommen
  - Remember: Commits sind Rückwärts-Deltas

### Git: Feature-getriebener Workflow (Bild)

![Git Feature-Workflow](assets/git-feature-workflow.png)<!--width=600px-->

### Git: Trunk-basierter Workflow (Bild)

![Git Trunk-Workflow](assets/git-trunk-workflow.png)<!--width=600px-->

### Git: Vor- und Nachteile Feature-Workflow

| Vorteile | Nachteile |
| :------: | :-------: |
| Verwaltung großer Projekte einfacher, da sauberer Zustand einzelner Branches | viele Merges notwendig, unübersichtlich |
| Trennung von stabilem und experimentellem Code, leichter Einstieg | langlebige Feature-Branches lassen Versionen divergieren |
| Unterstützung für Release-Planung und verschiedenen Release-Zweigen | parallele Branches erschweren DevOps |

### Git: Vor- und Nachteile Trunk-Workflow

| Vorteile | Nachteile |
| :------: | :-------: |
| Nur Main-Branch ist langlebig $\rightarrow$ weniger Merge-Konflikte | Main-Branch unterliegt ständiger Änderung (Churn) |
| Einfachs Branching-Modell, vermeidet divergierende Entwicklung | Parallele Feature-Entwicklung in einer Branch |
| Schnelle Entwicklungszyklen, da einfache Integration und jederzeit lauffähige Version | Gemeinsame Verwaltung von stabilem und experimentellem Code, da sofortiges Zusammenlaufen in `main` |

## Docker

- Container-basierte Virtualisierung von Anwendungen
- nutzt Features des Linux-Kernels : Namespaces, cgroups, libcontainer (MacOS und Windows: VM)
- nutzt Beschreibungsformate für Images und Container: Dockerfile, Compose-File

- Isolation von Dateisystem, Ressourcen und Netzwerk
- Verwaltung via Kommandozeile oder REST-API
- Logging-Funktionalität für Container

### Docker: Images

- unveränderliche Snapshots eines Dateisystems
- können beliebig oft instanziiert werden, sowie transportiert und veröffentlicht
- Identifikation über Hash, Eigentümer, Name und Tag
- **Container** sind Instanzen eines Images
- implementiert Dateisystem-Layers für aufeinander aufbauende Images und effizientere Speicherung (Think: übereinanderlegen von Polylux-Folien)
- Änderungen am Dateisystem in einem **Container** werden in eigenem Container-Layer gespeichert

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
