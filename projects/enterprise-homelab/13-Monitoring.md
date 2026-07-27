# Monitoring und Systemmanagement

## Zielsetzung

Ein kontinuierliches Monitoring der Infrastruktur dient der frühzeitigen Erkennung von Störungen, der Überwachung der Systemverfügbarkeit sowie der Unterstützung bei Wartungs- und Fehleranalyseprozessen.
Neben der Überwachung der Hardware werden auch Netzwerkkomponenten, Serverdienste sowie die Stromversorgung zentral überwacht.

---

## Monitoring-Plattform

Als zentrales Monitoringsystem wird **CheckMK** eingesetzt.

|||
|-|-|
| Software | CheckMK |
| Bereitstellung | Raspberry Pi |
| Aufgabe | Infrastrukturüberwachung |

CheckMK überwacht kontinuierlich den Zustand der produktiven Infrastruktur und informiert bei Abweichungen oder Ausfällen.

---

## Überwachte Systeme

Folgende Komponenten werden zentral überwacht:

- HP ProCurve 1810-24G
- Ruckus Accesspoints
- Proxmox VE
- Raspberry Pi Systeme
- Effekta Office RM600

---

## Überwachte Parameter

Je nach System werden unter anderem folgende Informationen erfasst:

### Netzwerk

- Erreichbarkeit
- Portstatus
- Antwortzeiten

### Server

- CPU-Auslastung
- Arbeitsspeicher
- Datenträgerauslastung
- Temperatur
- Dienste
- Systemlast

### USV

- Netzspannung
- Ausgangsspannung
- Batteriekapazität
- Batteriestatus
- Restlaufzeit
- Last
- Temperatur

---

## Inventarisierung

Die technische Dokumentation der Infrastruktur erfolgt mit **i-doit**.

Erfasst werden unter anderem:

- Netzwerkgeräte
- Virtuelle Maschinen
- IP-Adressen
- VLANs/Netze
- Verkabelung
- Patchfelder
- Dokumentationen

Die Inventarisierung bildet die Grundlage für Wartung, Fehleranalyse und Erweiterungen der Infrastruktur.

---

## Administration

Die Verwaltung der Infrastruktur erfolgt über die jeweils vorgesehenen Managementsysteme.

| System | Verwaltung |
|---------|------------|
| WatchGuard Firebox T20 | WatchGuard System Manager |
| HP ProCurve 1810-24G | Webinterface |
| Ruckus R500 | Ruckus Unleashed |
| Proxmox VE | Proxmox Webinterface |
| CheckMK | Webinterface |
| i-doit | Webinterface |
| Effekta Office RM600 | Generex CS141 SNMP Mini |

Der Zugriff auf sämtliche Administrationsoberflächen erfolgt ausschließlich über das Management-VLAN.

---

## Architekturentscheidung

Durch die Kombination aus zentralem Monitoring und vollständiger Inventarisierung wird eine hohe Transparenz über den Zustand der gesamten Infrastruktur erreicht.
Störungen können frühzeitig erkannt und gezielt analysiert werden. Gleichzeitig bildet die zentrale Dokumentation die Grundlage für Wartungsarbeiten, Erweiterungen sowie die langfristige Nachvollziehbarkeit technischer Entscheidungen.
Das Monitoring- und Managementkonzept orientiert sich an bewährten Verfahren professioneller Unternehmensnetzwerke und unterstützt einen stabilen und wartungsfreundlichen Betrieb der Infrastruktur.

---