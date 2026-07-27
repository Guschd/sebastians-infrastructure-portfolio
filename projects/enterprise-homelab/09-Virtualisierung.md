# Virtualisierung

## Zielsetzung

Die Virtualisierung bildet das Herzstück der gesamten Infrastruktur. Sämtliche zentralen Netzwerk- und Serverdienste werden als virtuelle Maschinen auf einem gemeinsamen Hypervisor betrieben.

Durch die Konsolidierung mehrerer Systeme auf einer Hardwareplattform werden Ressourcen effizient genutzt, Wartungsarbeiten vereinfacht und Datensicherungen zentralisiert.

---

## Hypervisor

Als Virtualisierungsplattform kommt **Proxmox Virtual Environment (VE)** zum Einsatz.

|||
|--------------|------|
| Hypervisor | Proxmox VE |
| Hostsystem | Dell OptiPlex 3040 Micro |
| Prozessor | Intel Core i5 |
| Arbeitsspeicher | 16 GB DDR3 SO-DIMM |
| Bootlaufwerk | 128 GB SATA SSD |
| VM-Datenspeicher | 128 GB PCIe NVMe SSD |

---

## Speicheraufteilung

Die Speicherressourcen wurden bewusst getrennt.

| Speicher | Verwendung |
|-----------|------------|
| **local** | Betriebssystem, ISO-Abbilder, Templates und Konfigurationsdaten |
| **local-lvm** | Virtuelle Festplatten sämtlicher virtueller Maschinen |

Da der Dell OptiPlex 3040 Micro nicht von einer NVMe-SSD booten kann, erfolgt der Systemstart über die SATA-SSD. Die virtuelle Infrastruktur nutzt hingegen die performantere NVMe-SSD als primären Datenspeicher.

---

## Netzwerkanbindung

Der Hypervisor ist über den HP ProCurve 1810-24G an die zentrale Netzwerkinfrastruktur angebunden.

Die Anbindung erfolgt als VLAN-Trunk, wodurch sämtliche virtuellen Maschinen direkt den jeweiligen Netzwerksegmenten zugeordnet werden können.

Das Routing zwischen den VLANs übernimmt ausschließlich die WatchGuard Firebox T20.

---

## Administration

Die Administration des Hypervisors erfolgt ausschließlich über das dedizierte Management-VLAN.

Administrative Zugriffe erfolgen von autorisierten oder dem Management VLAN zugehörigen Endgeräten.

Der Internetzugriff ist für das Netz standardmäßig deaktiviert. Für Systemaktualisierungen wird bei Bedarf temporär eine Firewallregel (**Any → Any**) aktiviert und nach Abschluss der Aktualisierung wieder entfernt.

---

## Backup

Die Datensicherung erfolgt über die integrierte Backup-Funktion von Proxmox VE.

Die Sicherungen werden auf einer dedizierten externen **Western Digital WD Red (500 GB)** gespeichert.

Dadurch sind Produktiv- und Sicherungsdaten physisch voneinander getrennt.

---

## Monitoring

Der Hypervisor wird kontinuierlich durch **CheckMK** überwacht.

Hierbei werden unter anderem folgende Parameter erfasst:

- CPU-Auslastung
- Arbeitsspeicher
- Datenträgerauslastung
- SMART-Status
- Netzwerk
- Verfügbarkeit
- Dienste

---

## Architekturentscheidung

Proxmox VE bietet eine leistungsfähige und zugleich wirtschaftliche Virtualisierungsplattform für kleine und mittlere Infrastrukturen.

Die Trennung von Betriebssystem und VM-Datenspeicher verbessert die Wartbarkeit und ermöglicht eine optimale Nutzung der vorhandenen Hardware. Durch die zentrale Virtualisierung können sämtliche produktiven Dienste effizient betrieben, überwacht und gesichert werden.

Die gewählte Architektur orientiert sich an etablierten Virtualisierungskonzepten im Enterprise-Umfeld und bildet die Grundlage für den zuverlässigen Betrieb der gesamten Infrastruktur.

---