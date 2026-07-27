# Virtuelle Maschinen

## Zielsetzung

Sämtliche produktiven Serverdienste werden als eigenständige virtuelle Maschinen auf dem Proxmox-Hypervisor betrieben.

Die Trennung der Dienste erhöht die Stabilität, vereinfacht Wartungsarbeiten und ermöglicht unabhängige Datensicherungen sowie Wiederherstellungen einzelner Systeme.

Jede virtuelle Maschine übernimmt eine klar definierte Aufgabe innerhalb der Infrastruktur.

---

## Übersicht

| Virtuelle Maschine | Betriebssystem | Aufgabe |
|--------------------|---------------|----------|
| Home Assistant | Home Assistant OS | Gebäudeautomation |
| OpenMediaVault | Debian | Netzwerkspeicher |
| Jellyfin | Ubuntu Server | Medienserver |
| i-doit | Debian Server | IT-Dokumentation |
| Minecraft Server | Debian Server | Gameserver |

---

## Home Assistant

|||
|--------------|------|
| Betriebssystem | Home Assistant OS |
| Aufgabe | Smart Home Zentrale |
| Netzwerk | VLAN 30 – IoT |

Home Assistant bildet die zentrale Automatisierungsplattform des Smart Homes.

Die Integration erfolgt ausschließlich über lokale Netzwerkdienste. Für den externen Zugriff wird ein Cloudflare Tunnel verwendet, wodurch keine eingehenden Portfreigaben an der Firewall erforderlich sind.

---

## OpenMediaVault

|||
|--------------|------|
| Betriebssystem | Debian |
| Aufgabe | Netzwerkspeicher |
| Netzwerk | Servernetz |

OpenMediaVault stellt zentrale Dateifreigaben für die Infrastruktur bereit.

Freigegebene Verzeichnisse:

- Backup
- Music
- STL

Die Bereitstellung erfolgt über SMB und NFS. Der Zugriff ist ausschließlich authentifizierten Benutzern gestattet.

---

## Jellyfin

|||
|--------------|------|
| Betriebssystem | Ubuntu Server |
| Aufgabe | Medienserver |
| Netzwerk | VLAN 20 |

Jellyfin dient der zentralen Bereitstellung von Filmen, Serien und Musik innerhalb des Heimnetzwerks.

Die Mediendateien werden über OpenMediaVault eingebunden.

---

## i-doit

|||
|--------------|------|
| Betriebssystem | Debian Server |
| Aufgabe | Configuration Management Database (CMDB) |
| Netzwerk | Management |

i-doit dokumentiert sämtliche Komponenten der Infrastruktur.

Erfasst werden unter anderem:

- Netzwerkgeräte
- Server
- Virtuelle Maschinen
- Patchfelder
- Verkabelung
- IP-Adressen
- Dokumente

Die CMDB dient als zentrale technische Dokumentation der gesamten Infrastruktur.

---

## Minecraft Server

|||
|--------------|------|
| Betriebssystem | Debian Server |
| Aufgabe | Multiplayer-Spieleserver |
| Netzwerk | VLAN 20 |

Der Minecraft-Server wird als eigenständige virtuelle Maschine betrieben und ist logisch vom übrigen Netzwerk getrennt.

---

## Architekturentscheidung

Die konsequente Trennung der einzelnen Dienste auf eigenständige virtuelle Maschinen erhöht die Betriebssicherheit und erleichtert Wartungs- sowie Backupprozesse erheblich.

Ausfälle oder Konfigurationsänderungen einzelner Systeme wirken sich dadurch nicht unmittelbar auf andere Dienste aus.

Durch die Virtualisierung können sämtliche Anwendungen ressourcenschonend auf einer gemeinsamen Hardwareplattform betrieben werden, ohne auf die Vorteile einer klar strukturierten Serverlandschaft verzichten zu müssen.

---