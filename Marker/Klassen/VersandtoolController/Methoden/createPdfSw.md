```Java
private void createPdfSw(String s) throws IOException {  
    //Neue Pdf im Querformat  
    Document document = new Document(PageSize.A4.rotate());  
    PdfWriter.getInstance(document, new FileOutputStream(s));  
    document.open();  
    int index = 0;  
    for (com.lowagie.text.Image img : swImages){  
        //Größe des Bildes Anpassen  
        img.scaleAbsoluteWidth(document.getPageSize().getWidth());  
        img.scaleAbsoluteHeight(document.getPageSize().getHeight());  
        //Position des Bildes muss explizit angegeben werden, sonst ist das Bild nicht vollständig drauf  
        img.setAbsolutePosition(0, 0);  
        if(index % 2 == 0){  
            document.add(img);  
        }  
        if(index % 2 == 1){  
            document.newPage();  
            document.add(img);  
        }  
        index++;  
    }  
    document.close();  
}
```