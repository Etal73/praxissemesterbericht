## Zurück zur [[Plugin/PluginDokumentation/Übersicht]]

Nachdem das Plugin mit __Maven package__ in eine Jar-Datei verpackt wurde, muss man es mit dem [Warp (Packer)](https://github.com/dgiagio/warp) zu einer Exe umwandeln, damit das StreamDeck es bei Programmstart starten kann. 

Ordner-Struktur "Jar2Exe"
```
├───Jar2Exe
│   └───bundle
│       └───jre
```

Um das zu erreichen, muss man zuerst die Jar-Datei zusammen mit einer JRE(11.0.17) in einen Ordner verschieben (bundle) und anschließend die warp-packer.exe im Ordner Jar2Exe mit folgendem Befehl von der Konsole aus ausführen: 
`.\warp-packer.exe --arch windows-x64 --input_dir bundle --exec run.bat --output plugin.exe
`
Um den Prozess zu vereinfachen, kann man auch ein Batch-Skript schreiben, welches die Jar-Datei automatisch verschiebt, anschließend die warp-packer.exe ausführt und zum Schluss die Ausführbare Exe in den Pluginordner verschiebt. Während der Entwicklung habe ich das folgende Skript benutzt: 
```
@echo off
setlocal

set "taskName=StreamDeck.exe"

taskkill /F /IM %taskName% //Beendet die SD-Software

// Entfernt die alte Version 
del "C:\Users\vitali.sokner\Desktop\StreamDeckBundle\bundle\H3Dplugin.jar"

// Verschiebt die aktuelle Version in den bundle-Ordner
move "C:\Users\vitali.sokner\IdeaProjects\StreamDeck4J3\target\H3Dplugin.jar" "C:\Users\vitali.sokner\Desktop\StreamDeckBundle\bundle"

// Führt den warp-packer aus
.\warp-packer.exe --arch windows-x64 --input_dir bundle --exec run.bat --output plugin.exe

// Verschiebt die Exe in den Plugin-Ordner
move "C:\Users\vitali.sokner\Desktop\StreamDeckBundle\plugin.exe" "C:\Users\vitali.sokner\AppData\Roaming\Elgato\StreamDeck\Plugins\de.howatherm.sdPlugin"

endlocal
```