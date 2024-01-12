## Wie man switchToProfile verwendet: 
1. Profile anlegen
3. Profile exportieren und ins Plugin-VZ verschieben
4. Profile dem Plugin "zuweisen", indem man diese im manifest.json ergänzt 
``` JSON
"SDKVersion": 2,
  "Software": {
    "MinimumVersion": "6.0"
  },
  "Profiles": [
    {
      "Name":"Elite Dangerous Main XL",
      "ReadOnly":false,
      "DeviceType":2,
      "DontAutoSwitchWhenInstalled":false
    },
    {
      "Name":"Elite Dangerous HardPoints XL",
      "ReadOnly":false,
      "DeviceType":2,
      "DontAutoSwitchWhenInstalled":true
    }
  ]  
}
```
	DeviceType ist wichtig! (0=Classic, 1=Mini, 2=XL, 3=Mobile, 7=PLUS)
4. Alle Profile, die exportiert wurden, aus `streamdeck\preferences\profiles` löschen 
5. Es wird ein Profil benötigt welches nicht im Manifest enthalten ist. Das Profil enthält mindestens einem Button aus dem Plugin. Dieses Profil muss das aktive Profil sein.
6. Nach einem Neustart bittet die App Profile des Plugins zu installieren.
7. Wenn die Profile erschienen sind, StreamDeck neustarten
0004000200050006000300040005000600060004
## Nützliche Links

[Automatic Profile Switching](https://github.com/mhwlng/streamdeck-elite/wiki/Automatic-Profile-Switching)
[setImage of multi-action funktioniert nicht](https://github.com/orgs/elgatosf/discussions/54)
[switchToProfile API can now be used with an editable preconfigured profile](https://docs.elgato.com/sdk/plugins/changelog#changes-in-stream-deck-4.6)














Wie triggere ich den Funktionsaufruf für switchToProfile,


```JSON
"0000" : true,
"0001" : false,
"0002" : true,
"profil" : H3D-Start
```

onAppeared: speichere DeviceID in globale Variable, speichere aktuelles Profil in globaler Variable
while(blabla)
	wenn bla.get("profil") != globaleVariableProfil
		globaleVariableProfil = bla.get("profil")
		switchToProfile(DeviceID, globaleVariableProfil)