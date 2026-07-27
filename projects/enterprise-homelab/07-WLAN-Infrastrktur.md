# 7 WLAN-Infrastruktur

## Zielsetzung

Die drahtlose Netzwerkinfrastruktur stellt eine flächendeckende Versorgung des gesamten Wohngebäudes mit mehreren logisch getrennten WLAN-Netzen bereit. Durch den Einsatz von VLAN-Tagging werden die verschiedenen SSIDs den jeweiligen Netzwerksegmenten zugeordnet, wodurch eine klare Trennung zwischen Client-, IoT-, Homeoffice- und Managementnetz erreicht wird.

Das WLAN ist vollständig in die bestehende Sicherheitsarchitektur integriert und orientiert sich hinsichtlich Aufbau und Administration an professionellen Enterprise-Netzwerken.

---

## Hardware

Für die WLAN-Versorgung werden vier Access Points des Typs **Ruckus R500** eingesetzt.

| Eigenschaft | Wert |
|--------------|------|
| Hersteller | Ruckus Wireless |
| Modell | R500 |
| Betriebsmodus | Unleashed |
| Anzahl | 4 |
| Stromversorgung | Power over Ethernet (PoE) |

Die Access Points arbeiten im **Ruckus Unleashed**-Verbund. Dadurch entfällt der Einsatz eines separaten WLAN-Controllers, während zentrale Konfiguration, Firmwareverwaltung und Roaming dennoch unterstützt werden.

---

## Standortplanung

Die Positionierung der Access Points erfolgte auf Grundlage einer WLAN-Ausleuchtung des Gebäudes.

Zur Ermittlung der optimalen Montagepositionen wurde ein **TP-Link TL-WA901ND** auf einer ausziehbaren Teleskopstange befestigt. Dadurch konnte die spätere Montagehöhe eines Access Points simuliert werden, ohne die produktive WLAN-Infrastruktur mehrfach ummontieren zu müssen.

Die Signalstärken wurden anschließend mit **NetSpot** auf einem **MacBook Pro (2014)** gemessen und dokumentiert.

Dieses Verfahren ermöglichte eine realitätsnahe Planung der Access-Point-Standorte sowie eine Optimierung der Funkversorgung vor der endgültigen Installation.

---

## SSIDs

Die folgenden drahtlosen Netzwerke werden bereitgestellt.

| SSID | VLAN | Verwendung |
|------|------|------------|
| WLAN-Allgemein | VLAN 10 | Standardnetz |
| WLAN-Kinder | VLAN 20 | Kindernetz |
| WLAN-MD | VLAN 30 | IoT |
| WLAN-Office | VLAN 40 | Homeoffice |
| WLAN-MGMT *(Hidden)* | VLAN 41 | Administration |

---

## VLAN-Zuordnung

Alle SSIDs werden mittels IEEE 802.1Q VLAN-Tagging an die **WatchGuard Firebox T20** angebunden.

Die Access Points selbst befinden sich im Managementnetz und stellen ausschließlich die Funkinfrastruktur bereit.

Das Routing zwischen den VLANs erfolgt ausschließlich über die Firewall.

---

## Administration

Die Administration der WLAN-Infrastruktur erfolgt zentral über **Ruckus Unleashed**.

Konfiguriert werden unter anderem:

- Access Points
- SSIDs
- VLAN-Zuordnungen
- Firmware
- Funkkanäle
- Sendeleistung
- Client-Statistiken

Der Zugriff auf die Administrationsoberfläche ist ausschließlich aus dem Management-VLAN möglich.

---

## Architekturentscheidung

Der Einsatz von **Ruckus Unleashed** ermöglicht den Betrieb einer Controller-basierten WLAN-Infrastruktur ohne zusätzliche Hardware.
Die Kombination aus mehreren Access Points, VLAN-Tagging und zentraler Administration gewährleistet eine hohe Flexibilität, eine vollständige Trennung der Netzwerksegmente sowie eine flächendeckende WLAN-Versorgung des gesamten Gebäudes.
Die zuvor durchgeführte WLAN-Ausleuchtung mit NetSpot ermöglichte eine optimale Platzierung der Access Points und trägt zu einer gleichmäßigen Funkversorgung bei.

---