```Java
protected void paneDragBoxDragged(MouseEvent event) {  
    if (event.isPrimaryButtonDown()){  
        dragBox.setX(Math.min(event.getX(), mouseDownX));  
        dragBox.setWidth(Math.abs(event.getX() - mouseDownX));  
        dragBox.setY(Math.min(event.getY(), mouseDownY));  
        dragBox.setHeight(Math.abs(event.getY() - mouseDownY));  
    }  
}
```
