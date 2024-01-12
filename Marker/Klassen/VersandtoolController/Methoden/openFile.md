```Java
protected void openFile(){  
    Stage stage = (Stage) canvas.getScene().getWindow();  
    File file = fileChooser.showOpenDialog(stage);  
    if(file != null){  
        Image image = new Image(file.toURI().toString());  
  
        anchor.getScene().getWindow().setWidth(image.getWidth()+20);  
        anchor.getScene().getWindow().setHeight(image.getHeight());  
        canvas.setHeight(image.getHeight());  
        canvas.setWidth(image.getWidth());  
  
        GraphicsContext gc = canvas.getGraphicsContext2D();  
        gc.drawImage(image, 0, 0);  
    }  
}
```
