
PRÜFUNGSDATENBANK Version 2.0

PHP-Anwendung mit MySQL/MariaDB-Datenbank
lauffähig in einer XAMPP-Entwicklungsumgebung

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Anwendungsumfang - gelieferte Dateien:

1. readme.txt     (diese Datei)
2. pruefungen.sql (MySQL-Datenbank-Dump)
3. pruefungen.zip (PHP-Frontend)

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


History
*******

Die Prüfungsdatenbank war ursprünglich als Webanwendung entwickelt worden, welche auf einer Microsoft SQL-Datenbank aufbaute.
Um den Installationsprozess zu vereinfachen und die Ressourcenkosten zu reduzieren, wurde die Datenbank Ende 2015 nach MySQL migriert
und das PHP-Frontend neu entwickelt.


Benötigte XAMPP-Version
***********************

Die vorliegende Version der Prüfungsdatenbank kommt mit einer "out of the box"-Installation von XAMPP aus.
(getestet bis XAMPP/PHP 5.6.15 mit MariaDB 10.1.9 unter Windows)

ACHTUNG!
Mit XAMPP/PHP Versionen 7.x ist die Anwendung NICHT ohne Anpassung der Einstellungen lauffähig! (Stand Februar 2016)
Grund: standardmäßig nicht eingebundener PDO-Treiber für MySQL/MariaDB (Für einen Workaround siehe Troubleshooting unten)


Installation
************

-> XAMPP herunterladen und installieren:
Auf der Seite www.apachefriends.org/de/download.html die letzte XAMPP-Version 5.x runterladen (z.B. xampp-win32-5.6.15-1-VC11-installer.exe)
Runtergeladene Datei ausführen und XAMPP installieren. Empfohlen wird die Installation in ein Verzeichnis
unterhalb des Rootverzeichnisses eines Partition (z.B. c:\xxamp\).
Eine Installation im Programm-Verzeichnis von Windows kann zu Rechteproblemen führen!

-> Webserver und Datenbankserver starten: 
XAMPP Control Panel v3.2.2, Dienste: Apache, MySQL starten ..
Nach der Installation das XAMPP Control-Panel starten: Start -> Alle Programme -> XAMPP -> XAMPP Control Panel
Dienste Apache (Webserver) & MySQL (Datenbankserver) mit den entsprechenden Buttons starten.
Sollte dies nicht möglich sein und es zu Fehlermeldungen (insbesondere beim Apache) kommen,
bitte einen Windows-Neustart durchführen und nochmals probieren. Sollte das auch nichts helfen,
ggf. in den Optionen von Skype den Haken entfernen, der Skype erlaubt, die Ports 80 und 443
für zusätzliche Eingehende Verbindungen zu benutzen.
Wenn Apache und MySQL laufen, einen Browser öffnen und in der Adresszeile 'localhost' eingeben, um zu prüfen,
ob sich die Willkommensseite von XAMPP angezeigen lässt.


-> Datenbank importieren:
PhpMyAdmin (Datenbankadministration) aufrufen durch Eingabe von 'localhost/phpmyadmin' in der Adresszeile des Browserfensters.
In der PHPMyAdmin-Konsole auf den Reiter 'Importieren' klicken.
Importdatei 'pruefungen.sql' mit der Funktion des Buttons 'Durchsuchen' auswählen, alle anderen Optionen auf den Standard-Einstellungen belassen.
Es wird die Datenbankinstanz 'pruefungen' einschliesslich Tabellen und benötigten Datensätzen angelegt 
und in der PHPMyAdmin-Konsole als weitere Datenbankinstanz angezeigt.

-> PHP-Frontend importieren:
Die Datei pruefungen.zip in das htdocs-Verzeichnis von XAMPP (z.B. C:\xampp\htdocs) entpacken, es wird der dort Ordner 'pruefungen' angelegt.

-> Prüfungsdatenbank öffnen:
In einem Browserfenster 'localhost/pruefungen' eingeben/ausführen.

-> Prüfungsdatenbank schliessen / Beenden der Anwendung: 
Vor schliessen der Anwendungsseiten vorsichtshalber Dienste stoppen ..

Troubleshooting
***************

Fehler 'Could not connect to database':

- Falls die Zugangsdaten oder der Port von MySQL/MariaDB geändert wurden,
  können diese in der Datei xampp\htdocs\pruefungen\conf\database.cfg angepasst werden.

- XAMPP ab Version 7.x
  Um die Datenbank unter XAMPP ab Version 7.x zum laufen zu bekommen, muss in der php.ini der PDO-Treiber für MySQL aktiviert werden.
  Hierzu im XAMPP Control-Panel in der Zeile 'Apache' auf den Button 'Konfig' klicken und 'PHP (php.ini)' auswählen.
  Es öffnet sich die Konfigurations-Datei von PHP im Editor. In dieser die Zeile ';extension=php_pdo_mysql.dll' suchen
  und das Semikolon am Anfang der Zeile entfernen. Anschließend die Datei speichern und schließen.
  Im XAMPP Control-Panel den Apache einmal stoppen und neu starten, dann die Seite 'localhost/pruefungen' erneut aufrufen bzw. aktualisieren.

Fehler in der Darstellung der Anwendung:
  
- Falls die Seite aus irgendwelchen Gründen nicht richtig angezeigt wird,
  kann die Fehlerausgabe in der Datei index.php aktiviert werden
  
- Falls die Themenstatistik nicht richtig angezeigt wird,
  kann die Datei json.php separat im Browser geöffnet werden, um ggf. Fehler zu finden.






