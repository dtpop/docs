# Fragmente

Fragmente werden in REDAXO eingesetzt, um wiederkehrende Codeschnippsel übersichtlich zu verwalten. Fragmente sind PHP Dateien und werden bei der Ausgabe geparst, sodass Variablen ausgegeben und verarbeitet werden können. In REDAXO selbst werden zahlreiche Fragmente für die Ausgabe des Backends verwendet. Diese Fragmente können auch als Ausgangsbasis für eigene Fragmente genutzt werden. Grundsätzlich wird ein Fragment in dieser Form angesrochen und ausgegeben:

    $fragment->parse('meinfragment.php');
    
Fragmente, die in addons im Verzeichnis fragments abgelegt werden, werden ohne Pfadangabe gefunden.

## Variablen in Fragmente

Fragmente können Variablen ausgeben, die zuvor dem Fragment per setVar zugewiesen wurden.

    $fragment->setVar('meinevar','Ich bin der Inhalt',false);
    
Die Ausgabe im Fragment erfolgt per

    echo $this->meinevar;
    
oder

    echo $this->getVar('meinevar');
    
Wenn eine Variable vom Typ Array übergeben wird, so kann dieses Array durchlaufen werden:

    $fragment->setVar('monate',['Januar','Februar','März','April','Mai','Juni','Juli','August','September','...']);
    
Ausgabe im Fragment:

    <ul>
    <?php foreach ($this->monate as $monat) : ?>
      <li><?= $monat ?></li>
    <?php endforeach ?>
    </ul>
    

    
