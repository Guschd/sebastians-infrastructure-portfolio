# 12 Backup- und Wiederherstellungskonzept

## Zielsetzung

Eine zuverlässige Datensicherung ist wesentlicher Bestandteil des Infrastrukturkonzeptes. Ziel ist die Wiederherstellung produktiver Systeme nach Hardwaredefekten, Softwarefehlern oder Fehlkonfigurationen innerhalb eines möglichst kurzen Zeitraums.

Neben der Sicherung der virtuellen Maschinen werden auch anwendungsspezifische Konfigurationen regelmäßig exportiert und separat gespeichert.

---

## Backup-Strategie

Die Datensicherung erfolgt auf mehreren Ebenen.

| Ebene | Sicherungsverfahren |
|--------|---------------------|
| Virtuelle Maschinen | Imagebasierte Backups |
| Anwendungen | Konfigurations- und Datenexporte |
| Dokumentation | Dateibasierte Sicherung |

Dadurch können sowohl vollständige Systeme als auch einzelne Anwendungen unabhängig voneinander wiederhergestellt werden.

---

## Backup-Ziel

Die Proxmox-Backups werden auf einer dedizierten externen Festplatte gespeichert.

|-|-|
| Hersteller | Western Digital |
| Modell | WD Red |
| Kapazität | 500 GB |
| Anschluss | USB |
| Verwendung | Ausschließlich Proxmox-Backups |

Die Backup-Festplatte ist nicht Bestandteil des produktiven Datenspeichers und dient ausschließlich der Datensicherung.

---

## Gesicherte Systeme

Folgende virtuelle Maschinen werden regelmäßig gesichert:

- Home Assistant OS
- OpenMediaVault
- Jellyfin
- i-doit
- Minecraft Server

---

## Anwendungsspezifische Sicherungen

Zusätzlich zu den imagebasierten Sicherungen werden wichtige Anwendungen durch eigene Exportmechanismen gesichert.

Hierzu zählen unter anderem:

- Home Assistant
- i-doit
- OpenMediaVault-Konfiguration

Diese Sicherungen ermöglichen eine Wiederherstellung einzelner Anwendungen unabhängig vom Hypervisor.

---

## Wiederherstellung

Die Wiederherstellung erfolgt über die integrierten Funktionen von Proxmox VE.

Nach Auswahl des gewünschten Sicherungsstandes kann eine virtuelle Maschine vollständig wiederhergestellt werden.

Anwendungsspezifische Backups können zusätzlich innerhalb der jeweiligen Software importiert werden.

---

## Architekturentscheidung

Durch die Kombination aus vollständigen VM-Backups und anwendungsspezifischen Datensicherungen wird ein hohes Maß an Ausfallsicherheit erreicht.

Die physische Trennung von Produktiv- und Sicherungsdaten reduziert das Risiko eines gleichzeitigen Datenverlustes und vereinfacht Wiederherstellungsprozesse im Fehlerfall.

Das Sicherungskonzept orientiert sich an bewährten Verfahren professioneller IT-Infrastrukturen und ermöglicht sowohl die Wiederherstellung kompletter Systeme als auch einzelner Anwendungen.

---