# Stromversorgung und unterbrechungsfreie Stromversorgung

## Zielsetzung

Die Stromversorgung der produktiven Infrastruktur erfolgt zentral über eine Online-USV. Ziel ist der Schutz vor Spannungsschwankungen, Netzausfällen sowie kurzzeitigen Unterbrechungen der Stromversorgung.

Durch die unterbrechungsfreie Versorgung zentraler Netzwerkkomponenten bleibt die Infrastruktur auch bei einem Stromausfall kontrolliert erreichbar und kann geordnet heruntergefahren werden.

---

## Stromversorgung

Die elektrische Versorgung erfolgt über einen separat abgesicherten Stromkreis.

Der Strompfad ist wie folgt aufgebaut:

```text
Hausverteilung
        │
        ▼
B16-Leitungsschutzschalter
        │
        ▼
Schutzkontaktsteckdose
        │
        ▼
Effekta Office RM600 Online-USV
        │
        ▼
19"-Brennenstuhl-PDU
        │
        ├── WatchGuard Firebox T20
        ├── HP ProCurve 1810-24G
        ├── YuanLey PoE Switch
        ├── Dell OptiPlex 3040 Micro
        ├── LogiLink USB-Netzteil (Raspberry Pi)
        └── LogiLink USB-Netzteil (Raspberry Pi)
```

---

## Unterbrechungsfreie Stromversorgung

Zum Schutz der Infrastruktur wird eine **Effekta Office RM600 Online-USV** eingesetzt.

### Technische Daten
|||
|-|-|
| Hersteller | Effekta |
| Modell | Office RM600 |
| Bauform | 19"-Rack |
| Höheneinheiten | 2 HE |
| USV-Typ | Online-USV (Double Conversion) |

Die USV übernimmt die permanente Versorgung sämtlicher zentraler Infrastrukturkomponenten.

---

## Netzwerkmanagement

Zur Fernüberwachung ist die USV mit einer **Generex CS141 SNMP Mini** ausgestattet.

### Funktionen

- SNMP-Monitoring
- Weboberfläche
- Ereignisprotokollierung
- Netzwerkmanagement
- Alarmierung

Die Managementkarte befindet sich im Management-VLAN und wird durch CheckMK überwacht.

---

## Verbraucher

Folgende Systeme werden über die USV versorgt:

- WatchGuard Firebox T20
- HP ProCurve 1810-24G
- YuanLey PoE Switch
- Dell OptiPlex 3040 Micro (Proxmox VE)
- LogiLink USB-Netzteil (Raspberry Pi – Pi-hole)
- LogiLink USB-Netzteil (Raspberry Pi – CheckMK)

---

## Monitoring

Die Überwachung erfolgt zentral durch CheckMK.

Erfasst werden unter anderem:

- Eingangsspannung
- Ausgangsspannung
- Batteriekapazität
- Batteriestatus
- Restlaufzeit
- Last
- Temperatur
- Ereignisse

---

## Architekturentscheidung

Bei der Auswahl der USV standen neben der technischen Ausstattung insbesondere die Einbautiefe und das Preis-Leistungs-Verhältnis im Vordergrund.

Viele Rack-USV-Systeme besitzen eine Gehäusetiefe von über 45 cm und eignen sich daher nur eingeschränkt für kompakte Netzwerkschränke. Die Effekta Office RM600 verfügt dagegen über eine vergleichsweise geringe Einbautiefe von rund 30 cm und lässt sich dadurch problemlos im vorhandenen Rack integrieren.

Die USV konnte für etwa 148 € netto beschafft werden und stellte damit eine wirtschaftliche Alternative zu deutlich teureren Enterprise-Systemen dar.

Zur Netzwerkanbindung wurde eine Generex CS141 SNMP Mini verwendet. Der reguläre Neupreis liegt bei etwa 289 €, die Managementkarte konnte jedoch gebraucht für rund 80 € erworben werden.

Durch diese Kombination konnte mit überschaubarem Budget eine professionelle, netzwerkfähige USV-Lösung realisiert werden, die sämtliche Anforderungen hinsichtlich Verfügbarkeit, Überwachung und Wartbarkeit erfüllt.

---