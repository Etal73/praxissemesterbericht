```Java
protected void getCoords(MouseEvent event){  
    if(event.isPrimaryButtonDown()){  
        koords.add(new Koordinaten(event.getX(), event.getY()));  
    }  
}
```
