Zukünftige Änderungen in Kontext.md
<Ziel>
Der Benutzer soll auswählen können, ob nach Protein oder Kohlenhydrate oder Kalorien, aufsteigend oder absteigend sortiert werden soll.
Die Liste mit den Produkten wird online recherchiert und befindet sich in einer eigenen Datei.
Außerdem soll man nach Fast-Food-Ketten und zusätzlich nach Alle Produkte/Dessert/kein Dessert filtern können.
In der Ausgabe soll auch ein Feld mit Produktkombinationen erscheinen in der die Kombination aus mehreren Produkten die gewünschte Kalorienzahl ergibt.
</Ziel>
<Dateiübersicht>
"Backlog.md": Text mit zukünftigen Änderungen
"Produktliste": Liste mit allen recherchierten Produkten (Dateiformat noch nicht klar)
</Dateiübersicht>
<Regeln>
-Keine Auswahl der Sortierung: Standard-Reihenfolge nach Kalorien absteigend sortiert
-Ob ein Produkt Dessert oder kein Dessert ist wird von der KI entschieden und wird beim Anliegen jedes Produktes festgelegt (wie <kcal>)
-Bei falscher Entscheidung ob Dessert oder kein Dessert kann ich manuell die Produktangaben ändern.
-Standardmäßig soll für den zweiten Filter (Alle Produkte/Dessert/kein Dessert) auf <Alle Produkte> eingestellt sein
-Bei den Produktkombinationen müssen alle Produkte von der selben Kette sein
-Bei Produktkombinationen werden mindestens 2 und maximal 3 Produkte ausgegeben
-Bei Produktkombinationen ist der Spielraum genauso relevant
-Produktkombinationen sind auch Sortierbar nach den Sortierparameter (Summe aller Produkte als relevante Größe)
-Ausgabe, wenn keine passende Kombination gefunden wurde: "Keine passende Kombination gefunden"
- Ausgabe: Wenn Kalorienzahl + Spielraum exakt gleich dem Kalorienwert des Produktes ist: Produkt wird ausgegeben. (Auch für Produktkombinationen)
- Ausgabe: Wenn Kalorienzahl - Spielraum exakt gleich dem Kalorienwert des Produktes ist: Produkt wird ausgegeben. (Auch für Produktkombinationen)
- Ausgabe: Wenn Kalorienzahl exakt gleich dem kalorienärmsten Produktes ist: Produkt wird ausgegeben. (Auch für Produktkombinationen)
</Regeln>
<Testfälle>
Eingabe: <490; 70; 0> Sortierung: <nach Kalorien, absteigend> Filter1: <McDonald's> Filter2:<Alle Produkte>
Sollwert <Big Mac, McDonald's ,550kcal, 25g P, 45g K, 30g F>
Kombinationen:
<Pommes (mittel), McDonald's ,330kcal, 4g P, 42g K, 16g F + Cola (0,4 l), McDonald's ,170kcal, 0g P, 42g K, 0g F>
<Cheeseburger, McDonald's ,320kcal, 16g P, 33g K, 14g F + Cola (0,4 l), McDonald's ,170kcal, 0g P, 42g K, 0g F>
Eingabe: <490; 70; 0> Sortierung: <nach Kalorien, absteigend> Filter1: <Burger King> Filter2: <kein Dessert>
Sollwert <Chicken Royale, Burger King, 500kcal, 22g P, 44g K, 26g F>
Kombinationen:
<Kein passende Kombination gefunden>
Eingabe: <490; 70; 0> Sortierung: <nach Kalorien, absteigend> Filter1: <Burger King> Filter2: <Dessert>
Sollwert <Keine Produkte für diesen Filter gefunden!>
Kombinationen:
<Keine passende Kombination gefunden>
Eingabe: <490; 70; 0> Sortierung: <nach Protein, absteigend> Filter1: <Burger King> Filter2: <Dessert>
Sollwert <Keine Produkte für diesen Filter gefunden!>
Kombinationen:
<Keine passende Kombination gefunden>
</Testfälle>