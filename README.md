# Projektseite-2.-Halbjahr

### Inhaltsverzeichnis

[Einleitung](#1)


### <a name="1"></a>Einleitung
Für dieses Projekt wollten wir etwas Neues ausprobieren. Wir haben uns schon seit Anfang der Benutzung von Snap! gefragt, was es mit den Blocks rund um "Pen" aufsich hat. In dem Curriculum con "The Beauty and Joyy of Computing haben wir nach Möglichkeiten gesucht, diese Funktionen von Snap! zu benutzten. (https://bjc.edc.org/bjc-r/course/bjc4nyc.html)
Schnell sind wir fündig geworden. Uns hat das Thema "Recursion" interessiert und begonnen Fractals zu kreieren. Begonnen mit der Form eines Dreiecks haben wir das gleiche Prinzip auf einige andere geometrische Figuren anwenden wollen, sodass verschiedene Mandalas entstehen. Daraus haben wir nun eine Art Spiel gemacht, bei dem der Spieler verschiedene Auswahlmöglichkeiten hat, um verschiedene Formen/ Mandalas zeichnen zu lassen.

### <a name="1"></a>Auswahl der Eigenschaften
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
Dies ist der Start für die Auswahl der geometrischen Form. 
Es kann zwischen einem Dreieck, Quadrat oder Pentagon gewählt werden. Nach der Auswahl verschwindet der Sprite und wir mussten am Ende des Scripts noch einen Hack einbauen, damit am Anfang der Sprite nicht die letzte Sprechblase zuerst anzeigt. Nur durch das Einfügen des Blocks *say: Hello* wurde dieser Fehler behoben. 

![image5](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Anfang%203.png)
 
Wird die Form ausgewählt, T für Dreieck, S für Quadrat und P  für Pentagon, so wird die Variable *Fractalchoice* auf die entsprechende Form gesetzt und blockiert. Außerdem wird ein Broadcast mit der Bezeichnung der ausgewählten Form verschickt, was zu Ausführung der entsprechenden Zeichnung führt. 

![image6](https://github.com/userhg/Projektseite-2.-Halbjahr/blob/master/Formauswahl.png)
