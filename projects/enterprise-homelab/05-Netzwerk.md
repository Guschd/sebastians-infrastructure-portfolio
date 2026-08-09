# Physische Netzwerkinfrastruktur

## Zielsetzung

Die Netzwerkinfrastruktur bildet das Rückgrat der gesamten IT-Umgebung. Sie verbindet sämtliche aktiven Komponenten miteinander und stellt die Grundlage für Kommunikation, Virtualisierung, Storage, WLAN sowie den Internetzugang dar.

Besonderes Augenmerk wurde auf eine klare Trennung der Aufgabenbereiche, eine strukturierte Verkabelung sowie eine wartungsfreundliche Architektur gelegt.

---

## Netzwerkübersicht

Die physische Netzwerkinfrastruktur besteht aus folgenden Hauptkomponenten:

| Komponente | Aufgabe |
|------------|---------|
| AVM FRITZ!Box | Internetzugang |
| WatchGuard Firebox T20 | Firewall, Routing, VLANs |
| HP ProCurve 1810-24G | Zentraler Core-Switch |
| YuanLey PoE Switch | Versorgung der Access Points |
| Ruckus R500 | WLAN-Infrastruktur |
| Dell OptiPlex 3040 | Virtualisierung (Proxmox VE) |

---

## Internetanbindung

Der Internetzugang erfolgt über einen Vodafone-Kabelanschluss.

Die AVM FRITZ!Box übernimmt die Verbindung zum Provider und stellt die WAN-Schnittstelle für die WatchGuard Firebox bereit.

Sämtlicher Netzwerkverkehr wird anschließend über die Firebox geroutet und durch die Firewall verarbeitet.

---

## Core-Switch

Als zentraler Switch wird ein HP ProCurve 1810-24G eingesetzt.

Der Switch übernimmt unter anderem folgende Aufgaben:

- Verteilung aller kabelgebundenen Netzwerkverbindungen
- VLAN-Transport (802.1Q)
- Verbindung der Serverinfrastruktur
- Anbindung der Firewall
- Verbindung zum PoE-Switch
- Verbindung zum Patchpanel

---

## PoE-Infrastruktur

Die Versorgung der WLAN-Infrastruktur erfolgt über einen YuanLey PoE-Switch.

Über diesen werden sämtliche Access Points mit Daten und Strom versorgt.

Dadurch entfällt die Installation separater Netzteile an den Montageorten.

---

## WLAN-Infrastruktur

Für die drahtlose Netzwerkversorgung kommen vier Ruckus R500 Access Points zum Einsatz.

Die Geräte arbeiten im Unleashed-Verbund und benötigen keinen separaten Hardware-Controller.

Jeder Access Point stellt sämtliche produktiven WLANs bereit und bindet diese über VLAN-Tagging an die Firebox an.

---

## Serveranbindung

Der Dell OptiPlex 3040 Micro ist direkt mit dem HP ProCurve verbunden.

Über diese Verbindung werden sämtliche virtuellen Maschinen sowie die Speicher- und Netzwerkdienste an das Unternehmensnetz angebunden.

---

## Management

Die Administration der aktiven Netzwerkkomponenten erfolgt ausschließlich über das dedizierte Management-VLAN.

Hierzu gehören unter anderem:

- WatchGuard Firebox T20
- HP ProCurve 1810-24G
- YuanLey PoE Switch
- Ruckus Unleashed
- Generex CS141 SNMP Mini
- Proxmox VE

Durch die Trennung vom produktiven Netzwerk wird der administrative Zugriff zusätzlich abgesichert.

---

## Architekturentscheidung

Die physische Netzwerkinfrastruktur folgt einem klassischen Core-Access-Konzept.

Die WatchGuard Firebox übernimmt für bestimmte VLANs Routing- und Sicherheitsfunktionen, während der HP ProCurve als zentraler Verteilerswitch fungiert. 
Der PoE-Switch versorgt ausschließlich die WLAN-Infrastruktur.

Durch diese Aufgabenverteilung bleibt die Infrastruktur übersichtlich, wartungsfreundlich und jederzeit erweiterbar.

---