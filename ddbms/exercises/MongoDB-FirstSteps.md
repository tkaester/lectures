<h2>Vorwort</h2>

Alle folgenden Erläuterungen gehen davon aus, dass Sie entweder mit einem Mac oder mit einem Linux System (Ubuntun) arbeiten.

<h2>Installation</h2>

Unter macOS wird empfohlen, MongoDB via Anaconda (www.anaconda.com) zu installieren. Führen Sie dazu einfach folgendes Kommando aus:

conda install -c anaconda mongodb

Des Weiteren müssen Sie noch diverse Tools installieren, insbesondere mongorestore

conda install -c conda-forge mongo-tools


Für die Installation unter Ubuntu Linux folgen Sie bitte den folgenden Erläuterungen:

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/


<h2>Erste Schritte:</h2>

Von nun an, arbeiten Sie in einem Terminal bzw. Shell-Fenster. Bevor der MongoDB Prozess gestartet werden kann, muss ein Ordner für die entsprechenden Daten angelegt werden.

Dies können Sie z.B. in Ihrem Home-Verzeichnis tun:

mkdir $HOME/data


Als nächstes starten Sie den MongoDB Server, welcher per Default auf Port 27017 läuft:

mongod --dbpath $HOME/data

In Ihrer Konsole erscheinen nun die verschiedenen Log-Meldungen vom Start, in der Sie auch sehen können, dass der Server auf Port 27017 gestartet wurde.


<h2>Testdatensatz importieren</h2>

Mit dem folgenden Kommando können Sie in einer weiteren Konsole eine Datenbank anlegen und die Testdaten importieren:

mongorestore -d moviedb ./movies.bson

Dieses Kommando legt die Datenbank "moviedb" an sowie die Collection "movies" an. Letztere beinhaltet die einzelnen Dokumente.

<h2>Die MongoDB Shell</h2>

Als nächstes starten sie die MongoDB Shell:

mongo

Es erscheint nun ein Prompt, mit dem Sie verschiedene Eingaben machen können.

Mit folgendem Kommando können sie sich die aktuellen Datenbanken anzeigen lassen:

show dbs

Dort sollten Sie nach dem Import auch die Datenbank "moviedb" sehen. Mit folgendem Kommando können Sie diese benutzen:

use moviedb

Die vorhandenen Collections können Sie sich wie folgt anzeigen lassen:

show collections

Sie sehen dort nun auch die Collection "movies", die Datensätze (Dokumente) zu Filmen beinhaltet.

Mit folgendem Kommando können Sie sich den Inhalt dieser Collection anzeigen lassen:

db.movies.find()

Es werden ihnen nun die ersten 20 Einträge angezeigt. Wenn sie "it" eingeben, sehen Sie die nächsten 20 Einträge.

Um eine leserlichere Ausgabe zu erhalten, ergänzen Sie zum Kommando "pretty()", die bringt ihnen die Ausgabe in eine leserliche Formatierung:

db.movies.find().pretty()


Mit "limit(5)" können Sie die Ausgabe beispielsweise auf fünf Dokumente begrenzen:

db.movies.find().limit(5).pretty()

<h2>Referenzen und Tutorials</h2>
Weitere Informationen zu den vorhandenen Kommandos und verschiedene Tutorials finden sie unter:

https://docs.mongodb.com/manual/reference/database-references/

und

https://docs.mongodb.com/manual/tutorial/




