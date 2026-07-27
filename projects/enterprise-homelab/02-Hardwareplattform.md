# 2 Hardwareplattform

## Zielsetzung

Die Hardwareplattform bildet die Grundlage der gesamten IT-Infrastruktur. Bei der Auswahl der Komponenten standen Zuverlässigkeit, Energieeffizienz, kompakte Bauform sowie ein wirtschaftlicher Betrieb im Vordergrund.

Anstelle spezialisierter Serverhardware wurde bewusst auf bewährte Business-Hardware gesetzt. Dadurch konnten professionelle Funktionen mit einem vergleichsweise geringen Investitionsaufwand realisiert werden.

---

## Virtualisierungshost

Die zentrale Virtualisierungsplattform basiert auf einem Dell OptiPlex 3040 Micro. Das System übernimmt den Betrieb sämtlicher produktiver virtueller Maschinen und bildet das Herzstück der Infrastruktur.

| Eigenschaft | Wert |
|-------------|------|
| Hersteller | Dell |
| Modell | OptiPlex 3040 Micro |
| Hypervisor | Proxmox VE |
| Prozessor | Intel Core i5 |
| Arbeitsspeicher | 16 GB DDR3 SO-DIMM |
| Bootmedium | 128 GB SATA SSD |
| VM-Datenspeicher | 128 GB PCIe NVMe SSD |

---

## Speicherkonzept

Aufgrund einer hardwarebedingten Einschränkung des Dell OptiPlex 3040 erfolgt der Systemstart ausschließlich von der SATA-SSD. Die Speicheraufteilung wurde daher bewusst so gewählt, dass Betriebssystem und virtuelle Maschinen voneinander getrennt werden.

| Proxmox-Speicher | Physischer Datenträger | Verwendung |
|------------------|------------------------|------------|
| **local** | 128 GB SATA SSD | Proxmox VE, ISO-Abbilder, LXC-/Container-Templates sowie System- und Konfigurationsdaten |
| **local-lvm** | 128 GB PCIe NVMe SSD | Virtuelle Festplatten sämtlicher virtueller Maschinen |

Die SATA-SSD übernimmt ausschließlich die System- und Verwaltungsaufgaben des Hypervisors, während die PCIe-NVMe-SSD den performanten Speicher für alle virtuellen Maschinen bereitstellt.

---

## Backup-Speicher

Die Sicherung der Virtualisierungsplattform erfolgt auf eine dedizierte externe Festplatte, welche dauerhaft am Proxmox-Host eingebunden ist.

| Eigenschaft | Wert |
|-------------|------|
| Hersteller | Western Digital |
| Baureihe | WD Red |
| Kapazität | 500 GB |
| Anschluss | USB |
| Verwendung | Proxmox-Backups |

Die Backup-Festplatte wird ausschließlich zur Datensicherung verwendet und ist nicht Bestandteil des produktiven VM-Speichers.

---

## Architekturentscheidung

Die Hardware wurde unter Berücksichtigung von Leistung, Energieverbrauch, Wartbarkeit und Kosten ausgewählt.

Durch die Trennung von Bootlaufwerk und VM-Datenspeicher profitieren die virtuellen Maschinen von den höheren I/O-Leistungen der NVMe-SSD, während das Betriebssystem des Hypervisors unabhängig davon auf der SATA-SSD betrieben wird.

Der Einsatz einer dedizierten externen Backup-Festplatte ermöglicht eine klare Trennung zwischen Produktiv- und Sicherungsdaten und vereinfacht sowohl Wartungsarbeiten als auch Wiederherstellungsprozesse.

Die gewählte Plattform bietet ausreichend Leistungsreserven für den produktiven Betrieb der vorhandenen Dienste und lässt gleichzeitig zukünftige Erweiterungen innerhalb der vorhandenen Hardware zu.

---