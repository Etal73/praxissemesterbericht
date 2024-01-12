
```Java
protected void reset(){  
    toPdfList.clear();  
    swImages.clear();  
    rechtecke.clear();  
    koords.clear();  
    nummerierung = 1;  
    GraphicsContext gc = canvas.getGraphicsContext2D();  
    gc.clearRect(0,0,canvas.getWidth(), canvas.getHeight());  
}
```
