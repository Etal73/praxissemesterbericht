## [[API-Dokumentation]]

Methode wird aufgerufen mit 
```Java
api.setSettings(Kontext, jsonObject)
```
den Kontext erhält man durch:   
```Java
event.getContext()
```
jedes Event trägt den Kontext mit sich

das JsonObject legt man folgendermaßen an: 
```Java
JsonObject settingsObject = new JsonObject();
settingsObject.addProperty("makro", makro);
```
die addProperty()-Methode hat einmal den __Namen__ der Eigenschaft als Eingabeparameter("makro") und einmal den __Wert__, welcher vom Bool, String, Number/Int oder Character Datentyp sein muss. 
