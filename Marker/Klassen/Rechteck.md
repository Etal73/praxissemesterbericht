```Java
public class Rechteck {  
    public double getStartX() {  
        return startX;  
    }  
  
    public double getStartY() {  
        return startY;  
    }  
    public double getHoehe() {  
        return hoehe;  
    }  
  
    public double getBreite() {  
        return breite;  
    }  
  
    Rechteck(double sX, double sY, double eX, double eY){  
        this.startY = sY;  
        this.startX = sX;  
        this.hoehe =  Math.abs(eY - startY);  
        this.breite = Math.abs(eX - startX);  
    }  
    public String toString(){  
        return "[Start X: " + this.startX + "] [Start Y: " + this.startY + "]" + "[Hoehe: " + this.hoehe +"] [Breite: " + this.breite + "]";  
    }  
    private final double startX;  
    private final double startY;  
    private final double hoehe;  
    private final double breite;  
  
}
```
