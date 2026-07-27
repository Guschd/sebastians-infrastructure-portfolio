# Storage und Dateidienste

## Zielsetzung

Die zentrale Datenspeicherung erfolgt über einen dedizierten Netzwerkspeicher auf Basis von OpenMediaVault. Ziel ist die zentrale Bereitstellung gemeinsamer Datenbestände sowie die Trennung von Anwendungsdaten und der Virtualisierungsplattform.
Durch die Nutzung standardisierter Netzwerkprotokolle können verschiedene Betriebssysteme und Dienste auf dieselben Daten zugreifen.

---

## Storage-Plattform

Als Netzwerkspeicher kommt **OpenMediaVault** zum Einsatz.

|||
|--------------|------|
| Betriebssystem | Debian |
| Plattform | OpenMediaVault |
| Bereitstellung | Virtuelle Maschine |
| Aufgabe | Zentrale Dateifreigaben |

---

## Netzwerkfreigaben

Der Dateiserver stellt folgende Freigaben bereit.

| Freigabe | Verwendung | Protokolle |
|-----------|------------|------------|
| Backup | Datensicherungen | SMB, NFS |
| Music | Mediendateien | SMB, NFS |
| STL | 3D-Druck-Projekte | SMB, NFS |

---

## Zugriffssteuerung

Der Zugriff auf sämtliche Netzwerkfreigaben erfolgt ausschließlich nach erfolgreicher Benutzerauthentifizierung.
Nicht authentifizierte Zugriffe sind nicht möglich.
Die Berechtigungen werden zentral innerhalb von OpenMediaVault verwaltet.

---

## Integration

Der Dateiserver wird von mehreren Diensten der Infrastruktur genutzt.

Unter anderem greifen folgende Systeme auf die bereitgestellten Freigaben zu:

- Jellyfin
- Proxmox Backup
- Arbeitsplatzrechner
- Mobile Endgeräte

Durch die zentrale Speicherung werden doppelte Datenbestände vermieden und die Administration vereinfacht.

---

## Unterstützte Protokolle

Zur Bereitstellung der Netzwerkfreigaben werden folgende Protokolle eingesetzt.

- SMB/CIFS
- NFS

Dadurch können sowohl Windows- als auch Linux-Systeme problemlos auf die Daten zugreifen.

---

## Architekturentscheidung

OpenMediaVault bietet eine stabile und ressourcenschonende Plattform für zentrale Dateidienste.
Die Bereitstellung als virtuelle Maschine ermöglicht eine einfache Datensicherung sowie eine flexible Erweiterung der Speicherinfrastruktur.
Durch die Nutzung standardisierter Netzwerkprotokolle bleibt der Dateiserver unabhängig von den eingesetzten Clientbetriebssystemen und integriert sich nahtlos in die bestehende Infrastruktur.

---