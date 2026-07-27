# Enterprise Homelab

## Architektur- und Betriebsdokumentation

**Version:** 1.0  
**Autor:** Sebastian Besold  
**Stand:** Juli 2026  
**Status:** Final (Work in Progress)

---

# Executive Summary

## Einleitung

Dieses Dokument beschreibt die Planung, den Aufbau und den Betrieb einer privaten IT-Infrastruktur, die sich hinsichtlich Struktur, Dokumentation und Betriebsprozessen an den Standards professioneller Unternehmensnetzwerke orientiert.
Das Homelab die t als Testumgebung zur Bewertung von Technologien, Validierung von Konzepten und Erweiterung meiner praktische Expertise.

Ziel des Projekts war nicht die Errichtung eines klassischen Homelabs zum Experimentieren, sondern der Aufbau einer dauerhaft produktiv betriebenen Infrastruktur mit besonderem Fokus auf Verfügbarkeit, Sicherheit, Wartbarkeit und vollständiger Dokumentation.

Die Infrastruktur übernimmt im täglichen Betrieb unter anderem folgende Aufgaben:

- Zentrale Virtualisierung mittels Proxmox VE
- Netzwerksegmentierung über VLANs
- Firewall- und Routingfunktionen
- Smart-Home-Integration
- Medienbereitstellung
- Netzwerkmonitoring
- Konfigurations- und Inventardokumentation
- Datensicherung
- Flächendeckende WLAN-Versorgung des gesamten Gebäudes

Alle Systeme werden zentral dokumentiert und überwacht. Die Architektur orientiert sich dabei an Konzepten aus mittleren Unternehmensnetzwerken.

---

## Projektziele

Beim Entwurf der Infrastruktur wurden folgende Ziele definiert:

- Ausfallsicherheit zentraler Dienste
- Klare Netzsegmentierung
- Trennung von Benutzer-, Server- und Managementnetzen
- Einfache Wartbarkeit und Störungsidentifikation
- Technische Dokumentation
- Professionelles Monitoring
- Sichere Fernwartung ohne klassische Portfreigaben
- Wirtschaftlicher Einsatz vorhandener Hardware und kostenorientierter Neubewchaffung
- Zukunftssichere Erweiterbarkeit

---

## Infrastrukturübersicht

Die Infrastruktur besteht aus mehreren logisch voneinander getrennten Ebenen.

### Internetanbindung

- Vodafone Coaxial Kabelanschluss
- AVM FRITZ!Box 6591 als Internetrouter

### Perimeterschutz

- WatchGuard Firebox T20

### Switching

- HP ProCurve 1810-24G
- YuanLey 5-Port PoE Switch

### Virtualisierung

- Dell OptiPlex 3040 Micro
- Proxmox VE

### Storage

- OpenMediaVault

### Netzwerkdienste

- Pi-hole
- Home Assistant
- Jellyfin
- Minecraft Server

### Dokumentation

- i-doit Open

### Monitoring

- CheckMK

### Stromversorgung

- Effekta Office RM600 mit Generex CS141 SNMP Mini

---

## Dokumentationsumfang

Diese Dokumentation umfasst sämtliche produktiv betriebenen Komponenten der Infrastruktur einschließlich:

- Hardware
- Netzwerkarchitektur
- VLAN-Konzept
- WLAN-Infrastruktur
- Virtualisierung
- Storage
- Backup
- Monitoring
- Management
- Stromversorgung
- Architekturentscheidungen

Besonderes Augenmerk wurde auf die Nachvollziehbarkeit technischer Entscheidungen sowie auf eine 
wartungsfreundliche Dokumentation gelegt. Ziel ist es, sowohl den aktuellen Aufbau als auch die 
zugrunde liegenden Konzepte und Entwcheidungsprozesse transparent darzustellen.

---

> **Hinweis**
>
> Dieses Dokument zeigt den Zustand der Infrastruktur zum Zeitpunkt der Veröffentlichung. 
> Änderungen an Hard- oder Software können zu Abweichungen gegenüber späteren Versionen führen.

---