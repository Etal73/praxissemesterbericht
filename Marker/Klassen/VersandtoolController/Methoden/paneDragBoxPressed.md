```Java
protected void paneDragBoxPressed(MouseEvent event){  
    mouseDownX = event.getX();  
    mouseDownY = event.getY();  
    dragBox.setVisible(true);  
    dragBox.setStroke(Color.RED);  
    dragBox.setFill(Color.TRANSPARENT);  
    dragBox.getStrokeDashArray().addAll(5.0,5.0);  
    /*dragBox.*/  
    if (!anchor.getChildren().contains(dragBox)){  
        anchor.getChildren().add(dragBox);  
    }  
    dragBox.setX(event.getX());  
    dragBox.setY(event.getY());  
    dragBox.setWidth(0);  
    dragBox.setHeight(0);  
  
}
```