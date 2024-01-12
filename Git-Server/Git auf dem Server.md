[Quelle](https://git-scm.com/book/de/v2/Git-auf-dem-Server-Git-auf-einem-Server-einrichten)

- bestehendes Repository in ein neues Bare-Repository exportieren
	- = Repository ohne Arbeitsverzeichnis
	- `$ git clone --bare my_project my_project.git`
- ###### Bare-Repository auf einen Server ablegen
	- leere Kopie auf einen Serverablegen und Protokolle einrichten
	- ANNAHME: Es existiert ein Server `git.example.com` und SSH-Zugriff auf diesen Server ist vorhanden, Das Verzeichnis: `/srv/git` existiert ebenfalls  
		- neues Repository wird eingerichtet in dem das leere Repository kopiert wird:
			- `$ scp -r my_project.git user@git.example.com:/srv/git`
		- Ab diesem Zeitpunkt können andere Benutzer die SSH-basierten Lesezugriff auf das VZ haben, das Repository klonen in dem sie Folgendes aufrufen:
			- `$ git clone user@git.example.com:/srv/my_project.git`
		- Wenn sich ein Nutzer über SSH auf den Server einloggt und Schreibrechte auf das VZ hat, so hat er automatisch auch Push-Rechte
	- Schreibrechte für Gruppen wreden automatisch zu einem Repository hinzugefügt, wenn der Befehl `git init` mit der Option `--shared` ausgeführt wird.
		- Durch die Ausführung des Befehls werden keine Commits, Refs usw während des Prozesses zertört
		   `$ ssh user@git.example.com`
		   `$ cd /srv/git/my_project.git`
		   `$ git init --bare --shared`
	- Von nun an ist es möglich mit allen Personen mit SSH-Zugriff am Projekt mitzuwirken

Kompliziert soll es erst bei der Einrichtung der Benutzerverwaltung. 
Wenn einige Repositories für bestimmte Nutzer schreibgeschützt und für andere lesend und schreibend sind, können Zugriff und Berechtigungen etwas schwieriger zu realisieren sein. 