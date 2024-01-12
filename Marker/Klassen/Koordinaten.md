```Java
public class Koordinaten {  
    public double getY() {  
        return y;  
    }  
  
    public double getX() {  
        return x;  
    }  
  
    private final double x;  
    private final double y;  
  
    Koordinaten(double inX, double inY){  
        this.x = inX;  
        this.y = inY;  
    }  
  
    public String toString(){  
        return "X: " + this.x + "| Y: " + this.y;  
    }  
}
```