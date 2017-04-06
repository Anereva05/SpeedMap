
PR�FUNGSDATENBANK Version 2.0

PHP-Anwendung mit MySQL/MariaDB-Datenbank
lauff�hig in einer XAMPP-Entwicklungsumgebung

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Anwendungsumfang - gelieferte Dateien:

1. readme.txt     (diese Datei)
2. pruefungen.sql (MySQL-Datenbank-Dump)
3. pruefungen.zip (PHP-Frontend)

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


History
*******

Die Pr�fungsdatenbank war urspr�nglich als Webanwendung entwickelt worden, welche auf einer Microsoft SQL-Datenbank aufbaute.
Um den Installationsprozess zu vereinfachen und die Ressourcenkosten zu reduzieren, wurde die Datenbank Ende 2015 nach MySQL migriert
und das PHP-Frontend neu entwickelt.


Ben�tigte XAMPP-Version
***********************

Die vorliegende Version der Pr�fungsdatenbank kommt mit einer "out of the box"-Installation von XAMPP aus.
(getestet bis XAMPP/PHP 5.6.15 mit MariaDB 10.1.9 unter Windows)

ACHTUNG!
Mit XAMPP/PHP Versionen 7.x ist die Anwendung NICHT ohne Anpassung der Einstellungen lauff�hig! (Stand Februar 2016)
Grund: standardm��ig nicht eingebundener PDO-Treiber f�r MySQL/MariaDB (F�r einen Workaround siehe Troubleshooting unten)


Installation
************

-> XAMPP herunterladen und installieren:
Auf der Seite www.apachefriends.org/de/download.html die letzte XAMPP-Version 5.x runterladen (z.B. xampp-win32-5.6.15-1-VC11-installer.exe)
Runtergeladene Datei ausf�hren und XAMPP installieren. Empfohlen wird die Installation in ein Verzeichnis
unterhalb des Rootverzeichnisses eines Partition (z.B. c:\xxamp\).
Eine Installation im Programm-Verzeichnis von Windows kann zu Rechteproblemen f�hren!

-> Webserver und Datenbankserver starten: 
XAMPP Control Panel v3.2.2, Dienste: Apache, MySQL starten ..
Nach der Installation das XAMPP Control-Panel starten: Start -> Alle Programme -> XAMPP -> XAMPP Control Panel
Dienste Apache (Webserver) & MySQL (Datenbankserver) mit den entsprechenden Buttons starten.
Sollte dies nicht m�glich sein und es zu Fehlermeldungen (insbesondere beim Apache) kommen,
bitte einen Windows-Neustart durchf�hren und nochmals probieren. Sollte das auch nichts helfen,
ggf. in den Optionen von Skype den Haken entfernen, der Skype erlaubt, die Ports 80 und 443
f�r zus�tzliche Eingehende Verbindungen zu benutzen.
Wenn Apache und MySQL laufen, einen Browser �ffnen und in der Adresszeile 'localhost' eingeben, um zu pr�fen,
ob sich die Willkommensseite von XAMPP angezeigen l�sst.


-> Datenbank importieren:
PhpMyAdmin (Datenbankadministration) aufrufen durch Eingabe von 'localhost/phpmyadmin' in der Adresszeile des Browserfensters.
In der PHPMyAdmin-Konsole auf den Reiter 'Importieren' klicken.
Importdatei 'pruefungen.sql' mit der Funktion des Buttons 'Durchsuchen' ausw�hlen, alle anderen Optionen auf den Standard-Einstellungen belassen.
Es wird die Datenbankinstanz 'pruefungen' einschliesslich Tabellen und ben�tigten Datens�tzen angelegt 
und in der PHPMyAdmin-Konsole als weitere Datenbankinstanz angezeigt.

-> PHP-Frontend importieren:
Die Datei pruefungen.zip in das htdocs-Verzeichnis von XAMPP (z.B. C:\xampp\htdocs) entpacken, es wird der dort Ordner 'pruefungen' angelegt.

-> Pr�fungsdatenbank �ffnen:
In einem Browserfenster 'localhost/pruefungen' eingeben/ausf�hren.

-> Pr�fungsdatenbank schliessen / Beenden der Anwendung: 
Vor schliessen der Anwendungsseiten vorsichtshalber Dienste stoppen ..

Troubleshooting
***************

Fehler 'Could not connect to database':

- Falls die Zugangsdaten oder der Port von MySQL/MariaDB ge�ndert wurden,
  k�nnen diese in der Datei xampp\htdocs\pruefungen\conf\database.cfg angepasst werden.

- XAMPP ab Version 7.x
  Um die Datenbank unter XAMPP ab Version 7.x zum laufen zu bekommen, muss in der php.ini der PDO-Treiber f�r MySQL aktiviert werden.
  Hierzu im XAMPP Control-Panel in der Zeile 'Apache' auf den Button 'Konfig' klicken und 'PHP (php.ini)' ausw�hlen.
  Es �ffnet sich die Konfigurations-Datei von PHP im Editor. In dieser die Zeile ';extension=php_pdo_mysql.dll' suchen
  und das Semikolon am Anfang der Zeile entfernen. Anschlie�end die Datei speichern und schlie�en.
  Im XAMPP Control-Panel den Apache einmal stoppen und neu starten, dann die Seite 'localhost/pruefungen' erneut aufrufen bzw. aktualisieren.

Fehler in der Darstellung der Anwendung:
  
- Falls die Seite aus irgendwelchen Gr�nden nicht richtig angezeigt wird,
  kann die Fehlerausgabe in der Datei index.php aktiviert werden
  
- Falls die Themenstatistik nicht richtig angezeigt wird,
  kann die Datei json.php separat im Browser ge�ffnet werden, um ggf. Fehler zu finden.






