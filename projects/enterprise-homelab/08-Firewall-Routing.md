# Firewall und Routing

## Zielsetzung

Die zentrale Netzwerksegmentierung sowie sämtliche Routing- und Sicherheitsfunktionen werden durch eine **WatchGuard Firebox T20** übernommen.

Neben der Trennung der einzelnen VLANs stellt die Firewall den kontrollierten Internetzugang, die VPN-Anbindung sowie die Kommunikation zwischen ausgewählten Netzwerksegmenten sicher.

Das Sicherheitskonzept basiert auf dem Grundsatz **"Default Deny"**. Verbindungen zwischen VLANs werden grundsätzlich blockiert und ausschließlich über dokumentierte Firewallregeln freigegeben.

---

## Hardware

|||
|--------------|------|
| Hersteller | WatchGuard |
| Modell | Firebox T20 |
| Aufgabe | Firewall, Routing, VPN, VLAN-Gateway |

---

## Aufgaben der Firewall

Die WatchGuard Firebox T20 übernimmt innerhalb der Infrastruktur folgende Aufgaben:

- Routing zwischen den VLANs
- Stateful Firewall
- Paketfilter
- Network Address Translation (NAT)
- DHCP für ausgewählte VLANs
- Netzwerksegmentierung
- Zentrale Sicherheitsrichtlinien

---

## Routing

Sämtliche VLANs werden auf der WatchGuard Firebox T20 terminiert.

Dadurch befindet sich jedes Netzwerk in einer eigenen Broadcast-Domäne. Ein direkter Datenverkehr zwischen den VLANs ist standardmäßig nicht möglich.

Kommunikationsbeziehungen werden ausschließlich über explizite Firewallregeln definiert.

---

## Sicherheitskonzept

Das Regelwerk orientiert sich am Prinzip der minimalen Berechtigungen.

Grundsätzlich gilt:

- Kein VLAN kommuniziert direkt mit einem anderen VLAN.
- Jeder Zugriff muss explizit erlaubt werden.
- Nicht definierter Netzwerkverkehr wird verworfen.

Dieses Verfahren reduziert die Angriffsfläche erheblich und verhindert eine unkontrollierte Ausbreitung von Schadsofteare dirch kompromittierte Systeme.

---

## Dokumentierte Firewall-Ausnahmen

Zur Gewährleistung des Produktivbetriebs wurden einzelne Kommunikationsbeziehungen bewusst freigegeben.

| Regel | Quelle | Ziel | Zweck |
|--------|---------|------|-------|
| B-01 | Management | Pi-hole | DNS-Auflösung |
| B-02 | Management | Alle VLANs | Temporäre Any→Any-Regel ausschließlich für Proxmox-Systemupdates |
| B-03 | Home Assistant | Proxmox VE | API-Zugriff |
| B-04 | Cloudflare Tunnel | Home Assistant | Sicherer Remotezugriff |
| B-05 | Clients | OpenMediaVault | SMB- und NFS-Freigaben |

Alle weiteren Kommunikationsbeziehungen bleiben standardmäßig blockiert.

---

## VPN

- Könnte über die Firebox per SSLVPN oder OpenVPN abgebildet werden, wird aber altuell aufgrund bereits existerendem Wireguard nicht benötigt.

## Administration

Die Administration der Firewall erfolgt ausschließlich aus dem Management-VLAN.

Hierfür wird der **WatchGuard System Manager** verwendet.

---

## Architekturentscheidung

Die WatchGuard Firebox T20 bildet den zentralen Sicherheitsanker der gesamten Infrastruktur.

Durch die Kombination aus VLAN-Routing, Stateful Firewall, VPN und zentralem Regelwerk werden sämtliche Kommunikationsbeziehungen kontrolliert und dokumentiert.

Die Umsetzung des **Default-Deny-Prinzips** sorgt dafür, dass ausschließlich ausdrücklich freigegebene Verbindungen zwischen den einzelnen Netzwerksegmenten möglich sind und entspricht damit bewährten Sicherheitskonzepten professioneller Unternehmensnetzwerke.

---