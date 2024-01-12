```Java
ArrayList<Koordinaten> koords = new ArrayList<>();  
ArrayList<Rechteck> rechtecke = new ArrayList<>();  
ArrayList<com.lowagie.text.Image> toPdfList = new ArrayList<>(); 

private final FileChooser fileChooser = new FileChooser();  

private final Rectangle dragBox = new Rectangle();  
  
private Color colorFill = Color.RED;  

private final ArrayList<com.lowagie.text.Image> swImages = new ArrayList<>();  

double mouseDownX;  
double mouseDownY;  

int fontSize = 45;  
int nummerierung = 1;
```