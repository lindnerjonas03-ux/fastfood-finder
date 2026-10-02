<Ziel>
Ein Ordner mit verschiedenen Dateien und Codes, welche für die Erstellung einer Web-Seite (Kernversion) notwendig sind. In der Kernversion Web-Seite werden Kalorien mit Spielraum eingegeben. Danach werden passende Produkte aus meiner Liste ausgeben. Der Benutzer soll auswählen können, ob nach Protein oder Kohlenhydrate oder Kalorien, aufsteigend oder absteigend sortiert werden soll. Dabei soll ein Auswahlfeld verwendet werden. Außerdem soll man nach Fast-Food-Ketten und zusätzlich nach Alle Produkte/Dessert/kein Dessert filtern können. Dafür soll aus einer Auswahlliste durch klicken auf ein Kontrollkästchen ausgewählt werden können welche Ketten erwünscht sind und ob Alle Produkte/Dessert/kein Dessert. Die App wird im Browser auf dem Smartphone verwendet.
</Ziel>
<Dateiübersicht>
"Backlog.md": Text mit zukünftigen Änderungen
"Kontext.md": Kontext Datei für den Ordner
"fastfood_testdaten.csv": Excel Tabelle mit 17 Beispielprodukten
"fastfood_finder.html": Datei mit Array der Produkte, Funktion passendeProdukte() und Oberfläche
</Dateiübersicht>
<Regeln>
- Es wird die Kalorienanzahl, der Spielraum + und der Spielraum - eingegeben
- Ausgabe bei leere Eingabe oder ungültige Eingabe (keine Zahl), (egal ob bei Kalorienzahl oder Spielraum): "Bitte eine gültige Kalorienzahl eingeben!", kein Ergebnis
- Ausgabe, wenn die Kalorienzahl geringer als die Kalorienzahl des kalorienärmsten Produkts: "Deine Kalorienzahl ist zu gering!" , kein Ergebnis
- Ausgabe falls die Kalorienzahl größer als das Kalorienärmste Produkt ist, der Spielraum aber zu klein für ein passendes Produkt: "Keine passenden Produkte gefunden, versuche einen größeren Spielraum!"
- Ausgabe, wenn der Filter alle Ergebnisse wegfiltert: "Keine Produkte für diesen Filter gefunden!"
- Ausgabe: Wenn Kalorienzahl + Spielraum exakt gleich dem Kalorienwert des Produktes ist: Produkt wird ausgegeben.
- Ausgabe: Wenn Kalorienzahl - Spielraum exakt gleich dem Kalorienwert des Produktes ist: Produkt wird ausgegeben.
- Ausgabe: Wenn Kalorienzahl exakt gleich dem kalorienärmsten Produktes ist: Produkt wird ausgegeben.
- Keine Auswahl der Sortierung: Standard-Reihenfolge nach Kalorien absteigend sortiert
-Wenn keine Auswahl im Filter ausgewählt wurde: Alle Ergebnis aus allen Ketten soll angezeigt werden
- Zusätzlicher Dropdown-Filter "Dessert" (unabhängig vom Ketten-Filter): Alle / Nur Dessert / Nur kein Dessert
- Dessert-Zuordnung ist ein festes Datenfeld pro Produkt (boolean), analog zu kcal; KI-Einschätzung mit manueller Korrekturmöglichkeit, 
Beispiele:
{ name: "Bacon Egg Cheese Sandwich", kette: "Dunkin' Donuts", kcal: 470, protein: 21, kh: 38, fett: 26, dessert: false }
{ name: "Glazed Donut", kette: "Dunkin' Donuts", kcal: 220, protein: 3, kh: 27, fett: 11, dessert: true }
- Dessert-Filter wird vor der Sortierung und vor der Kombinationssuche angewendet
- Ergibt der Dessert-Filter zusammen mit dem Ketten-Filter keine Treffer: "Keine Produkte für diesen Filter gefunden!" (bestehende Regel, gilt auch hier)
-Standardmäßig soll für den zweiten Filter (Alle Produkte/Dessert/kein Dessert) auf <Alle Produkte> eingestellt sein
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
(Ab hier mit Sortierung und Filter)
Eingabe: <400; 0; 10> Sortierung: <Standardeinstellung (Dropdown unverändert)> Filter: <kein Filter>
Sollwert <McChicken, McDonald's ,400kcal, 17g P, 40g K, 20g F; Original Recipe Chicken Breast, KFC, 390kcal, 33g P, 12g K, 24g F>
Eingabe: <400; 0; 10> Sortierung: <nach Protein, absteigend> Filter: <kein Filter>
Sollwert <Original Recipe Chicken Breast, KFC, 390kcal, 33g P, 12g K, 24g F; McChicken, McDonald's ,400kcal, 17g P, 40g K, 20g F>
Eingabe: <490; 70; 0> Sortierung: <nach Protein, absteigend> Filter: <kein Filter>
Sollwert <Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F; Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
Eingabe: <490; 70; 0> Sortierung: <nach Protein, absteigend> Filter: <Burger King>
Sollwert <Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
Eingabe: <490; 70; 10> Sortierung: <nach Kalorien, aufsteigend> Filter: <kein Filter>
Sollwert <Zinger Burger, KFC, 480kcal, 24g P, 42g K, 24g F; Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F; Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F>
Eingabe: <490; 70; 10> Sortierung: <nach Kalorien, absteigend> Filter: <kein Filter>
Sollwert <Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F; Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F; Zinger Burger, KFC, 480kcal, 24g P, 42g K, 24g F>
(Ab hier mit zusätzlichen Dessert Filter)
Eingabe: <490; 70; 0> Sortierung: <nach Kalorien, absteigend> Filter1: <McDonald's> Filter2:<Alle Produkte>
Sollwert <Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F>
Kombinationen:
<Pommes (mittel), McDonald's ,330kcal, 4g P, 42g K, 16g F + Cola (0,4 l), McDonald's ,170kcal, 0g P, 42g K, 0g F>
<Cheeseburger, McDonald's ,320kcal, 16g P, 33g K, 14g F + Cola (0,4 l), McDonald's ,170kcal, 0g P, 42g K, 0g F>
Eingabe: <490; 70; 0> Sortierung: <nach Kalorien, absteigend> Filter1: <Burger King> Filter2: <kein Dessert>
Sollwert <Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
Eingabe: <490; 70; 0> Sortierung: <nach Kalorien, absteigend> Filter1: <Burger King> Filter2: <Dessert>
Sollwert <Keine Produkte für diesen Filter gefunden!>
Eingabe: <490; 70; 0> Sortierung: <nach Protein, absteigend> Filter1: <Burger King> Filter2: <Dessert>
Sollwert <Keine Produkte für diesen Filter gefunden!>
Eingabe: <220; 0; 0> Sortierung: <nach Protein, absteigend> Filter1: <kein Filter> Filter2: <Dessert>
Sollwert <Glazed Donut, Dunkin' Donuts, 220kcal, 3g P, 27g K, 11g F>
Eingabe: <220; 0; 0> Sortierung: <nach Protein, absteigend> Filter1: <kein Filter> Filter2: <kein Dessert>
Sollwert <Keine Produkte für diesen Filter gefunden!>
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
Alle Testfälle prüfen bei Rückgabe der Funktion vom Agenten
</Meine Prüfpflicht>