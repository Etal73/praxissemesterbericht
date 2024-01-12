[Quelle](https://docs.google.com/presentation/d/1IQCRPHEIX-qKo7QFxsD3V62yhyGA9_5YsYXFOiBpgkk/view#slide=id.g4d6b1121f4_2_60)
# Repository Struktur

![[Pasted image 20231215101753.png]]

- .git Ordner ist die GitDatenbank
- Ein Git Repository hat höchstens einen working tree
- Ein Git Repository ohne working nennt man ``bare repository``
- `git checkout` erstellt ein working tree auf Basis des gewünschten `commit`
- Änderungen werden Git mit `git add <file>`  und `git rm <file>` mitgeteilt
- Dateien die mit `git add` hinzugefügt werden im Index vorgemerkt, will man die Änderungen rückgängig machen, so muss man `git reset HEAD <file>` ausführen
- `git commit` überführt die Änderungen ausm Index in den `objects`-Ordner
![[Pasted image 20231215102813.png]]

# Änderungen anschauen
![[Pasted image 20231215102904.png]]
