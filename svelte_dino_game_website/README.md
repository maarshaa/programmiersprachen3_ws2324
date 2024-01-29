Doku:

________________________________________________________________________________________________________________

App generell:

Inhalt:

Erstellt wurde eine App mit *drei Unterseiten*; Home, Übersicht und Spiel

*Dark und Light Mode* vorhanden (ansteuerbar durch Sonne/Mond Icon im Header)

Nahtloses, *responsives Design* 



Vorgehen:

Erstellung der einzelnen Unterseiten, im Anschluss wurden diese durch den *Router (svelte-spa-router)* verknüpft

Dark-Mode: Trigger ändert Hintergrund- und Schriftfarben, Boxen/Buttons/etc ändern ihre Farbe durch Transperenz
-> Problem: bei der Rückkehr auf "Home" wird Seite neu geladen, was dazu führt das sich der Mode nicht gemerkt wird,
wurde behoben durch das ausgliedern von Home ähnlich wie bei den anderen Unterseiten (für Home wird nicht index.html
aufgerufen, sondern #/home) dadurch wird aber beim ersten aufrufen der Seite kein Inhalt gezeigt, deswegen wurde
dies wieder verworfen und das Problem bleibt ungelöst.
-> bei der Aktion das Ganze zurückzusetzen ist leider auch die Hinterlegung des Homebuttons abhanden gekommen :/

Responsivness durch max-width 

Um dem User ein besseres Verständnis für die Werte zu geben ist in dem Footer eine Legende, welche die verschiedenen 
Icons erklärt

________________________________________________________________________________________________________________

Home:

Inhalt:

*Buttons* auf dem Homescreen navigieren zusätzlich zu der navigation bar zu "Spiel" und "Übersicht"

*Bild-Api* von Pexels *(https://www.pexels.com/api/documentation/)*, durch klicken auf den Button wird ein Bild 
von Pexel unter dem Suchbegriff "Dino" geladen

________________________________________________________________________________________________________________

Übersicht:

Inhalt:

Informationskarten basierend auf den Daten aus *dinosaur_data.js* mit Bildern aus Ordner Public -> Images

*Interaktionsmöglichkeit* durch:
*Sortierfunktion* (durch klicken auf Icons) 
klicken auf die Karten selbst (Anzeigen des *Random Facts* in einem seperaten Feld oben rechts)


Vorgehen: 

Die Informationskarten wurden erstellt, indem die Quartettkarten recycelt und leicht angepasst wurden

________________________________________________________________________________________________________________

Spiel:

Dinoquiz; durch das Anzeigen verschiedener Infomationen soll der Spieler den gesuchten Dino erraten


Inhalt:

*Interaktionsmöglichkeit* durch:
Auswählen einer *Schwierigkeitsstufe* (über die 6 Kreise)
Die Möglichkeit sich die Lösung oder den nächsten Dino anzeigen zu lassen
Das erraten des Dino selbst, durch klicken auf das jeweilige Bild

*Feedback* durch:
grüner oder roter Rahmen um das Bild selbst, sowie Färbung des Infokasten in der jeweiligen Farbe,
durch klicken auf "Lösung" werden die fehlenden Informationen ausgefüllt und das entsprechende Dinobild grün 
umrahmt

*Punkteberechnung* 


Vorgehen:

Die Schwierigkeitsstufen geben an, wie viele Informationen über den Dino dem Spieler angezeigt werden. Durch 
klicken auf eine andere Schwierigkeitsstufe wird auch der Dino gewechselt, um Schummeln zu verhindern.

Die Farbe des Rahmens um das Bild wird dadurch bestimmt, dass der currentDino mit dem geklickten verglichen wird. 
Der grüne Rahmen bleibt bestehen, bis die nächste Runde beginnt, damit der Spieler genug Zeit hat die Informationen 
und das Bild nochmal anzuschauen. Der rote Rahmen verschwindet, sobald die Maus das Bild verlässt (durch ein 
on:mouseleave)

Die Punkte werden dadurch berechnet, dass es 5 Basispunkte gibt. Bei jedem falschen Klick wird davon ein Punkt 
abgezogen. Sobald der richtige Dino ausgewählt wurde werden die verbleibenden Punkte mit dem Schwierigkeitsgrad 
multipliziert.
Sprich; 2x falsch geklickt bei Schwierigkeitsstufe 3 -> (5-2) x 3 = 9 Punkte

Punkte werden gezählt bis die Seite neu geladen oder das Spiel verlassen wird.







