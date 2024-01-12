```Java
protected void safeKoords(){  
    if(!koords.isEmpty()) {  
        rechtecke.add(new Rechteck(koords.get(0).getX(), koords.get(0).getY(), koords.get(koords.size() - 1).getX(), koords.get(koords.size() - 1).getY()));  
        //System.out.println("Added: "+rechtecke.get(rechtecke.size()-1).toString());  
    }  
    koords.clear();  
}
```
