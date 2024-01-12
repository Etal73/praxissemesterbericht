```Java
public void initialize(URL url, ResourceBundle resourceBundle) {  
    //Dropdown-Menü für die Auswahl der Schriftgröße initialisieren  
    ObservableList<Integer> observableList = FXCollections.observableArrayList(45,55,65,75,85);  
    schriftGroesse.setItems(observableList);  
    schriftGroesse.getSelectionModel().selectFirst();  
}
```