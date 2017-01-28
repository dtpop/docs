# Paginierung

Paginierungen werden für unterschiedlichste Zwecke eingesetzt. Genannt seien hier Datensätze einer Liste oder Newseinträge in einem Archiv. Paginierungen können im Backend und im Frontend eingesetzt werden. Genau zu diesen Zwecken kann man die in REDAXO vorgefertigte Paginierungsklasse rex_pager einsetzen. Das rex_pager Objekt ist für die Paginierung zuständig. Die Anzeige der jeweiligen Inhalte (Datensätze, Artikel etc.) wird unabhängig davon programmiert.

Wir beginnen direkt mit einem Beispiel.

    <?php $pager = new rex_pager(50,'offset') ?>
    
erstellt ein neues Paginierungsobjekt, es werden maximal 50 Einträge pro Seite angezeigt. Standard ist 30. Der Parameter, der die Paginierung steuert, heißt in unserem Beispiel *offset*. Standard ist *start*.

Der Wert *offset* wird als get oder post Parameter erwartet und gibt die Anzahl der Datensätze an, ab der die Anzeige beginnt. Wir können also diesen Parameter nutzen und in eine SQL-Abfrage zur Anzeige einbauen.

Mit

    <?php $pager->setRowCount(123) ?>
    
wird die Gesamtanzahl der anzuzeigenden Elemente festgelegt. Der Wert kann mit

    <?php $numRowsTotal = $pager->getRowCount() ?>
    
ausgelesen werden.

Damit kann der Pager berechnen, wie viele Seiten für die Darstellung aller Datensätze benötigt werden. Der Wert kann mit

    <?php $totalPages = $pager->getPageCount() ?>

