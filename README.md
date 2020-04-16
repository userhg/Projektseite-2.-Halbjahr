# Projektseite-2.-Halbjahr

von Gesche Meyer
und Hannah Fußner

## Inhaltsverzeichnis

[Einleitung](#1)

[Auswahl der Eigenschaften](#2)

[Die Fractal Scripts](#3)

[Reflexion](#4)


### <a name="1"></a>Einleitung
Für dieses Projekt wollten wir etwas Neues ausprobieren. Wir haben uns schon seit Anfang der Benutzung von Snap! gefragt, was es mit den Blocks rund um "Pen" aufsich hat. In dem Curriculum con "The Beauty and Joyy of Computing haben wir nach Möglichkeiten gesucht, diese Funktionen von Snap! zu benutzten. (https://bjc.edc.org/bjc-r/course/bjc4nyc.html)
Schnell sind wir fündig geworden. Uns hat das Thema "Recursion" interessiert und begonnen Fractals zu kreieren. Begonnen mit der Form eines Dreiecks haben wir das gleiche Prinzip auf einige andere geometrische Figuren anwenden wollen, sodass verschiedene Mandalas entstehen. Daraus haben wir nun eine Art Spiel gemacht, bei dem der Spieler verschiedene Auswahlmöglichkeiten hat, um verschiedene Formen/ Mandalas zeichnen zu lassen.

### <a name="2"></a>Auswahl der Eigenschaften
Der Spieler hat drei Mal die Möglichkeit, das Fractal nach seinen Wünschen zu bestimmen, welches dann im Anschluss gezeichnet wird.
Die Auswahl wird durch den Sprite *Welcome* koordiniert. 

Zuerst wird ausgewählt, wie viele Level das Fractal haben soll, also wie oft, die Form an jede Ecke jeweils gezeichnet werden soll.
Dafür haben wir die Variable *Levelchoice* eingeführt. Es kann zwischen 1, 2 oder 3 Levels ausgewählt werden. Es wird immer die Grundform gezeichnet und dann so viele weitere Level, wie ausgewählt, später hinzugefügt.

![image1](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Anfang%201.png)

Außerdem werden alle weiteren Variablen eingefügt, jedoch nur die der Levelauswahl in aktiver Form. Die anderen sind durch die FLAG-Methode vorerst inaktiv, damit sie nicht im vorhinein ausgewählt werden können.

Sobald 1, 2, oder 3 ausgewählt werden wir die Variable auf diese Zahl gesetzt und danach unveränderbar gemacht.

![image2](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Levelauswahl.png)

Nach der Auswahl der Levelanzahl wird der Broadcast *Colour?* verschickt, welcher nun der Start für die Farbauswahl ist. 

Nun wird die Variable *Colourchoice* aktiviert. Es kann zwischen einer schwarzen Figur und einer bunten Figur ausgewählt werden.

![image3](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Anfang%202%20r.png)

Entsprechend der Wahl des Spielers wird die Variable auf C für Bunt oder B für Schwarz gesetzt und durch die Flag Methode die Variable unveränderbar gemacht.

![image4](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Farbauswahl.png)

Nach der Auswahl der Farbe wird der Broadcast *Fractal?* gesendet.
Dies ist der Start für die Auswahl der geometrischen Form. zuvor wird die Variable *Fractalchoice* aktiviert.
Es kann zwischen einem Dreieck, Quadrat oder Pentagon gewählt werden. Nach der Auswahl verschwindet der Sprite und wir mussten am Ende des Scripts noch einen Hack einbauen, damit am Anfang der Sprite nicht die letzte Sprechblase zuerst anzeigt. Nur durch das Einfügen des Blocks *say: Hello* wurde dieser Fehler behoben. 

![image5](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Anfang%203.png)
 
Wird die Form ausgewählt, T für Dreieck, S für Quadrat und P  für Pentagon, so wird die Variable *Fractalchoice* auf die entsprechende Form gesetzt und blockiert. Außerdem wird ein Broadcast mit der Bezeichnung der ausgewählten Form verschickt, was zu Ausführung der entsprechenden Zeichnung führt. 

![image6](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Formauswahl.png)

### <a name="3"></a>Die Fractal Scripts
Für jedes Fractal (Triangle, Square oder Pentagon) haben wir zuerst ein Scrpit für die einfache Form gebaut. "Triangle size_" "Square size_" und "Pentagon size_"
Diese beruhen auf dem Prinzip, dass der Sprite sich eine bestimmte Länge (size) bewegt und sich dann um eine bestimmte Gradzahl dreht. Bei einem Dreieck muss dieser Vorgang dreimal wiederholt werden, da ein Dreieck drei Seiten besitzt. Die Befehle "move size steps" und "turn _ degrees" werden also in eine Schleife von drei Wiederholungen gesetzt. 
Die Gradzahl lässt sich mit der Winkelsumme eines Dreiecks und den Winkelgesetzen bestimmen. In einem Dreieck betragen alle Winkel zusammen 180 Grad. Da wir ein gleichwinkliges Dreieck zeichnen, können wir daraus schließen, dass der Sprite sich 120 Grad drehen muss, um zwischen den Seiten einen Winkel von 60 Grad zu bekommen. Im Inneren des Dreiecks befindet sich also der Scheitelwinkel mit 60 Grad. Mit dem Nebewinkel von 120 Grad addiert ergeben sich so 180 Grad. 
In das Script für die einfache Form ist auch der Block "pen down" integriert, damit die Strecke des Sprites aufgezeichnet wird.

![image7](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Triangle%20block%201.png)

Für die anderen Formen, dem Quadrat und dem Pentagon, geht man nach dem selben Prinzip vor. Vier Wiederholungen und 270 Grad (im Viereck Winkelsumme 360 Grad) für das Viereck, fünf Wiederholungen und 432 Grad (Winkelsumme im Pentagon 540 Grad) für das Pentagon. 

![image9](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/square%20size%201.png)      
![image10](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/pentagon%20block%201.png)

Diese Blocks für die Grundformen haben wir in den Block für die Mandalas gesetzt. Zu der variirbaren *size* kommt die Variabel *Level* dazu. 
Wird das Level 0 gewählt, ensteht nur die Grundform. Der von uns erstellte Block "Triangle size" wird ausgeführt. Hat der Spieler die Level 1, 2, oder 3 gewählt, so kommt der neue von uns erstellte Block "Triangle fractal level _ size_" an die Reihe. In diesem Block ist eingebaut, dass das Level jeweils um 1 subtrahiert wird und die Größe der Formen um 0.5 verkleinert, sodass sich der Block solange selbst aufruft, bis das Level 0 durch Substraktion erreicht wird. Mit dem vorherigen Befehl "move size steps" und dem folgendem Befehl "turn _ degrees" enstehen so an den Ecken der Formen jeweils die neuen Formen und das gewünschte Fractal entsteht. Die Befehle kennen wir aus dem Script für die Grundformen. Wie dort, muss das Ganze sooft wiederholt werden, wie die Form Seiten hat.

Beispiel Dreieck-Fractal:

![image11](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/T%20fractal%20%20.png)

Für die farbliche Variante, haben wir für jede Figur denselben Block "Triangle fractal level _ size_" mit dem Befehl "change pen hue by -5 " erweitert, sodass ein Farbverlauf entsteht.

![image12](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/T%20fractal%20colour.png)

Mit diesem Prinzip haben wir ebenfalls die Viereckversion und die Fünfeckversion erstellt.

Je nachdam, welches Level, welche Form und welche Farboption gewählt wurde (siehe Auswahl der Eigenschaften), wird der jeweilige Block ausgeführt und man erhält sein gewünschtes Fractal.
Bei Schwarz wird die Farbe vorher, außerhalb des "Triangle fractal level _ size_" - Blocks,  durch "set pen colour to _ " zu schwarz geändert. 

![image13](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Auswertung.png)

Am Anfang des Spiels, wenn die grüne Flagge geklickt ist, wird der Bildschirm "entleert", gezeichnete Fractals gelöscht ("clear"), die Farbe wird auf die Ursprungsfarbe zurück geändert ("set pen colour to") und der Sprite wird in die Ausgangssituation zurück gebracht (go to x: 0 y:-70). Der Sprite ist während des ganzen Vorgangs nicht zu sehen (hide). 

![image14](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/drawer%20start.png)

Mögliche Ergebnisse könnten so aussehen:

![image15](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Erg.1.png)
![image16](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Erg.2.png)
![image17](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Erg.3.png)
![image18](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Erg.4.png)
![image19](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Erg.5.png)
![image20](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Erg.6.png)


### <a name="4"></a>Reflexion
Anfangs hatten wir Schwierigkeiten ein Thema zu finden, welches uns reizte, zu erarbeiten, oder wir hatten Probleme bei der Umsetzung. Dadurch haben wir ein wenig Zeit verloren und relativ spät mit unserer wirklichen Idee begonnen. Wir hätten noch mehr Level ins "Spiel" bauen können oder uns mit einer allgemeineren Formel beschäftigenkönnen, was uns vor allem aus zeitlichen Gründen leider nicht gelungen ist. 
Insgesamt können wir aber sagen, dass wir zufrieden mit unserem Ergebnis sind. Wir haben es geschafft, eigene Blocks zu erstellen und mit Rekursion zu arbeiten. Auch sind wir mit unserer Lösung glücklich, das Ganze als ein Spiel aufzuziehen und zu verbinden.
