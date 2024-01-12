## [[API-Dokumentation]]
Methode zum Senden von Daten an den [[Property Inspector]]
![[Pasted image 20231031155730.png]]
das JsonObject legt man folgendermaßen an: 
```Java
JsonObject settingsObject = new JsonObject();
settingsObject.addProperty("makro", makro);
```
die addProperty()-Methode hat einmal den __Namen__ der Eigenschaft als Eingabeparameter("makro") und einmal den __Wert__, welcher vom Bool, String, Number/Int oder Character Datentyp sein muss. 
