## Zurück zur [[Plugin/PluginDokumentation/Übersicht]]

[Referenz](https://docs.elgato.com/sdk/plugins/events-sent)
Das Plugin sendet "Events", oder in dem Fall von Java: Methoden, an das StreamDeck wodurch dann der gewünschte Effekt auftritt.
Das Plugin und der [[Property Inspector]] können beide Events an das Stream Deck schicken, hier sind die mMn Wichtigsten:  
- [[setSettings()]]
- [[getSettings()]]
Des Weiteren kann das Plugin weitere Events schicken, die Wichtigsten sind:
- [[setTitle()]]
- [[setImage()]]
- [[showAlert()]]
- [[showOk()]]
- [[switchToProfile]]
- [[sendToPropertyInspector]]
Der [[Property Inspector]] kann außerdem noch das folgende Event schicken:
- [[sendToPlugin]]
