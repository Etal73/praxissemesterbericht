```Java
protected void drawRectangle() throws Exception {  
    GraphicsContext gc = canvas.getGraphicsContext2D();  
    //Erste Schleife, Nummern werden platziert  
    for (Rechteck rechteck : rechtecke){  
        //System.out.println("For-Schleife 1: "+rechteck.toString());  
        double hoehe = rechteck.getHoehe();  
        double breite = rechteck.getBreite();  
        double startX = rechteck.getStartX();  
        double startY = rechteck.getStartY();  
  
        //Mittelpunkt des Rechtecks, zur Platzierung der Nummer  
        double mitteX = startX + (breite/2);// - ((double) fontSize /1.7);  
        double mitteY = startY + (hoehe/2) + ((double) fontSize /2.5);  
  
        gc.setGlobalAlpha(0.4);  
        gc.setFill(Color.WHITE);  
        gc.fillRect(startX, startY, breite, hoehe);  
  
        //Formatierung für die Nummerierung  
        gc.setGlobalAlpha(1);  
        gc.setFont(Font.font("Arial", fontSize));  
        gc.setFill(Color.BLACK);  
        gc.setStroke(Color.BLACK);  
        gc.fillText(String.valueOf(nummerierung), mitteX, mitteY);  
        nummerierung++;  
  
    }  
    saveCanvasNummeriert(canvas);  
    //Zweite Schleife, Farbige Kästchen werden gemalt  
    for (Rechteck rechteck : rechtecke){  
        //System.out.println("For-Schleife 2: "+rechteck.toString());  
        double hoehe = rechteck.getHoehe();  
        double breite = rechteck.getBreite();  
        double startX = rechteck.getStartX();  
        double startY = rechteck.getStartY();  
  
        Canvas canvasCopy = new Canvas(canvas.getWidth(), canvas.getHeight());  
        GraphicsContext gc2 = canvasCopy.getGraphicsContext2D();  
  
        gc2.drawImage(canvas.snapshot(null, null), 0, 0);  
        gc2.setGlobalAlpha(0.4);  
        gc2.setFill(colorFill);  
        gc2.setStroke(Color.BLACK);  
        gc2.fillRect(startX, startY, breite, hoehe);  
  
        saveCanvas(canvasCopy);  
    }  
    rechtecke.clear();  
}
```