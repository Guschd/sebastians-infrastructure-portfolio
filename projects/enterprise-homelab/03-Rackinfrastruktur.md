# 3 Rackinfrastruktur

## Zielsetzung

Die gesamte produktive Infrastruktur ist in einem zentralen 19"-Serverschrank untergebracht. Durch die Zusammenführung aller aktiven Netzwerkkomponenten, der Virtualisierungsplattform sowie der Stromversorgung entsteht eine übersichtliche, wartungsfreundliche und erweiterbare Infrastruktur.

Die Anordnung der Komponenten folgt funktionalen Gesichtspunkten und ermöglicht kurze Leitungswege sowie eine strukturierte Verkabelung.

---

## Rackaufbau

Der Serverschrank beherbergt sämtliche zentralen Infrastrukturkomponenten.

Hierzu zählen unter anderem:

- Effekta Office RM600 Online-USV
- Brennenstuhl 19"-Steckdosenleiste
- WatchGuard Firebox T20
- HP ProCurve 1810-24G
- YuanLey 5-Port PoE Switch
- Dell OptiPlex 3040 Micro (Proxmox VE)
- Patchpanel
- Raspberry-Pi-Systeme
- Kabelmanagement

Die genaue Höheneinteilung ist im Racklayout (Anhang) dokumentiert.

---

## Verkabelung

Die Netzwerkverkabelung erfolgt vollständig über strukturierte Patchverkabelung innerhalb des Serverschranks.

Kurze Patchkabel die in Rangierpanelen zwischen Patchpanel und aktiven Komponenten geführt werden, sorgen für eine übersichtliche Installation und erleichtern Wartungs- und Erweiterungsarbeiten.

Die Stromversorgung ist innerhalb des Wchranks räumlich getrennt von der Datenverkabelung geführt, um die Übersichtlichkeit zu erhöhen.

---

## Farb- und Kennzeichnungskonzept der Netzwerkverkabelung

Die Farbgebung der Patchkabel dient nicht der Kennzeichnung von VLANs oder IP-Netzen. Stattdessen folgt sie einem funktionsorientierten Konzept, bei dem zusammengehörige Hardwarekomponenten und Infrastrukturbereiche einheitlich gekennzeichnet werden.

Die eindeutige Identifikation einzelner Leitungen erfolgt zusätzlich über **PatchSee-Patchkabel** mit farbigen PatchClips. In Verbindung mit einem **PatchLight** können die integrierten Lichtleiter genutzt werden, um eine Verbindung sowohl am aktiven Netzwerkgerät als auch am Patchpanel innerhalb weniger Sekunden eindeutig zu identifizieren.

### Farbkonzept

| Farbe | Bereich | Beispiele |
|--------|----------|-----------|
| 🔵 Blau | WLAN-Infrastruktur | Firewall ↔ PoE-Switch, PoE-Switch ↔ Patchpanel, RJ45-Dosen ↔ Access Points |
| 🟠 Orange | Servertechnik | HP ProCurve ↔ Dell OptiPlex (Proxmox), HP ProCurve ↔ Raspberry Pi (CheckMK), HP ProCurve ↔ Raspberry Pi (Pi-hole), HP ProCurve ↔ USV |
| 🟡 Gelb | WAN & Telekommunikation | FRITZ!Box ↔ Firebox (WAN), FRITZ!Box ↔ Core-Switch, FRITZ!Box ↔ Gigaset DL500A |
| ⚫ Schwarz | Multimedia | Smart TV, Vodafone TV-Receiver |

---

## PatchSee-System

Der überwiegende Teil der strukturierten Netzwerkverkabelung nutzt PatchSee-Patchkabel mit integrierten Lichtleitfasern.

Mittels eines **PatchLight** können die integrierten Lichtleiter sowohl am aktiven Netzwerkgerät als auch am Patchpanel beleuchtet werden. Dadurch lässt sich die gewünschte Netzwerkverbindung innerhalb weniger Sekunden eindeutig identifizieren, ohne Kabel verfolgen oder abziehen zu müssen.

### Vorteile

- Schnelle Identifikation einzelner Netzwerkverbindungen
- Reduzierter Zeitaufwand bei Wartungs- und Erweiterungsarbeiten
- Minimierung des Risikos, versehentlich das falsche Patchkabel zu trennen
- Unabhängigkeit von einer VLAN- oder Farbcodierung
- Professionelle Leitungsverfolgung innerhalb des Serverschranks

> **Hinweis:** Die eindeutige Identifikation der Netzwerkverbindungen erfolgt über die PatchSee-Technologie und die Dokumentation der Portbelegung. Die Kabelfarbe dient ausschließlich der funktionalen Zuordnung der Infrastrukturkomponenten.

---

## Architekturentscheidung

Der zentrale Einbau sämtlicher Infrastrukturkomponenten in einem 19"-Serverschrank verbessert die Übersichtlichkeit, reduziert Kabellängen und vereinfacht Wartungsarbeiten.

Die Kombination aus strukturierter Patchverkabelung, funktionsorientierter Farbkennzeichnung und PatchSee-Leitungsverfolgung ermöglicht eine schnelle Fehleranalyse und unterstützt den langfristig wartungsfreundlichen Betrieb der Infrastruktur.

---