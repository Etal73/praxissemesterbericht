# Git-Protokolle
[Quelle](https://git-scm.com/book/de/v2/Git-auf-dem-Server-Die-Protokolle)
---
# Lokales Protokoll

- Einfachstes Protokoll, Repository befindet sich in einem Verzeichnis auf dem selben Host
- Wird häufig verwendet, wenn jeder im Team Zugriff auf ein freigegebenes Dateisystem (bspw. NFS-Mount) hat
---
### Klonen
`$ git clone /srv/git/project.git`

oder 

`$ git clone file:///srv/git/project.git` 

 - `file://` lässt Git Prozesse auslösen, welche normalerweise zum Übertragen von Daten über ein Netzwerk verwendet werden. 
	- Wird normalerweise verwendet, wenn eine saubere Kopie des Repositorys mit fremden Referenzen oder weggelassenen Objekten gewünscht ist, bspw. bei einem Import aus einem anderen VCS
	- Langsamer als die erste Variante

---
### Lokales Repository zu einem bestehende Git-Projekt hinzufügen
`$ git remote add lokales_projekt /srv/git/project.git`

---

### Vor- und Nachteile
---
#### Vorteile

- einfache Einrichtung
- verwendet vorhandene Datei- und Netzwerk-Berechtigungen

---

#### Nachteile

- gemeinsamer Zugriff ist i.d.R. schwieriger und langsamer, wenn man den "Server" von mehreren Standorten erreichen möchte

	"Es ist wichtig zu erwähnen, dass es nicht unbedingt die schnellste Option ist, wenn Sie einen gemeinsamen Mount verwenden. Ein lokales Repository ist nur dann schnell, wenn Sie schnellen Zugriff auf die Daten haben. Ein Repository auf NFS-Mounts ist oft langsamer als der Zugriff auf das Repository über SSH auf demselben Server, während Git lokale Festplatten in jedem System nutzt."

---

---
# HTTP Protokolle

### Smart HTTP - "Es ist wahrscheinlich der beliebteste Weg, heute Git zu verwenden"

- Ähnlich zu SSH oder Git Protokoll, läuft aber über Standard HTTPS-Ports
- Kann versch. HTTP-Authentifizierungsmechanismen verwenden
	- Es kann Benutzername/Passort Authetifizierung verwendet werden, anstatt SSH-Schlüssel einrichten zu müssen
- Kann mit einer einzigen URL anonym wie das `git://`-Protokoll oder mit Verschlüsselung wie das SSH-Protokoll betrieben werden. 
	- Server kann bei einem Push oder beim Lesen nach einer Authetifizierung verlangen

---

### Dumb HTTP

- Git Client greift darauf zurück, wenn der Server auf den HTTP Smart Service nicht antworten sollte
- einfache Einrichtung
	- ein leeres Git-Repository unter HTTP-Dokument-Root ablegen und einen `post-update` Hook einrichten
	- Ab da kann jeder, der auch Zugriff auf den Webserver hat, das Repository klonen
- Im Allgemeinen wird ein Smart HTTP-Server zum Lesen/Schreiben betrieben oder die Datei werden als schreibgeschützt im Dumb-Modus zur Verfügung gestellt

---

## Vorteile
- Einfach für den Endbenutzer, da: 
	- eine URL für alle Zugriffsarten 
	- Server-Prompt wird nur bei erforderlicher Authentifizierung gebraucht
- Authetifizierung mit Benutzernamen/Passowrt
- Verschlüsselung und Erzwingung für das Verwenden von bestimmten SSL-Zertifikaten möglich
- HTTP/HTTPS ist weitverbreitet, Firewalls sind oft so eingerichtet, dass sie den Datenverkehr über deren Ports ermöglichen

---

## Nachteile 

- Git über HTTPS kann im Vergleich zu SSH auf einigen Servern etwas komplizierter einzurichten sein
- Bei der verwendung von authetifiziertem Pushen, ist die Bereitstellung der Anmeldeinformationen manchmal komplizierter als die Verwendung von Schlüsseln über SSH
	- Tools wie Credential Manger von Windows vereinfachen das Ganze jedoch

---

# SSH-Protocol

- SSH-Zugriff auf den Server ist in den meisten Fällen bereits eingerichtet und wenn nicht, soll es einfach zu bewerkstelligen sein.
- SSH allgegenwärtig und im Allg. einfach einzurichten und zu verweden 
- `$ git clone ssh://[user@]server/project.git` oder
- `$ git clone [user@]server:project.git`
	- falls der optionale Benutzername nicht angegeben wird, benutzt Git den User mit dem Sie aktuell angemeldet sind

---

## Vorteile
- SSH ist relativ eifnach einzurichten, SSH Daemons sind weit verbreitet
- Zugriff über SSH ist sicher, der gesamte Datentransfer wird verschlüsselt und authentifiziert 
- Genau wie das HTTPS-, Git- oder Local-Protokoll effizient, Daten werden vor der Übertragung so stark wie möglich komprimiert 

---

## Nachteile
- Anonymer Zugriff auf das Git-Repository wird nicht unterstützt 
- Hat ein Benutzer keinen SSH-Zugriff, so er verfügt er nichtmal Lesezugriff auf das Repository

---

# Git Protokoll

- Spezieller Daemon, wird mit Git ausgliefert
- Lauscht auf einen dedizierten Port (9418) 
- Stellt einen dien ähnlich dem des SSH Protokolls bereit, aber ohne jegliche Authentifizierung oder Verschlüsselung
- Damit ein Repository über das Git-Protokoll bedient werden kann, muss eine `git-daemon-export-ok` Datei erstellt werden 
- idR gibt es keinen Push über dieses Protokoll
- Entweder ist das Repository für jeden zum Klonen zugänglich oder für niemanden 
- Push Zugriff kann aktiviert werden, allerdings ist dadurch jedem, der über den Link verfügt, zu diesem Projekt zu pushen.

---

## Vorteile

- oft als erstes Netzwerkübertragungsprotokoll verfügbar
- gleicher Datenübertragunsmechanismus wie das SSH-Protokoll, jedoch ohne den Aufwand für Verschlüsselung und Authetifizierung
- Nützlich für öffentliche Projekte

---

## Nachteile

- Das Git-Protokoll sollte vermieden werden, es sei denn, man weiß, was man tut. 
- das Fehlen von TLS oder einer anderen Verschlüsselung kann das Klonen über "git://" zu der Schwachstelle bei der Ausführung von willkürlichen Codes führen und sollte daher vermieden werden
- Keine Authetifizierung 
- Wahrscheinlich auch das am schwierigsten einzurichtende Protokoll
- Muss seinen eigenen Daemon laufen lassen, der eine `xinetd` oder `systemd` Konfiguration oder derlgeichen erfordert 
- Erfordert Firewallzugang auf Port 9418, welcher kein Standardport ist. 