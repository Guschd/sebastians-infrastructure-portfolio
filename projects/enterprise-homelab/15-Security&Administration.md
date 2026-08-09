# Security, Administration und Betrieb

Das Enterprise Homelab ist keine isolierte Spielumgebung, sondern eine
produktionsnahe Infrastruktur, in der Dienste dauerhaft betrieben,
Änderungen kontrolliert durchgeführt und neue Technologien unter
realistischen Bedingungen getestet werden.

Die Sicherheits- und Betriebsentscheidungen orientieren sich deshalb
nicht ausschließlich daran, ob etwas technisch möglich ist. Entscheidend
ist vielmehr, ob eine Lösung im Alltag wartbar, nachvollziehbar und
wirtschaftlich sinnvoll betrieben werden kann.

---

## Administrative Arbeitsplätze

Für die Administration werden bewusst nur wenige Geräte verwendet.

Das MacBook dient sowohl der privaten Nutzung als auch gelegentlichen
administrativen Aufgaben. Die installierte Software ist auf die tatsächlich
benötigten Werkzeuge begrenzt.

Dazu gehören unter anderem:

- LibreOffice
- Firefox
- NetSpot
- SQuirreL SQL
- FileZilla
- Angry IP Scanner
- WireGuard
- Apple-Entwicklungs- und Administrationswerkzeuge

Das MacBook wird außerdem für die Verwaltung und Pflege der vorhandenen
iPads und iPods verwendet, beispielsweise für Softwareupdates und die
Übertragung von Musik.

Für speziellere administrative Aufgaben steht ein ThinkPad X230 zur
Verfügung.

Das Gerät besitzt zwei physisch getrennte Laufwerke und damit zwei
bewusst getrennte Arbeitsumgebungen.

### Windows 11

Auf der mSATA-SSD befindet sich eine bewusst stark reduzierte
Windows-11-Installation.

Nicht benötigte Windows-Komponenten und vorinstallierte Anwendungen
wurden entfernt beziehungsweise deaktiviert. Das System ist damit kein
allgemeiner Arbeitsplatz, sondern eine möglichst kleine Werkzeugumgebung
für Aufgaben, für die Windows beziehungsweise herstellerspezifische
Software benötigt wird.

Installiert sind unter anderem:

- LibreOffice
- Firefox
- WatchGuard System Manager
- PuTTY
- WinSCP
- FlipperZero-Lab
- WireGuard

Die Systempartition ist mit BitLocker verschlüsselt.

Ein wesentlicher Grund für die separate Windows-Umgebung ist der
WatchGuard System Manager. Für diesen steht keine vergleichbare native
Variante für macOS oder Linux zur Verfügung.

### Zorin OS

Auf der zweiten, klassischen 2,5"-SATA-Festplatte befindet sich Zorin OS.

Die Installation basiert weitgehend auf der Standardinstallation und
wurde nur um die für die technische Arbeit benötigten Werkzeuge ergänzt.

Unter anderem wird FlipperZero-Lab verwendet.

Die Linux-Umgebung stellt darüber hinaus native Werkzeuge zur Verfügung,
die für Netzwerkadministration und Security-Tests sinnvoll sind,
beispielsweise Nmap und Hashcat.

Auch diese Arbeitsumgebung verwendet verschlüsselten Speicher.

Die Aufteilung des ThinkPad ist damit bewusst gewählt:

```text
ThinkPad X230
│
├── mSATA
│   └── Windows 11 / BitLocker
│       └── Windows- und Herstellerwerkzeuge
│
└── 2,5" SATA
    └── Zorin OS
        └── Linux-/Unix-Administration