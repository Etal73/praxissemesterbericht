```Java
private com.lowagie.text.Image getImage(Canvas canvas) throws IOException {  
  
    WritableImage snapshot = canvas.snapshot(null, null);  
    BufferedImage image = SwingFXUtils.fromFXImage(snapshot, null);  
  
    ByteArrayOutputStream baos = new ByteArrayOutputStream();  
    ImageIO.write(image, "png", baos);  
  
    return com.lowagie.text.Image.getInstance(baos.toByteArray());  
}
```
