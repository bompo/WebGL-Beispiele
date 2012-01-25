Die folgenden Beispiele sollen der Festigung des im Beleg behandelten Stoffes dienen. 

#### Aufgabe 1 ####
Erstellen Sie eine HTML Seite, welche ein Canvas Element mit der Größe $800x480$ Pixel beinhaltet. Erstellen Sie über dieses Canvas Element den WebGL Kontext. Setzen Sie die clearColor auf blau und löschen Sie anschließend den Farbbuffer. 

#### Aufgabe 2 ####
Erstellen Sie einen einfachen Vertex und Fragment Shader. Fügen Sie beide zu einem Shaderprogramm zusammen. Fügen Sie anschließend einen Fehler in das Shaderprogramm ein und lassen Sie sich den Fehler über die Funktion alert() anzeigen. 

#### Aufgabe 3 ####
Zeichnen Sie ein blaues Dreieck. Die Koordinaten des Dreieckes sollen in Clipped Space Cordinates angegeben werden. Die Farbe soll im Fragment Shader durch eine Konstante festgelegt werden. 

#### Aufgabe 4 ####
Färben Sie das Dreieck aus Aufgabe 3 mit einem Farbverlauf ein. Übergeben Sie dazu die Farbwerte als VBO an den Vertex Shader. Dieser soll das Attribut an den Fragment Shader weiter reichen und somit den Farbverlauf über die automatische Interpolation realisieren. 

#### Aufgabe 5 ####
Animieren Sie das Dreieck aus Aufgabe 4, indem Sie dieses um die Z-Achse herum drehen. Nutzen Sie für die Transformation der 3D Daten in den 2D Raum eine Projection-Matrix und animieren Sie das Modell über eine Model-Matrix.

#### Aufgabe 6 ####
Zeichnen sie eine dreidimensionale Pyramide. Jede Seite der Pyramide soll dabei mit einer einheitlichen Farbe ohne Farbverläufe eingefärbt sein.

#### Aufgabe 7 ####
Geben Sie der Pyramide aus Aufgabe 6 eine Textur. Achten Sie darauf, dass die Textur dabei nicht verzerrt dargestellt wird. Sie können dafür die Texur im Ordner data verwenden.

#### Aufgabe 8 ####
Legen Sie für die Pyramide aus Aufgabe 7 die Normalen fest. Beleuchten Sie das Pyramidenmodell von schräg oben mit einem leicht blauen Richtungslicht.

#### Aufgabe 9 ####
Wandeln Sie nun das Richtungslicht aus Aufgabe 8 in ein Punktlicht um. Um den Effekt besser zu erkennen, richten Sie die Szene so ein, als würde die Kamera von oben herab auf vier drehende Pyramiden schauen. Das Punktlicht soll dabei in der Mitte der vier Pyramiden platziert werden.

#### Aufgabe 10 ####
Überführen Sie die VBOs der Pyramide in ein JSON Format. Laden Sie dieses anschließend. Die Szene soll dabei wie in Aufgabe 9 aufgebaut sein.

#### Aufgabe 11 ####
Laden sie das Teapot Model über die JSON Datei aus dem Ordner \textit{data}. Realisieren Sie anschließend das Beleuchtungsmodell nach Blinn. Verändern Sie dabei die Shininess Variable und beobachten Sie deren Einfluss.

#### Aufgabe 12 ####
Erstellen Sie einen Vignetten Effekt mittels Post Processing. Rendern Sie die Szene aus Aufgabe 11 in einen Framebuffer. Nutzen Sie die Textur des Framebuffers als Eingabe. Sie können dabei folgenden Fragment Shader verwenden.

```html
uniform sampler2D uSampler;
varying vec2 vTextureCoord;
    
float size = 0.5;
float amount = 0.6;
void main() {
    vec4 color = texture2D(uSampler, vTextureCoord);
    
    //Abstand von der Texturkoordinate zum Mittelpunkt
    float dist = distance(vTextureCoord, vec2(0.5, 0.5));
    
    //Interpoliere den Abstandswert+Größe+Deckkraft in den Bereich [1.0-Größe]
    color.rgb *= smoothstep(1.0, size, dist * (amount + size));
    
    gl_FragColor = color;
}
```
