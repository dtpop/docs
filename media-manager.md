# Media Manager

Der Media Manager ist ein Basis Addon von Redaxo, welches bereits mit der Grundinstallation installiert und aktiviert wird.
Das Addon dient zum Anpassen von Grafiken und Handling von Dateien anhand von Mediatypen. Die Mediatypen werden in der Verwaltung des Addons erstellt und konfiguriert. Jeder Mediatyp kann beliebig viele Effekte enthalten, die auf das aktuelle Medium angewendet werden. Zum einbinden eines Mediums muss dazu der Mediatyp in der Url notiert werden.

Die durch den Media Manager erstellten Bilddateien werden im Cache abgelegt.

Die am häufigsten benutzten Effekte für den Media Manager sind resize und crop. Damit können Bilder auf eine einheitliche Größe gebracht werden.

Folgende Effekte stehen zur Verfügung:

Effekt| Beschreibung
------------- | -------------
convert2img  |  konvertiert eine Quelldatei in ein Web-Format. Mögliche Formate für die Bildquelle: .pdf, .ps, .psd, .tif,     .tiff, .bmp, .eps, .ico. Mögliche Formate für das Ziel: .jpg, .png
crop  | beschneidet ein Bild auf die angegebene Größe (Angabe in Pixel)
filter_blur | Unschärfefilter
filter_colorize | Einfärben eines Bildes
filter_greyscale | Bild in Graustufen umwandeln
filter_sepia | Bild mit Sepiatönung versehen
filter_sharpen | Scharfzeichnen eines Bildes
flip | Kann ein Bild horizontal oder vertikal spiegeln
header | - Keine Ahnung - (muss ich mir noch anschauen)
insert_image | Ein Bild in ein anderes kopieren (z.B. für Wasserzeichen)
mediapath |  - Keine Ahnung - (muss ich mir noch anschauen)
mirror | Kann irgendeinen Spiegelungseffekt (muss ich mir noch anschauen)
resize | verkleinern / vergrößern unter Angabe der gewünschten Breite bzw. Höhe in Pixel. Die Werte können optional als minimal, maximal oder exakt angegeben werden
rounded_corners | braucht kein Mensch, dafür gibt es CSS
workspace | - Keine Ahnung - (muss ich mir noch anschauen)

Alle Effekte können kaskadiert werden.

### Einen Effekt definieren

    - Gehe im Addon-Menü auf den Menüpunkt "Media Manager"
    - Wähle in der Tabelle links oben das Plus-Zeichen (+)
    - Schreibe bei Name einen Namen, unter dem der Effekt verfügbar sein soll. Der Name wird für den Aufruf des Effekts über die Url verwendet (z.B. thumb_small)
    - Schreibe eine kurze Beschreibung zum Effekt (z.B. Galerie Vorschaubilder 120 x 120 Pixel)
    - Speichere den Effekt und wähle dann "Effekt bearbeiten"
    - 
    


### Beispiel einer Filterdefinition:

resize min 800px / min 600 / Vergrößerung ja
crop 800px / 600px

Erzeugt aus jeder Quelldatei ein Bild in 800 x 600 Pixel Größe
