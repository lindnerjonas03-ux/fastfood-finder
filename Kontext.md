<Ziel>
Ein Ordner mit verschiedenen Dateien und Codes, welche für die Erstellung einer Web-Seite (Kernversion) notwendig sind. In der Kernversion Web-Seite werden Kalorien mit Spielraum eingegeben. Danach werden passende Produkte aus meiner Liste ausgeben. Sortierbar nach Protein und Kohlenhydrate. Außerdem kann man nach Fast-Food-Ketten filtern. Dafür soll aus einer Liste ausgewählt werden können welche Ketten erwünscht sind. Die App wird im Browser auf dem Smartphone verwendet.
</Ziel>
<Dateiübersicht>
"Kontext.md": Kontext Datei für den Ordner
"fastfood_testdaten.csv": Excel Tabelle mit 17 Beispielprodukten
"fastfood_finder.html": Leere Datei in der zukünftig der Code hinzugefügt werden soll
</Dateiübersicht>
<Regeln>
- Es wird die Kalorienanzahl, der Spielraum + und der Spielraum - eingegeben
-Ausgabe bei leere Eingabe oder ungültige Eingabe (keine Zahl): "Bitte eine gültige Kalorienzahl eingeben!", kein Ergebnis
-Ausgabe, wenn die Kalorienzahl geringer als die Kalorienzahl des kalorienärmsten Produkts: "Deine Kalorienzahl ist zu gering!" , kein Ergebnis
-Ausgabe falls die Kalorienzahl größer als das Kalorienärmste Produkt ist, der Spielraum aber zu klein für ein passendes Produkt: "Keine passenden Produkte gefunden, versuche einen größeren Spielraum!"
-Ausgabe, wenn der Filter alle Ergebnisse wegfiltert: "Keine Produkte für diesen Filter gefunden!"
</Regeln>
<Testfälle>
Eingabe: <490; 70; 0>
Sollwert <Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F; Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
Eingabe: <abc; 100; 0>
Sollwert <Bitte eine gültige Kalorienzahl eingeben!>
Eingabe: <50;0;0>
Sollwert <Deine Kalorienzahl ist zu gering!>
Eingabe: <270;0;0>
Sollwert <Keine passenden Produkte gefunden, versuche einen größeren Spielraum!>
</Testfälle>