<Ziel>
Ein Ordner mit verschiedenen Dateien und Codes, welche für die Erstellung einer Web-Seite (Kernversion) notwendig sind. In der Kernversion Web-Seite werden Kalorien mit Spielraum eingegeben. Danach werden passende Produkte aus meiner Liste ausgeben. Der Benutzer soll auswählen können, ob nach Protein oder Kohlenhydrate, aufsteigend oder absteigend sortiert werden soll. Dabei soll ein Auswahlfeld verwendet werden. Außerdem soll man nach Fast-Food-Ketten filtern können. Dafür soll aus einer Auswahlliste durch klicken auf ein Kontrollkästchen ausgewählt werden können welche Ketten erwünscht sind. Die App wird im Browser auf dem Smartphone verwendet.
</Ziel>
<Dateiübersicht>
"Kontext.md": Kontext Datei für den Ordner
"fastfood_testdaten.csv": Excel Tabelle mit 17 Beispielprodukten
"fastfood_finder.html": Datei mit Array der Produkte, Funktion passendeProdukte() und Oberfläche
</Dateiübersicht>
<Regeln>
- Es wird die Kalorienanzahl, der Spielraum + und der Spielraum - eingegeben
-Ausgabe bei leere Eingabe oder ungültige Eingabe (keine Zahl), (egal ob bei Kalorienzahl oder Spielraum): "Bitte eine gültige Kalorienzahl eingeben!", kein Ergebnis
-Ausgabe, wenn die Kalorienzahl geringer als die Kalorienzahl des kalorienärmsten Produkts: "Deine Kalorienzahl ist zu gering!" , kein Ergebnis
-Ausgabe falls die Kalorienzahl größer als das Kalorienärmste Produkt ist, der Spielraum aber zu klein für ein passendes Produkt: "Keine passenden Produkte gefunden, versuche einen größeren Spielraum!"
-Ausgabe, wenn der Filter alle Ergebnisse wegfiltert: "Keine Produkte für diesen Filter gefunden!"
- Ausgabe: Wenn Kalorienzahl + Spielraum exakt gleich dem Kalorienwert des Produktes ist: Produkt wird ausgegeben.
- Ausgabe: Wenn Kalorienzahl - Spielraum exakt gleich dem Kalorienwert des Produktes ist: Produkt wird ausgegeben.
- Ausgabe: Wenn Kalorienzahl exakt gleich dem kalorienärmsten Produktes ist: Produkt wird ausgegeben.
-Keine Auswahl der Sortierung: Standard-Reihenfolge nach Proteine absteigend sortiert
-Wenn keine Auswahl im Filter ausgewählt wurde: Alle Ergebnis aus allen Ketten soll angezeigt werden
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
Eingabe: <170; 0; 0>
Sollwert <Cola (0,4 l), McDonald's ,170kcal, 0g P, 42g K, 0g F>
Eingabe: <400; 0; 10>
Sollwert <Original Recipe Chicken Breast, KFC, 390kcal, 33g P, 12g K, 24g F; McChicken, McDonald's ,400kcal, 17g P, 40g K, 20g F>
(Ab hier mit Sortierung und Filter)
Eingabe: <490; 70; 0> Sortierung: <nach Protein, absteigend> Filter: <kein Filter>
Sollwert <Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F; Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
Eingabe: <490; 70; 0> Sortierung: <nach Protein, absteigend> Filter: <Burger King>
Sollwert <Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
</Testfälle>
<Abbruchkriterium>
Stoppe jeden weiteren Versuch wenn: Derselbe Testfall schlägt beim dritten Versuch in Folge fehl
Übergabe: Anzeigen von <git diff> 
Fragen bevor Start des nächsten Versuchs
Beispiel:
Eingabe: <abc; 100; 0>
Versuch 1 ergab <Error>
Eingabe: <abc; 100; 0>
Versuch 2 ergab <Hallo>
Eingabe: <abc; 100; 0>
Versuch 3 ergab <0>
<git diff> wird angezeigt
Frage bevor Start des nächsten Versuchs.
</Abbruchkriterium>
<Meine Prüfpflicht>
Prüfung bei Rückgabe des Agenten an mich (nicht jede Zwischenbearbeitung prüfen). Bereits bestehende Testfälle aus <Kontext.md> erneut prüfen, unabhängig davon, ob der Agent Erfolg meldet.
Beispiel:
Hinzufügen der Sortierung und Filter
Testfälle prüfen bei Rückgabe der Funktion vom Agenten:
Eingabe: <490; 70; 0>
Sollwert <Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F; Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
Eingabe: <abc; 100; 0>
Sollwert <Bitte eine gültige Kalorienzahl eingeben!>
Eingabe: <50;0;0>
Sollwert <Deine Kalorienzahl ist zu gering!>
Eingabe: <270;0;0>
Sollwert <Keine passenden Produkte gefunden, versuche einen größeren Spielraum!>
Eingabe: <170; 0; 0>
Sollwert <Cola (0,4 l), McDonald's ,170kcal, 0g P, 42g K, 0g F>
Eingabe: <400; 0; 10>
Sollwert <Original Recipe Chicken Breast, KFC, 390kcal, 33g P, 12g K, 24g F; McChicken, McDonald's ,400kcal, 17g P, 40g K, 20g F>
(Ab hier mit Sortierung und Filter)
Eingabe: <490; 70; 0> Sortierung: <nach Protein, absteigend> Filter: <kein Filter>
Sollwert <Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F; Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
Eingabe: <490; 70; 0> Sortierung: <nach Protein, absteigend> Filter: <Burger King>
Sollwert <Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
</Meine Prüfpflicht>