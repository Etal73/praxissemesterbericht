## Generelle Idee
- Jeder Drag erzeugt eine Dragbox
- Jede erzeugte DragBox, erzeugt in ihrem Zentrum eine *TextNode* und der Text ist String-Nr oder Char
- Jede DragBox wird gespeichert in einem Stack und bei dem Betätigen des Undo-Buttons wird die oberste Box entfernt

- Danach werden die Koordinaten übernommen durch [[Rechteck]] übernommen und anschließend startet die Methode [[DrawRectangle]] 

[[Auswahlfeedback]] ist somit auch implementiert


## Technische Umsetzungsideen:
- [[paneDragBoxPressed]] erzeugt eine neue DragBox und die größe der DragBox wird per [[paneDragBoxDragged]] bestimmt.
- Anschließend wird die erzeugte DragBox in einer [[global]]en ArrayList abgelegt. 
- [[paneDragBoxReleased]] ruft die Methode [[safeKoord]] auf, welche dann die Werte der DragBox(X,Y,Hoehe,Breite) übernimmt. =>[[getCoords]] wird damit überflüssig
- Beim Klicken von [[Einzeichnen]] werden die sichtbaren Rectangles entfernt 
## Textfelderzeugung 
- Es bedarf einer neuen Klasse, diese Klasse erbt von JavaFX.Rectangle und ist quasi ein Rectangle mit einem Textelement im Zentrum