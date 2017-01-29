# Paginierung

Paginierungen werden für unterschiedlichste Zwecke eingesetzt. Genannt seien hier Datensätze einer Liste oder Newseinträge in einem Archiv. Paginierungen können im Backend und im Frontend eingesetzt werden. Genau zu diesen Zwecken kann man die in REDAXO vorgefertigte Paginierungsklasse rex_pager einsetzen. Das rex_pager Objekt ist für die Paginierung zuständig. Die Anzeige der jeweiligen Inhalte (Datensätze, Artikel etc.) wird unabhängig davon programmiert.

Wir beginnen direkt mit einem Beispiel.

    <?php $pager = new rex_pager(50,'offset') ?>
    
erstellt ein neues Paginierungsobjekt, es werden maximal 50 Einträge pro Seite angezeigt. Standard ist 30. Der Parameter, der die Paginierung steuert, heißt in unserem Beispiel *offset*. Standard ist *start*.

Der Wert *offset* wird als get oder post Parameter erwartet und gibt die Anzahl der Datensätze an, ab der die Anzeige beginnt. Wir können also diesen Parameter nutzen und in eine SQL-Abfrage zur Anzeige einbauen.

*Hinweis* Die interne Zählung für die Seitennummer des rex_pager Objekts beginnt bei 0.

Mit

    <?php $pager->setRowCount(123) ?>
    
wird die Gesamtanzahl der anzuzeigenden Elemente festgelegt. Der Wert kann mit

    <?php $numRowsTotal = $pager->getRowCount() ?>
    
ausgelesen werden.

Damit kann der Pager berechnen, wie viele Seiten für die Darstellung aller Datensätze benötigt werden. Der Wert kann mit

    <?php $totalPages = $pager->getPageCount() ?>
    
Eine einfache Ausgabe, z.B. in einem Modul, könnte dann so aussehen:

        <?php
        echo '<ul>';
            for ($page = $pager->getFirstPage(); $page <= $pager->getLastPage(); ++$page) {
                echo '<li><a href="'.rex_getUrl(rex_article::getCurrentId(),'',[$pager->getCursorName() => $pager->getCursor($page)]).'">'.($page + 1).'</a></li>';    
            }
        echo '</ul>';
        ?>

Eine etwas komplexere Ausgabe steht im Fragment fragments/core/navigations/pagination.php. Ein Beispiel einer kompletten Ausgabe einer Paginierung mit diesem Fragment steht im Kapitel Fragmente.

Weitere Methoden der rex_pager Klasse sind

        <?php
        // Anzahl Elemente pro Seite (Standard 30)
        $rowsPerPage = getRowsPerPage();
        
        // Liefert den Wert des aktuellen Cursors
        // bei optionaler Übergabe einer Seitenzahl den Cursorwert der Seite
        $cursor = getCursor( integer $pageNo = null );
        
        // prüft den übergebenen Cursorwert
        // Rückgabe: 1, wenn der Cursorwert innerhalb des definierten Bereiches ist
        //           0, wenn der Cursorwert nicht innerhalb des Bereiches liegt
        $isValidCursor = validateCursor( integer $cursor );
        
        // Liefert den Name des Cursors. Standard ist "start"
        $cursorName = getCursorName( );
        
        // Gibt 0 zurück, da der Offset für die erste Seite immer 0 ist        
        $offsetForFirstPage = getFirstPage( );
        
        // Gibt die Seitennummer für die vorhergehenden Seite zurück
        // Wert ist nie kleiner als die kleinste mögliche Seitennummer
        $prevPageNo = getPrevPage( );
        
        // Gibt die Seitennummer der aktuellen Seite zurück oder 0
        $currentPageNo = getCurrentPage( );
        
        // Gibt die Seitennummer für die nächste Seite zurück
        // Wert ist nie größer als die höchste mögliche Seitennummer
        $nextPageNo = getNextPage( );
        
        // Gibt die höchste mögliche Seitennummer zurück
        $lastPageNo = getLastPage( );
        
        // gibt true zurück, wenn der Cursor auf der übergebenen Seitennummer steht
        $isActivePage = isActivePage( integer $pageNo );
        ?>
        
        
