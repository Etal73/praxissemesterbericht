```Java
private void createPdf() throws IOException{  
    Document document1 = new Document();  
    document1.setPageSize(PageSize.A4);  
  
    FileChooser fileChooser1 = new FileChooser();  
    FileChooser.ExtensionFilter extensionFilter = new FileChooser.ExtensionFilter("PDF Dateien (*.pdf)", "*.pdf");  
    fileChooser1.getExtensionFilters().add(extensionFilter);  
    File output = fileChooser1.showSaveDialog(anchor.getScene().getWindow());  
    PdfWriter.getInstance(document1, new FileOutputStream(output));  
  
    document1.open();  
    int index = 0;  
    for (com.lowagie.text.Image img : toPdfList){  
  
        img.scaleAbsoluteWidth(596);  
        img.scaleAbsoluteHeight(421);  
        img.setAbsolutePosition(0, 0);  
        if(index % 2 == 0){  
            img.setAbsolutePosition(0, 421);  
            document1.add(img);  
        }  
        if(index % 2 == 1){  
            img.setAbsolutePosition(0,0);  
            document1.add(img);  
            document1.newPage();  
        }  
        index++;  
    }  
    document1.close();  
    String pathToPdf = output.getPath();  
    String[] pathToPdfSw = pathToPdf.split(".pdf");  
    createPdfSw(pathToPdfSw[0]+"SW.pdf");  
    showLabel();  
}
```
