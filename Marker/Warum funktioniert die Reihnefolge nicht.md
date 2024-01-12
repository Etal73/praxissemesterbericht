- Bild wird geladen.
	- File-Objekt != null dann lade das Bild aufs Canvas
- Koordinaten werden erfasst 
	- onMouseDown werden die X/Y Koordinaten in einer Liste 
	- während mouseDown werden alle X/Y Koordinaten in einer Liste gespeichert
	- ab mouseReleased werden X/Y Koordinaten nicht mehr erfasst
	- mouseReleased triggert safeKoords()
- Erfasste Koordinaten werden gespeichert in einer Liste
	- Schaut sich die globale Liste "koords" an, falls diese nicht leer ist, wird das erste und letzte Element aus der Liste "koords", der Liste "rechtecke" hinzugefügt
	- anschließend wird die globale Liste "koords" geleert und es können wieder die nächsten Koordinaten erfasst werden. 
- Beim Drücken von "Einzeichnen"
	- Methode drawRectangle() wird ausgeführt 
		- Werte werden gesetzt 
		- for schleife wird eingeleitet 
			- werte werden gesetzt 

**FAZIT: KEINE AHNUNG** 