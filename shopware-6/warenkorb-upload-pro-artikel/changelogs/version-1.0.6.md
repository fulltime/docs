# Version 1.0.6

**Situation:**

Es gab ein Problem mit speziellen Dateitypen und der Medienverwaltung in Shopware. Vor der Version 1.0.6 wurden alle übertragenen Daten in die Medienverwaltung von Shopware kopiert. Diese Medienverwaltung ist durch eine eigene Definition der erlaubten Dateitypen beschränkt. Durch diese wurde beim Bestellabschluss mit nicht erlaubten Dateitypen ein Fehler geworfen und die Bestellung konnte nicht ausgeführt werden.

**Lösung:**

Das kopieren der Uploads beim Bestellabschluss in die Medienverwaltung wurde entfernt.Die Uploads werden nun im System aus dem Cache Ordner in den Final Ordner kopiert. Die Daten zu einer Bestellung können weiterhin im Admin in den Bestelldetails eingesehen bzw. heruntergeladen werden.

Möchten Sie nun alte Daten löschen, muss dies per FTP geschehen. Gehen Sie dazu in public/uploads/final

Die Erlaubten Dateitypen können nun wieder wie gewohnt in den Plugin-Einstellungen definiert werden.
