Einleitung
==========

|image0|\  opsi Package Builder

opsi Package Builder ist ein Werkzeug zur Erstellung und Verwaltung von
Softwarepaketen in Zusammenarbeit mit dem

opsi (open pc server integration) Clientmanagementsystem der Firma uib
GmbH.

Hauptmerkmale der Anwendung sind:

-  Paketstrukturen anlegen und wiederholt bearbeiten
-  Abh�ngigkeiten und Produktvariablen anlegen, l�schen, bearbeiten
-  Changelog pflegen
-  Skriptverwaltung, inkl. eigenem SkriptEditor
-  Paketrechte setzen
-  Pakete bauen, installieren und entfernen
-  Zeitplaner: zeitgesteuerte Installationsauftr�ge per AT Job am Server
   verwalten (inkl. on\_demand und WakeOnLan)

Mit dem Personal Edition von HelpNDoc erstellt: \ `Kindle eBooks einfach
herstellen <http://www.helpndoc.com/de/funktionen-tour/ebooks-fuer-den-amazon-kindle-erstellen>`__

Technisches und Danke an...
===========================

Ein paar "Interna"...

-  Anwendung basiert auf der Skriptsprache AutoIt
-  EXE in 32Bit
-  Serververbindungen sind SSH-basiert und verschl�sselt
-  Jobsteuerung per ATD D�mon direkt am Server
-  Zugriff zu spezifischen Informationen direkt �ber die JSON
   Schnittstelle des opsi Servers

...und ein herzliches "Danke!" an:

`opsi - open pc server integration <http://www.opsi.org>`__

Ohne opsi w�rde es das ganze Projekt schlie�lich nicht geben...

`AutoIt v3 <http://www.autoitscript.com/site/autoit/>`__

`ISN AutoIt
Studio <http://isnetwork.isi-webportal.at/index.php/meine-programme/isn-autoit-studio>`__

Speziell die Entwicklungsumgebung ISN AutoIt Studio hat mir bei der
Umsetzung der GUI gro�artige Dienste geleistet.

`PuTTY/Plink SSH
Client <http://www.chiark.greenend.org.uk/~sgtatham/putty/>`__

PuTTY, ein echtes Urgestein...

`HelpNDoc Personal Edition <http://www.helpndoc.com>`__

`Console UDF by Prog@ndy (with some small
modifications) <http://www.autoit.de/index.php?page=Thread&amp;threadID=25634>`__

`Marquee UDF by
Melba23 <http://www.autoitscript.com/forum/index.php?showtopic=143711>`__

`ModernMenu UDF by Holger
Kotsch <http://www.autoitscript.com/forum/index.php?showtopic=20967>`__

`Translate UDF by
Prog@ndy <http://www.autoit.de/index.php?page=Thread&amp;postID=157444#post157444>`__

`JSMN UDF (2013/05/19) by
Ward <http://www.autoitscript.com/forum/topic/104150-json-udf-library-fully-rfc4627-compliant/>`__

`Extracts from WinAPI Extended UDF by
Yashied <http://www.autoitscript.com/forum/topic/98712-winapiex-udf/>`__

`IniArray UDF by
Raupi <http://ipv4.autoit.de/index.php?page=Thread&amp;postID=152417>`__

Tolle UDFs, die die Funktionalit�t von AutoIt extrem erweitern!

... und vielen anderen im \ `deutschen <http://www.autoit.de/>`__\  und
\ `englischen <http://www.autoitscript.com/forum/>`__\  AutoIt Forum,
deren Hilfe mir bei der Umsetzung der Entwicklung geholfen hat!

Mit dem Personal Edition von HelpNDoc erstellt: \ `Einfacher EPub und
Dokumentationseditor <http://www.helpndoc.com/de>`__

Programmoberfl�che
==================

|image1|

Nachfolgend werden die einzelnen Oberfl�chenbestandteile der Anwendung
beschrieben und, wenn vorhanden, auf Besonderheiten im Umgang damit
eingegangen.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
Kindle eBooks
Generator <http://www.helpndoc.com/de/funktionen-tour/ebooks-fuer-den-amazon-kindle-erstellen>`__

Start
-----

|image2|

Beim Programmstart k�nnen die meist verwendeten Funktionen aufgerufen
werden. F�r einen schnellen Arbeitsablauf lassen sich die einzelnen
Funktionen per Funktionstasten aufrufen.

.. raw:: html

   <div class="rvps2">

+-------------------------+-------------------------+-------------------------+
| Funktion                | Hotkey                  | Beschreibung            |
+-------------------------+-------------------------+-------------------------+
| Neues Paket             | F1                      | Ein neues Software      |
|                         |                         | Installationspaket im   |
|                         |                         | Entwicklungsordner      |
|                         |                         | anlegen                 |
+-------------------------+-------------------------+-------------------------+
| Paket �ffnen            | F2                      | Aus dem                 |
|                         |                         | Entwicklungsordner eine |
|                         |                         | bestehende              |
|                         |                         | Paketstruktur einlesen. |
|                         |                         | Es k�nnen keine         |
|                         |                         | gepackten Pakete        |
|                         |                         | (\*.opsi) ge�ffnet      |
|                         |                         | werden.                 |
+-------------------------+-------------------------+-------------------------+
| Zuletzt...              | F3                      | Die letzten f�nf        |
|                         |                         | bearbeiteten            |
|                         |                         | Paketstrukturen         |
+-------------------------+-------------------------+-------------------------+
| Paketb�ndel erzeugen    | F5                      | Hilfsfunktion zur       |
|                         |                         | Schnellanlage von       |
|                         |                         | Paketb�ndeln. Diese     |
|                         |                         | Funktion erzeugt ein    |
|                         |                         | Paket, welches nur      |
|                         |                         | Abh�ngigkeiten zu       |
|                         |                         | weiteren Pakete         |
|                         |                         | beinhaltet, um immer    |
|                         |                         | wiederkehrende          |
|                         |                         | Installationen der      |
|                         |                         | gleichen Produkte zu    |
|                         |                         | vereinfachen.           |
+-------------------------+-------------------------+-------------------------+
| Paket installieren      | F6                      | Bereits bestehende      |
|                         |                         | Paketdateien (\*.opsi)  |
|                         |                         | k�nnen hier�ber direkt  |
|                         |                         | auf dem Server          |
|                         |                         | installiert werden.     |
+-------------------------+-------------------------+-------------------------+
| Paket hochladen         | F7                      | Paket ohne Installation |
|                         |                         | in einen Repository     |
|                         |                         | Ordner hochladen        |
+-------------------------+-------------------------+-------------------------+
| Paket(e) entfernen      | F8                      | Bereits auf dem Server  |
|                         |                         | bestehende Pakete       |
|                         |                         | k�nnen hier�ber direkt  |
|                         |                         | deinstalliert werden.   |
+-------------------------+-------------------------+-------------------------+
| Zeitplaner              | F4                      | �ffnen des Zeitplaners  |
|                         |                         | zum Einstellen von AT   |
|                         |                         | Auftr�gen am opsi       |
|                         |                         | Server                  |
+-------------------------+-------------------------+-------------------------+
| Depot Manager           | F9                      | Depotverwaltung, bei    |
|                         |                         | ersten �ffnen werden    |
|                         |                         | alle Depotserver        |
|                         |                         | ausgelesen und f�r      |
|                         |                         | einen schnelleren       |
|                         |                         | Zugriff sp�ter gecacht. |
+-------------------------+-------------------------+-------------------------+
| Client Agent            | F10                     | Verteilung des          |
| installieren            |                         | opsi-client-agent via   |
|                         |                         | /var/lib/opsi/depot/ops |
|                         |                         | i-client-agent/opsi-dep |
|                         |                         | loy-client-agent        |
+-------------------------+-------------------------+-------------------------+
| Einstellungen           |                         | �ffnet den              |
|                         |                         | Einstellungendialog     |
+-------------------------+-------------------------+-------------------------+
| Beenden                 | Q / Esc                 | Beendet die Anwendung   |
+-------------------------+-------------------------+-------------------------+

.. raw:: html

   </div>

Mit dem Personal Edition von HelpNDoc erstellt: \ `Hilfedokumente
einfach erstellen <http://www.helpndoc.com/de/funktionen-tour>`__

Reiter "Paket"
--------------

|image3|

Dieser Reiter beinhaltet die wesentlichen Paketinformationen, wie sie
auch durch das opsi Tool "opsi-newprod" zur Paketanlage abgefragt
werden.

Die Bezeichnungen sind weitestgehend selbsterkl�rend, daher nur einige
Hinweise:

.. raw:: html

   <div class="rvps2">

+--------------------------------------+-------------------------------------+
| Feld / Funktion                      | Hinweis                             |
+--------------------------------------+-------------------------------------+
| Priorit�t                            | Mit dem Schieber l��t sich die      |
|                                      | Priorit�t von -100 bis +100         |
|                                      | einstellen. Zum Zur�cksetzen auf 0  |
|                                      | einmal auf das Anzeigefeld daneben  |
|                                      | klicken.                            |
+--------------------------------------+-------------------------------------+
| Skripteingabefelder                  | Diese Felder entsprechen den        |
| (Install/Deinstall./Aktualisieren/Im | unterschiedlichen opsi-winst        |
| mer/Einmalig/Benutzer/Anmeldung)     | Installationsskripten. N�here       |
|                                      | Informationen dazu finden sich in   |
|                                      | den opsi Anwendungshandb�chern.     |
+--------------------------------------+-------------------------------------+
| |image4|                             | �ffnet das nebenstehende Skript im  |
|                                      | in den                              |
|                                      | \ `Einstellungen <#Programmeinstellu|
|                                      | ngen>`__\                           |
|                                      | hinterlegten Editor. Standard ist   |
|                                      | notepad.exe.                        |
+--------------------------------------+-------------------------------------+
| |image5|                             | Zeigt einen Dateiauswahldialog      |
|                                      | relativ zum Paketordner an und      |
|                                      | stellt sicher, dass nur Skripte     |
|                                      | innerhalb des Paketes ausgew�hlt    |
|                                      | werden k�nnen.                      |
+--------------------------------------+-------------------------------------+
| |image6|                             | �ffnet den in den                   |
|                                      | \ `Einstellungen <#Programmeinstellu|
|                                      | ngen>`__\                           |
|                                      | gew�hlten Changelog Editor Typ.     |
|                                      | N�heres dazu unter "\ `Changelog    |
|                                      | Editor <#ChangelogEditor>`__\ "     |
+--------------------------------------+-------------------------------------+
| |image7|                             | �ffnet die                          |
|                                      | \ `Strukturanzeige <#Skriptbaum>`__ |
|                                      |                                     |
|                                      | der Installationsskripte. Von dort  |
|                                      | k�nnen auch s�mtliche per "sub" bzw.|
|                                      | "include" eingebundenen Skripte     |
|                                      | eingesehen und, sofern im           |
|                                      | Paketordner befindlich, bearbeitet  |
|                                      | werden. Au�erhalb des Paketordners  |
|                                      | abgelegte Skripte k�nnen aus        |
|                                      | Sicherheitsgr�nden nicht bearbeitet |
|                                      | werden.                             |
+--------------------------------------+-------------------------------------+

.. raw:: html

   </div>

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis
Hilfeverfassungsumfeld <http://www.helpndoc.com/de/hilfeentwicklungs-tool>`__

Reiter "Abh�ngigkeit"
---------------------

|image8|

Auf diesem Reiter k�nnen Paketabh�ngigkeiten (product dependencies)
definiert und bearbeitet werden.

Der obere Teil des Fensters beinhaltet eine tabellarische Aufstellung
der derzeit im Paket definierten Abh�ngigkeiten. Sollte in der Liste nur
ein einziger Eintrag in der Spalte "Aktion" mit dem Inhalt "empty"
angezeigt werden, so wei�t das daraufhin, dass noch keinerlei
Abh�ngigkeiten definiert worden sind.

.. raw:: html

   <div class="rvps2">

+-------------------------+-------------------------+-------------------------+
| Feld / Funktion         | Beschreibung            | Hinweise                |
+-------------------------+-------------------------+-------------------------+
| Aktionsbezug            | F�r welche angeforderte | M�gliche Werte: setup / |
|                         | Aktion ist diese        | uninstall / update      |
|                         | Abh�ngigkeit g�ltig.    |                         |
+-------------------------+-------------------------+-------------------------+
| Notw. Produkt ID        | Produkt zu dem die      | Entweder ein            |
| (Auswahlliste /         | Abh�ngigkeit besteht    | bestehendes,            |
| Freitextfeld)           |                         | installiertes Produkt   |
|                         |                         | aus der Liste           |
|                         |                         | ausw�hlen, oder im      |
|                         |                         | Freitextfeld die        |
|                         |                         | Produkt ID eines        |
|                         |                         | derzeit nicht           |
|                         |                         | vorhandenen Produkts    |
|                         |                         | eingeben.               |
+-------------------------+-------------------------+-------------------------+
| Geford. Aktion          | Aktion, die f�r das     | M�gliche Werte: none /  |
|                         | abh�ngige Produkt       | setup / update          |
|                         | angefordert werden soll |                         |
|                         |                         | Werden "setup" oder     |
|                         |                         | "update" gew�hlt, wird  |
|                         |                         | der "Notw.              |
|                         |                         | Installationsstatus"    |
|                         |                         | autom. auf "none"       |
|                         |                         | gesetzt.                |
+-------------------------+-------------------------+-------------------------+
| Notw.                   | Installationsstatus,    | M�gliche Werte: none /  |
| Installationsstatus     | den das abh�ngige       | installed               |
|                         | Produkt besitzen muss   |                         |
|                         |                         | Wird "installed"        |
|                         |                         | gew�hlt, wird die       |
|                         |                         | "Geford. Aktion" autom. |
|                         |                         | auf "none" gesetzt.     |
+-------------------------+-------------------------+-------------------------+
| Reihenfolge             | Reihenfolge, in der die | M�gliche Werte: before  |
|                         | Abh�ngigkeit zum        | / after                 |
|                         | aktuellen Paket         |                         |
|                         | aufgel�st werden soll.  |                         |
+-------------------------+-------------------------+-------------------------+
| |image9|                | Eine neue Abh�ngigkeit  |                         |
|                         | anlegen.                |                         |
|                         |                         |                         |
|                         | Es �ffnet sich ein      |                         |
|                         | Dialogfenster, in dem   |                         |
|                         | die neuen Werte erfasst |                         |
|                         | werden k�nnen. Die      |                         |
|                         | Feldbezeichnungen und   |                         |
|                         | -vorgaben lauten        |                         |
|                         | entsprechend.           |                         |
+-------------------------+-------------------------+-------------------------+
| |image10|               | Eine bestehende         | Wenn der Reiter         |
|                         | Abh�ngigkeit �ndern und | gewechselt wird, ohne   |
|                         | aktualisieren.          | die �nderung zu         |
|                         |                         | �bernehmen, gehen diese |
|                         | Um eine bestehende      | i d. R. verloren.       |
|                         | Abh�ngigkeit zu         |                         |
|                         | ver�ndern, wie folgt    |                         |
|                         | vorgehen:               |                         |
|                         |                         |                         |
|                         | #. in der               |                         |
|                         |    tabellarischen       |                         |
|                         |    Auflistung die       |                         |
|                         |    entsprechende Zeile  |                         |
|                         |    anklicken            |                         |
|                         | #. die Werte in den     |                         |
|                         |    einzelnen Feldern    |                         |
|                         |    entsprechend         |                         |
|                         |    anpassen             |                         |
|                         | #. auf "�bernehmen"     |                         |
|                         |    klicken              |                         |
|                         |                         |                         |
|                         | Die �nderung wird       |                         |
|                         | sofort in die           |                         |
|                         | tabellarische           |                         |
|                         | Auflistung �bernommen.  |                         |
+-------------------------+-------------------------+-------------------------+
| |image11|               | Eine bestehende         | Solange das Paket nicht |
|                         | Abh�ngigkeit entfernen. | gespeichert wurde, kann |
|                         |                         | eine ungewollte         |
|                         | Um eine bestehende      | L�schung durch erneutes |
|                         | Abh�ngigkeit zu         | Einladen r�ckg�ngig     |
|                         | entfernen, wie folgt    | gemacht werden. Nach    |
|                         | vorgehen:               | dem Speichern muss die  |
|                         |                         | Vorg�ngerversion der    |
|                         | #. in der               | control Datei manuell   |
|                         |    tabellarischen       | aus dem                 |
|                         |    Auflistung die       | Unterverzeichnis "OPSI" |
|                         |    entsprechende Zeile  | des Pakets              |
|                         |    anklicken            | zur�ckgesichert werden. |
|                         | #. auf "L�schen"        |                         |
|                         |    klicken              |                         |
|                         | #. den nachfolgenden    |                         |
|                         |    Warnhinweis          |                         |
|                         |    best�tigen           |                         |
|                         |                         |                         |
|                         | Die �nderung wird       |                         |
|                         | sofort in die           |                         |
|                         | tabellarische           |                         |
|                         | Auflistung �bernommen.  |                         |
+-------------------------+-------------------------+-------------------------+

.. raw:: html

   </div>

.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis
HTML-Hilfedokumentationsgenerator <http://www.helpndoc.com/de>`__

Reiter "Produktvariablen"
-------------------------

|image12|

Auf diesem Reiter k�nnen Produktvariablen (product properties) definiert
und bearbeitet werden.

Der obere Teil des Fensters beinhaltet eine tabellarische Aufstellung
der derzeit im Paket definierten Produktvariablen. Sollte in der Liste
nur ein einziger Eintrag in der Spalte "Bezeichner" mit dem Inhalt
"empty" angezeigt werden, so wei�t das daraufhin, dass noch keinerlei
Produktvariablen definiert worden sind.

.. raw:: html

   <div class="rvps2">

+-------------------------+-------------------------+-------------------------+
| Feld / Funktion         | Beschreibung            | Hinweise                |
+-------------------------+-------------------------+-------------------------+
| Bezeichner              | Name der                | Dieser Bezeichner wird  |
|                         | Produktvariable         | in der                  |
|                         |                         | Produktkonfiguration im |
|                         |                         | opsi-configed angezeigt |
|                         |                         | und ist innerhalb der   |
|                         |                         | Skripte mit der         |
|                         |                         | Funktion                |
|                         |                         | "GetProductProperty"    |
|                         |                         | auslesbar.              |
|                         |                         |                         |
|                         |                         | Weitere Informationen   |
|                         |                         | siehe OPSI Getting      |
|                         |                         | Started Handbuch.       |
+-------------------------+-------------------------+-------------------------+
| Typ                     | Variablentyp            | M�gliche Werte: unicode |
|                         |                         | / bool                  |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Mehrfachwert            | Bestimmt, ob die        | Nur bei Typ "unicode"   |
|                         | Produktvariable nur     | verf�gbar               |
|                         | genau einen oder        |                         |
|                         | mehrere Werte annehmen  |                         |
|                         | kann                    |                         |
+-------------------------+-------------------------+-------------------------+
| �nderbar                | Bestimmt, ob die        | Nur bei Typ "unicode"   |
|                         | Vorgabewerte mit neuen  | verf�gbar               |
|                         | oder zus�tzlichen       |                         |
|                         | Werten �berschrieben    |                         |
|                         | werden k�nnen oder      |                         |
|                         | nicht                   |                         |
+-------------------------+-------------------------+-------------------------+
| Beschreibung            | Beschreibung der        | Wird im opsi-configed   |
|                         | Variablenfunktion       | als Tooltip angezeigt   |
+-------------------------+-------------------------+-------------------------+
| Werte                   | Komma-separiert Liste   | Falls "�nderbar" auf    |
|                         | der m�glichen           | "True" gesetzt wurde,   |
|                         | Eingabewerte            | kann die Liste sp�ter   |
|                         |                         | innerhalb von           |
|                         |                         | opsi-configed erg�nzt   |
|                         |                         | werden.                 |
|                         |                         |                         |
|                         |                         | Nur bei Typ "unicode"   |
|                         |                         | verf�gbar               |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Vorgabe (Freitextfeld / | Vorgabewert             | Nur bei Typ "unicode"   |
| Auswahlliste)           |                         | verf�gbar: Freitextfeld |
|                         |                         |                         |
|                         |                         | Nur bei Typ "bool"      |
|                         |                         | verf�gbar: Auswahlliste |
+-------------------------+-------------------------+-------------------------+
| |image13|               | Eine neue               |                         |
|                         | Produktvariable         |                         |
|                         | anlegen.                |                         |
|                         |                         |                         |
|                         | Es �ffnet sich ein      |                         |
|                         | Dialogfenster, in dem   |                         |
|                         | die neuen Werte erfasst |                         |
|                         | werden k�nnen. Die      |                         |
|                         | Feldbezeichnungen und   |                         |
|                         | -vorgaben lauten        |                         |
|                         | entsprechend.           |                         |
+-------------------------+-------------------------+-------------------------+
| |image14|               | Eine bestehende         | Wenn der Reiter         |
|                         | Produktvariable �ndern  | gewechselt wird, ohne   |
|                         | und aktualisieren.      | die �nderung zu         |
|                         |                         | �bernehmen, gehen diese |
|                         | Um eine bestehende      | i d. R. verloren.       |
|                         | Produktvariable zu      |                         |
|                         | ver�ndern, wie folgt    |                         |
|                         | vorgehen:               |                         |
|                         |                         |                         |
|                         | #. in der               |                         |
|                         |    tabellarischen       |                         |
|                         |    Auflistung die       |                         |
|                         |    entsprechende Zeile  |                         |
|                         |    anklicken            |                         |
|                         | #. die Werte in den     |                         |
|                         |    einzelnen Feldern    |                         |
|                         |    entsprechend         |                         |
|                         |    anpassen             |                         |
|                         | #. auf "�bernehmen"     |                         |
|                         |    klicken              |                         |
|                         |                         |                         |
|                         | Die �nderung wird       |                         |
|                         | sofort in die           |                         |
|                         | tabellarische           |                         |
|                         | Auflistung �bernommen.  |                         |
+-------------------------+-------------------------+-------------------------+
| |image15|               | Diese Funktion          | Werden Produktvariablen |
|                         | erm�glicht das          | gefunden, so wird f�r   |
|                         | automatische Ermitteln  | jede neue Variable ein  |
|                         | und Einlesen von        | kompletter Datensatz    |
|                         | Produktvariablen, die   | abgefragt.              |
|                         | in den verschiedenen    |                         |
|                         | Installationsskripten   | Die bereits vorhandenen |
|                         | definiert sind.         | und definierten         |
|                         |                         | Produktvariablen werden |
|                         | Das erleichtert         | ber�cksichtigt und nur  |
|                         | allerdings die Suche    | neue aufgenommen.       |
|                         | und Eintragung neuer    |                         |
|                         | Produktvariablen, die   |                         |
|                         | im Rahmen der           |                         |
|                         | Skriptentwicklung hinzu |                         |
|                         | gekommen sind.          |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| |image16|               | Eine bestehende         | Solange das Paket nicht |
|                         | Produktvariable         | gespeichert wurde, kann |
|                         | entfernen.              | eine ungewollte         |
|                         |                         | L�schung durch erneutes |
|                         | Um eine bestehende      | Einladen r�ckg�ngig     |
|                         | Produktvariable zu      | gemacht werden. Nach    |
|                         | entfernen, wie folgt    | dem Speichern muss die  |
|                         | vorgehen:               | Vorg�ngerversion der    |
|                         |                         | control Datei manuell   |
|                         | #. in der               | aus dem                 |
|                         |    tabellarischen       | Unterverzeichnis "OPSI" |
|                         |    Auflistung die       | des Pakets              |
|                         |    entsprechende Zeile  | zur�ckgesichert werden. |
|                         |    anklicken            |                         |
|                         | #. auf "L�schen"        |                         |
|                         |    klicken              |                         |
|                         | #. den nachfolgenden    |                         |
|                         |    Warnhinweis          |                         |
|                         |    best�tigen           |                         |
|                         |                         |                         |
|                         | Die �nderung wird       |                         |
|                         | sofort in die           |                         |
|                         | tabellarische           |                         |
|                         | Auflistung �bernommen.  |                         |
+-------------------------+-------------------------+-------------------------+

.. raw:: html

   </div>

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
Dokumentationsgenerator <http://www.helpndoc.com/de>`__

Paketfunktionen
---------------

|image17|

Im unteren Teil des Anwendungsfensters bleiben die Onlinefunktionen, die
zur Verf�gung, stehen jederzeit sichtbar.

Funktionsbeschreibung

| Hinweis zur nachfolgenden Aufstellung:
| Es k�nnen ab Version 7.0 erweiterten Depotfunktionen aktiviert werden.
  Dann sind alle manuell hinterlegten Befehle au�er Kraft,
| sondern werden ja nach verwendetem Depot intern autom. erzeugt.

.. raw:: html

   <div class="rvps2">

+-------------------------+---------------------------+-------------------------+
| Funktion                | Beschreibung              | Besonderheiten bei      |
|                         |                         = | Offline Nutzung         |
+-------------------------+---------------------------+-------------------------+
| Paketordner             | Der Ordnername des      - |                         |
|                         | aktuell ge�ffneten        |                         |
|                         | Pakets.                 - |                         |
+-------------------------+---------------------------+-------------------------+
| Basis                   | Der in den             -- | Tempor�rer              |
| Entwicklungsordner      | \ `Einstellungen <#Allg   | Entwicklungsordner      |
|                         | emein>`__\             -- | Laufwerk C:\\ wird      |
|                         | hinterlegte Stammordner   | automatisch             |
|                         | f�r Paketentwicklung.  -- | eingestellt.            |
+-------------------------+---------------------------+-------------------------+
| |image18|               | Onlinefunktion:        -- | Die Funktion steht      |
|                         |                           | nicht zur Verf�gung.    |
|                         | L�st per SSH Verbindung-- |                         |
|                         | zum opsi Server die       |                         |
|                         | Paketerzeugung aus.    -- |                         |
|                         |                           |                         |
|                         |                        -  |                         |
|                         |  `<#opsiVerwaltungsbefeh  |                         |
|                         | le>`__                 -- |                         |
|                         |                           |                         |
|                         | `Standardeinstellung <#-- |                         |
|                         | opsiVerwaltungsbefehle>   |                         |
|                         | `__\                   -- |                         |
|                         | des verwendeten           |                         |
|                         | Befehls:               -- |                         |
|                         |                           |                         |
|                         | opsi-makeproductfile   -- |                         |
|                         | -vv                       |                         |
|                         |                        -- |                         |
|                         | Weitere Informationen     |                         |
|                         | dazu im opsi Handbuch. -- |                         |
+-------------------------+---------------------------+-------------------------+
| |image19|               | Onlinefunktion:        -- | Die Funktion steht      |
|                         |                           | nicht zur Verf�gung.    |
|                         | Weist per SSH          -- |                         |
|                         | Verbindung den opsi       |                         |
|                         | Server an, dass zu     -- |                         |
|                         | dieser Version            |                         |
|                         | vorliegende            -- |                         |
|                         | Installationspaket in     |                         |
|                         | das Depot einzuspielen.-- |                         |
|                         |                           |                         |
|                         | `Standardeinstellung ---- |                         |
|                         | <#opsiVerwaltungsbefehle> |                         |
|                         | `__\                   -- |                         |
|                         | des verwendeten           |                         |
|                         | Befehls:                - |                         |
|                         |                           |                         |
|                         | opsi-package-manager -i-- |                         |
|                         | -q                        |                         |
|                         |                        -- |                         |
|                         | Es k�nnen auch mehrere    |                         |
|                         | Depots angesprochen    -- |                         |
|                         | werden. Um bspw. 2        |                         |
|                         | bestimmte Depots zu    -- |                         |
|                         | versorgen, �ndern sie     |                         |
|                         | den eingetragenen      -- |                         |
|                         | Befehl wie folgt ab:      |                         |
|                         |                        -- |                         |
|                         | opsi-package-manager -i   |                         |
|                         | -d <depot1>,<depot2> -q-- |                         |
|                         |                           |                         |
|                         | wobei f�r <depot1> und -- |                         |
|                         | <depot2> die jeweilige    |                         |
|                         | DepotID verwendet      -- |                         |
|                         | werden muss.              |                         |
|                         |                        -- |                         |
|                         | Um alle Depots mit        |                         |
|                         | einem Paket zu         -- |                         |
|                         | versorgen, �ndern sie     |                         |
|                         | den eingetragenen      -- |                         |
|                         | Befehl wie folgt ab:      |                         |
|                         |                        -- |                         |
|                         | opsi-package-manager -i   |                         |
|                         | -d all -q              -- |                         |
|                         |                           |                         |
|                         | WICHTIG: "-q" muss     -- |                         |
|                         | immer als letzter         |                         |
|                         | Parameter verwendet    -- |                         |
|                         | werden!                   |                         |
|                         |                        -- |                         |
|                         | Weitere Informationen     |                         |
|                         | dazu im opsi Handbuch. -- |                         |
|                         |                           |                         |
+-------------------------+---------------------------+-------------------------+
| |image20|               | siehe "Installieren" -    | Die Funktion steht      |
|                         | zus�tzlich dazu wird   -- | nicht zur Verf�gung.    |
|                         | das Paket  auf allen      |                         |
|                         | Maschinen, auf denen es-- |                         |
|                         | als "installed"           |                         |
|                         | gekennzeichnet ist, auf-- |                         |
|                         | "setup" gesetzt.          |                         |
+-------------------------+---------------------------+-------------------------+
| |image21|               | Onlinefunktion:           | Die Funktion steht      |
|                         |                        -- | nicht zur Verf�gung.    |
|                         | Weist per SSH             |                         |
|                         | Verbindung den opsi    -- |                         |
|                         | Server an, die aktuell    |                         |
|                         | ge�ffnete Version aus  -- |                         |
|                         | dem Softwaredepot zu      |                         |
|                         | entfernen.             -- |                         |
|                         |                           |                         |
|                         | `Standardeinstellung <#-- |                         |
|                         | opsiVerwaltungsbefehle>   |                         |
|                         | `__\                   -- |                         |
|                         | des verwendeten           |                         |
|                         | Befehls:               -- |                         |
|                         |                           |                         |
|                         | opsi-package-manager -r-- |                         |
|                         | -q                        |                         |
|                         |                        -- |                         |
|                         | WICHTIG: "-q" muss        |                         |
|                         | immer als letzter      -- |                         |
|                         | Parameter verwendet       |                         |
|                         | werden!                -- |                         |
|                         |                           |                         |
|                         | Weitere Informationen  -- |                         |
|                         | dazu im opsi Handbuch.    |                         |
+-------------------------+---------------------------+-------------------------+
| |image22|               | �ffnet den aktuellen      |                         |
|                         | Paketordner in einem   -- |                         |
|                         | Explorerfenster.          |                         |
+-------------------------+---------------------------+-------------------------+
| |image23|               | Backup der                |                         |
|                         | vorhergehenden         -- |                         |
|                         | Paketkonfiguration und    |                         |
|                         | Speichern der aktuellen-- |                         |
|                         | Informationen. Dies       |                         |
|                         | erzeugt die control    -- |                         |
|                         | Datei des Pakets neu.     |                         |
+-------------------------+---------------------------+-------------------------+

.. raw:: html

   </div>

Einschr�nkungen

Einige der o. a. Funktionen stehen nur unter bestimmten Voraussetzungen
zur Verf�gung:

.. raw:: html

   <div class="rvps2">

+--------------------------------------+--------------------------------------+
| Funktion                             | Voraussetzung                        |
+--------------------------------------+--------------------------------------+
| |image24|                            | Liegt zur aktuellen Paketversion     |
|                                      | eine bereits gepackte \*.opsi Datei  |
|                                      | im Paketordner vor, so wird diese    |
|                                      | Schaltfl�che aktiviert.              |
+--------------------------------------+--------------------------------------+
| |image25|                            | Schaltfl�che wird aktiviert, wenn    |
|                                      | ein Produkt mit der zugeh�rigen      |
|                                      | ProduktID auf dem Server installiert |
|                                      | ist und entfernt werden kann.        |
+--------------------------------------+--------------------------------------+

.. raw:: html

   </div>

Mit dem Personal Edition von HelpNDoc erstellt: \ `CHM-Hilfedokumente
einfach erstellen <http://www.helpndoc.com/de/funktionen-tour>`__

Changelog Editor
----------------

|image26|

Beschreibung zur Changelog Editor Funktionalit�t

Mit Hilfe des Changelog Editors k�nnen die in der Control Dateisektion
[Changelog] hinterlegten Eintr�ge gepflegt werden. Da der Aufbau dieser
Sektion, im Gegensatz zur sonstigen Struktur der Control Datei, nicht
fest vorgegeben ist, ist es grunds�tzlich m�glich, diese Sektion
unterschiedlich mit Informationen anzureichern.

Variante 1:

Unterhalb der Sektions�berschrift wird unstrukturierter Freitext
hinterlegt. Auch wenn damit eine Dokumentation nat�rlich grunds�tzlich
m�glich ist, so kann diese Art der Dokumentation mit einigen
Einschr�nkungen verbunden sein. Neben der Tatsache, da� Flie�text nicht
zwingend die Lesbarkeit erh�ht, so dokumentiert er ggf. auch nicht
notwendige Informationen, um die zu dokumentierenden �nderungen
zeitlich, bzgl. ihrer Wichtigkeit oder auch bezogen auf den Autor der
�nderung einzugliedern.

Variante 2:

Die Changelog Eintr�ge werden nach einem festen Schema zeitlich
absteigend sortiert in Textbl�cken hinterlegt. Sie erhalten eine
feststehende �berschrift (=Kopfzeile) und einen Abschlussvermerk
(=Fu�zeile), der den Eintrag n�her beschreibt. Diese Eintragungsart wird
auch bei der Paketanlage von opsi-newprod f�r den ersten Eintrag
verwendet.

Um diesen beiden Paradigmen Rechnung zu tragen, enth�lt opsi Package
Builder zwei verschiedene Arten von Editoren f�r die Changelog Eintr�ge,
den \ `einfachen <#Einfach>`__\  (Variante 1) und den
\ `erweiterten <#Erweitert>`__\  (Variante 2) Editor.

Beim �ffnen eines Pakets wird der gesamte Text innerhalb der
[Changelog]-Sektion der Control Datei gem�� der in den \ `Einstellungen
gew�hlten Editorvariante <#Programmeinstellungen>`__\  eingelesen. F�r
den Betrieb des erweiterten Editors spielt dabei zus�tzlich der Eintrag
im \ `Feld "Blockerkennung" <#Programmeinstellungen>`__\  eine
entscheidende Rolle. Findet opsi Package Builder beim Einlesen eine
Textzeile, die den dort hinterlegten Eintrag beinhaltet, wird der
nachfolgende Text als neuer Changelog Textblock erkannt.

Achtung:

Die Changelog Eintr�ge der Control Datei werden nur einmalig beim �ffnen
des Pakets geladen und interpretiert. Sollten in der Zwischenzeit bei
ge�ffnetem Paket �nderungen an den Einstellungen zur Verwendung des
Editors oder der Blockerkennung durchgef�hrt werden, so muss das
ge�ffnete Paket geschlossen und wieder ge�ffnet werden.

Hinweise zur Bestandspflege "alter" Pakete

Soll ein bereits bestehendes Paket mit opsi Package Builder gepflegt
werden, so ist es f�r die weiterf�hrende Pflege der "alten" Changelog
Eintr�ge wichtig, ob in der Vergangenheit mit Variante 1 oder 2
gearbeitet wurde.

-  wurde ausschlie�lich mit Variante 1 gearbeitet:

| In den Einstellungen sollte der Haken bei "Erweiterten Changelog
  Editor verwenden" entfernt werden. Damit kann die Pflege auf gewohnte
  Weise fortgesetzt werden. Sollen die alten Eintr�ge in die neue,
  strukturierte Form �berf�hrt werden, ist wie in der Hilfe unter
  \ `Konvertierungshinweise <#Konvertierungshinweise>`__\  beschrieben
  vorzugehen.
| 

-  wurde ausschlie�lich mit Variante 2 gearbeitet:

In den Einstellungen sollte der Haken bei "Erweiterten Changelog Editor
verwenden" gesetzt werden. Zus�tzlich sollte �berpr�ft werden, ob die
verwendete �berschrift (=Kopfzeile) den in den \ `Einstellungen im Feld
"Blockerkennung" <#Programmeinstellungen>`__\  hinterlegten Text
beinhaltet. Wurde eine eigene, wiederkehrende Textmarkierung verwendet,
ist der Wert in den Einstellungen entsprechend anzupassen. Weitere
Informationen dazu \ `hier <#Konvertierungshinweise>`__\ .

Beispiele f�r strukturierte Changelog Eintr�ge in der Control Datei zur
Verwendung mit opsi Package Builder

        

1. Eintr�ge gem. opsi-newprod Vorgabe und Grundeinstellung in opsi
Package Builder:

[Changelog]

acroread (11.0.01-2) stable; urgency=low

  \* Test abgeschlossen

  \* Paket in stable

 -- Holger Pandel <holger.pandel@....de>  Wed, 31 Jan 2013 11:43:01
+0000

acroread (11.0.01-1) testing; urgency=low

  \* Initial package

 -- Holger Pandel <holger.pandel@....de>  Wed, 30 Jan 2013 16:25:01
+0000

Die gr�n markierte Textstelle kehrt bei jedem Changelog Eintrag wieder
und kennzeichnet damit den Beginn eines neuen Textblocks. Sie wird gem.
der Standardeinstellung in opsi Package Builder zur Blockerkennung
verwendet.

2. Eintr�ge mit selbstgew�hlter, wiederkehrender Struktur

[Changelog]

Lfd. Nr. der �nderung: 2 am  31 Jan 2013 11:43:01

Paketversion: 11.0.01-2

Status: stable

urgency=low

  \* Test abgeschlossen

  \* Paket in stable

 -- Holger Pandel <holger.pandel@....de>

Lfd. Nr. der �nderung: 1 am 15 Jan 2013 13:28:15

Paketversion: 11.0.01-1

Status: testing

urgency=low

  \* Initial package

 -- Holger Pandel <holger.pandel@....de>

Die gr�n markierte Textstelle kehrt bei jedem Changelog Eintrag wieder
und kennzeichnet damit den Beginn eines neuen Textblocks. Sie kann somit
ebenfalls zur Blockerkennung verwendet werden und muss in
den\ `Einstellungen im Feld
"Blockerkennung" <#Programmeinstellungen>`__\  hinterlegt werden. Es ist
jedoch hierbei darauf zu achten, dass dieser Begriff nicht zus�tzlich im
Langtext des Changelog Eintrags auftaucht, um Fehler bei der
Blockerkennung zu vermeiden.

Vorteile bei der Nutzung des Standardverhaltens

Wird das Standardverhalten von opsi Package Builder beibehalten, k�nnen
mit den Funktionen und zus�tzlichen Auswahlfeldern im erweiterten Editor
komfortabel und schnell neue Eintr�ge angelegt werden, die vollst�ndig
kompatibel zur Blockerkennung von opsi Package Builder sind. Falls doch
eine individuelle Blockgestaltung genutzt werden soll ist
sicherzustellen, dass die Blockmarkierung, die im individuellen
Eingabefeld eingegeben wird eindeutig ist.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis
iPhone-Dokumentationsgenerator <http://www.helpndoc.com/de/funktionen-tour/erstellen-sie-iphone-webseiten-und-dokumentationen>`__

Einfach
~~~~~~~

|image27|

Ist in den \ `Einstellungen <#Programmeinstellungen>`__\  die Nutzung
des erweiterten Changelog Editors deaktiviert, erscheint beim Klick auf
die Schaltfl�che "Changelog" im \ `Reiter "Paket" <#ReiterPaket>`__\ 
das einfache Editorfenster. Hier kann reiner Flie�text in beliebiger
Form als Hinterlegt werden.

Wird der Editor �ber die Schaltfl�che \ |image28|\  geschlossen, werden
autom. s�mtliche �nderungen �bernommen.

Hinweis:

Ist der erweiterte Editor ausgew�hlt und es tritt beim Einlesen eines
Pakets ein Fehler bei der Changelog Blockerkennung auf, so wird
ebenfalls der einfache Editor ge�ffnet. Der Benutzer erh�lt einen
entsprechenden Warnhinweis.

Mit dem Personal Edition von HelpNDoc erstellt: \ `iPhone Websites
einfach
gemacht <http://www.helpndoc.com/de/funktionen-tour/erstellen-sie-iphone-webseiten-und-dokumentationen>`__

Erweitert
~~~~~~~~~

|image29|

Ist in den \ `Einstellungen <#Programmeinstellungen>`__\  die Nutzung
des erweiterten Changelog Editors aktiviert, erscheint beim Klick auf
die Schaltfl�che "Changelog" im \ `Reiter "Paket" <#ReiterPaket>`__\ 
das erweiterte Editorfenster. Damit k�nnen die einzelnen Changelog
Eintr�ge komfortabel verwaltet werden.

Hinweis:

Ist der erweiterte Editor ausgew�hlt und es tritt beim Einlesen eines
Pakets ein Fehler bei der Changelog Blockerkennung auf, so wird der
einfache Editor ge�ffnet. Der Benutzer erh�lt einen entsprechenden
Warnhinweis.

.. raw:: html

   <div class="rvps2">

+-------------------------+-------------------------+-------------------------+
| Feld / Funktion         | Beschreibung            | Hinweise                |
+-------------------------+-------------------------+-------------------------+
| Tabelle "Changelog      | Alle vorhandenen        | absteigend sortiert     |
| Entry"                  | Changelog Eintr�ge in   |                         |
|                         | der Reihenfolge der     |                         |
|                         | Anlage                  |                         |
+-------------------------+-------------------------+-------------------------+
| Feld 1                  | Paketversion des        | nur Anzeige             |
|                         | Changelog Eintrags      |                         |
|                         |                         | nur aktiv bei           |
|                         |                         | Standardblockerkennung  |
+-------------------------+-------------------------+-------------------------+
| Feld 2                  | Paketstatus Markierung  | M�gliche Werte: testing |
|                         |                         | / stable                |
|                         |                         |                         |
|                         |                         | nur aktiv bei           |
|                         |                         | Standardblockerkennung  |
+-------------------------+-------------------------+-------------------------+
| Feld 3                  | Dringlichkeitsmarkierun | M�gliche Werte:         |
|                         | g                       | urgency=low /           |
|                         | der �nderung            | urgency=middle /        |
|                         |                         | urgency=high            |
|                         |                         |                         |
|                         |                         | nur aktiv bei           |
|                         |                         | Standardblockerkennung  |
+-------------------------+-------------------------+-------------------------+
| Feld 4                  | Individuelles Header    | nur aktiv bei           |
|                         | Feld                    | individueller           |
|                         |                         | Blockerkennung          |
+-------------------------+-------------------------+-------------------------+
| unteres Editorfeld      | Langtext des Changelog  |                         |
|                         | Eintrags                |                         |
+-------------------------+-------------------------+-------------------------+
| |image30|               | Erzeugen eines neuen    | Der Eintrag bekommt     |
|                         | Eintrags                | einen initialen Text    |
|                         |                         | und eine letzte Zeile   |
|                         |                         | nach dem Schema         |
|                         |                         |                         |
|                         |                         | Maintainer/Mail/Datum/U |
|                         |                         | hrzeit/UTC              |
+-------------------------+-------------------------+-------------------------+
| |image31|               | �nderungen �bernehmen   | S�mtliche �nderungen    |
|                         |                         | gro�en Textfeld, die    |
|                         |                         | nicht �bernommen        |
|                         |                         | wurden, gehen beim      |
|                         |                         | Schlie�en des Dialogs   |
|                         |                         | verloren.               |
+-------------------------+-------------------------+-------------------------+
| |image32|               | Entfernen eines         | Es kann immer nur ein   |
|                         | Changelog Eintrags      | Eintrag auf einmal      |
|                         |                         | entfernt werden.        |
+-------------------------+-------------------------+-------------------------+
| |image33|               | Beenden des Dialogs     | Alle nicht �bernommenen |
|                         |                         | �nderungen im Textfeld  |
|                         |                         | gehen verloren.         |
+-------------------------+-------------------------+-------------------------+

.. raw:: html

   </div>

Unterschiede in der Darstellung zwischen Standardblockerkennung und
individueller Blockerkennung

Standardblockerkennung

Bei der Standardblockerkennung sind die erweiterten Auswahl- und
Eingabefelder aktiv.

|image34|

Individuelle Blockerkennung

Bei der individuellen Blockerkennung ist nur das freie Eingabefeld
verf�gbar.

|image35|

Mit dem Personal Edition von HelpNDoc erstellt: \ `CHM, PDF, DOC und
HTML Hilfeerstellung von einer einzigen Quelle
aus <http://www.helpndoc.com/de/hilfeentwicklungs-tool>`__

Konvertierungshinweise
~~~~~~~~~~~~~~~~~~~~~~

Konvertierung von einfacher in erweiterte Darstellung und Funktionalit�t

Alte Changelog Eintr�ge, die nicht einer festen strukturierten Form
entsprechen, k�nnen in die strukturierte Form �berf�hrt werden, ohne
dass die Inhalte verloren gehen.

Dazu ist folgende Reihenfolge in der Vorgehensweise einzuhalten:

#. opsi Package Builder starten
#. unter "Einstellungen" - "Programmeinstellungen" den Haken bei
   "Erweiterten Changelog Editor verwenden" entfernen (die auftretende
   Meldung kann ignoriert werden, solange kein Paket geladen ist)
#. das Paket mit den zu konvertierenden Changelog Eintr�gen �ffnen
#. unter "Einstellungen" - "Programmeinstellungen" den Haken bei
   "Erweiterten Changelog Editor verwenden" setzen
   es erfolgt folgende Meldung:
   |image36|

#. das Paket speichern

Jetzt liegt das Changelog inkl. der alten Eintr�ge im neuen Format vor
und kann mit dem erweiterten Editor bearbeitet werden.

Beispiel f�r umgestellte Eintr�ge

Eintr�ge vor der Konvertierung:

[Changelog]

Das hier ist nur allgemeines Changelog blabla ohne Struktur

damit l��t sich nicht viel anfangen

aber gehen tuts auch

brabrabra

t�t�ta

Eintr�ge nach der Konvertierung:

[Changelog]

acroread (11.0.01-2) testing; urgency=low

  \* ChangeLog converted via opsi PackageBuilder editor

                ----------- ALTES CHANGELOG FORMAT -----------

                Das hier ist nur allgemeines Changelog blabla ohne
Struktur

                

                damit l��t sich nicht viel anfangen

                aber gehen tuts auch

                

                brabrabra

                

                t�t�ta

                

                

                ----------- ALTES CHANGELOG FORMAT -----------

 -- Holger Pandel <holger.pandel@....de> Tue, 02 Apr 2013 18:03:37 +
0100

Konvertierung von erweiterter in einfache Darstellung und Funktionalit�t

In diese Richtung findet keine Konvertierung statt. Es reicht, unter
"Einstellungen" - "Programmeinstellungen" den Haken bei "Erweiterten
Changelog Editor verwenden" zu entfernen.

Sollte zu diesem Zeitpunkt bereits ein Paket geladen sein, erfolgt
nachstehender Hinweis:

|image37|

Dies erfolgt aus Sicherheitsgr�nden, um keinen der bestehenden Eintr�ge
zu verlieren.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
EPub-Generator <http://www.helpndoc.com/de/epub-ebooks-erstellen>`__

Skriptbaum
----------

|image38|

Im Skriptbaum werden die einzelnen m�glichen Steuerskripte f�r
opsi-winst dargestellt, inklusive der verwendeten Include-Dateien.

Mit einem Doppelklick kann ein vorhandenes Skript direkt aus der
Baumdarstellung heraus mit dem in den
\ `Einstellungen <#Programmeinstellungen>`__\  verkn�pften Editor
(\ `intern <#ToolSkriptEditor>`__\  oder extern) ge�ffnet werden.

opsi-winst bietet die M�glichkeit, immer wiederkehrende Funktionen in
separate Dateien auszulagern, die dann per Include-Anweisung eingebunden
werden. Diese Include-Dateien werden dabei in der Regel von mehreren
Paketen referenziert.

Um zu verhindern, dass diese Skripte unbeabsichtigt oder aus
Unwissenheit heraus fehlerhaft ge�ndert werden und diese �nderung sich
automatisch auf s�mtliche Pakete auswirkt, die diese Skripte verwenden,
k�nnen daher aus der Baumdarstellung heraus nur Dateien ge�ffnet werden,
die sich im CLIENT\_DATA Ordner des aktuell ge�ffneten Pakets befinden.

Skripte, die nicht ge�ndert werden k�nnen, werden in Klammern "( .. )"
dargestellt. Zus�tzlich erh�lt der Anwender beim Versuch ein solches
Skript zu �ffnen, eine Warnmeldung.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Web-basierte
iPhone-Dokumentation
erstellen <http://www.helpndoc.com/de/funktionen-tour/erstellen-sie-iphone-webseiten-und-dokumentationen>`__

Zeitplaner
----------

|image39|

Der Zeitplaner erm�glicht die Anlage und Verwaltung von zeitgesteuerten
(De-)Installationsauftr�gen von localboot Paketen direkt am opsi Server.
Bitte die \ `technischen Voraussetzungen <#TechnischeHinweise>`__\ 
daf�r unbedingt lesen!

Hinweis:

Da sowohl beim �ffnen des Zeitplaners, als auch nach dem Schlie�en des
Auftragsanlagedialogs die bestehenden Auftr�ge direkt vom Server
abgerufen werden, kann es einen Moment dauern. Bitte hier um etwas
Geduld, vor allem bei vielen vorhandenen Auftr�gen.

.. raw:: html

   <div class="rvps2">

+-------------------------+-------------------------+-------------------------+
| Funktion                | Hotkey                  | Beschreibung            |
+-------------------------+-------------------------+-------------------------+
| |image40|               | F1                      | Neue                    |
|                         |                         | (De-)Installationsauftr |
|                         |                         | �ge                     |
|                         |                         | anlegen                 |
+-------------------------+-------------------------+-------------------------+
| |image41|               | F2                      | Einzelne, ausgew�hlte   |
|                         |                         | Auftr�ge l�schen, es    |
|                         |                         | erfolgt eine            |
|                         |                         | Sicherheitsabfrage      |
+-------------------------+-------------------------+-------------------------+
| |image42|               | F3                      | Aktualisieren der       |
|                         |                         | Anzeige                 |
+-------------------------+-------------------------+-------------------------+
| |image43|               | F4                      | S�mtliche aktiven       |
|                         |                         | Auftr�ge entfernen, es  |
|                         |                         | erfolgt eine            |
|                         |                         | Sicherheitsabfrage      |
+-------------------------+-------------------------+-------------------------+
| |image44|               |                         | Schlie�en der Anzeige   |
+-------------------------+-------------------------+-------------------------+

.. raw:: html

   </div>

Erl�uterungen zur Spalte "Aktion"

Hier werden die unterschiedlichen Auftragstypen angezeigt:

setup:                Installanstionsanforderung

uninstall:        Deinstallationsanforderung

wol:                Vor dem eigentlichen Auftrag wird ein Wake On Lan
Paket an die betreffende Maschine gesendet.

on\_demand:        Nachdem die Auftr�ge eingestellt worden sind, wird
ein "on\_demand" Ereignis ausgel�st.

Mit dem Personal Edition von HelpNDoc erstellt: \ `iPhone-Dokumentation
einfach
erstellen <http://www.helpndoc.com/de/funktionen-tour/erstellen-sie-iphone-webseiten-und-dokumentationen>`__

Auftr�ge anlegen
~~~~~~~~~~~~~~~~

|image45|

In diesem Dialog wird ein neuer (Massen-)Auftrag definiert. Bitte auf
jeden Fall auch die \ `technischen Hinweise <#TechnischeHinweise>`__\ 
beachten!

.. raw:: html

   <div class="rvps2">

+--------------------------------------+--------------------------------------+
| Feld / Funktion                      | Hinweis                              |
+--------------------------------------+--------------------------------------+
| Liste "Arbeitspl�tze"                | Alle am opsi Server definierten      |
|                                      | Clients                              |
|                                      |                                      |
|                                      | Mit Hilfe der <Ctrl>-Taste k�nnen    |
|                                      | mehrere Arbeitspl�tze auf einmal     |
|                                      | ausgew�hlt werden. Die Auftr�ge      |
|                                      | werden dann f�r alle ausgew�hlten    |
|                                      | Arbeitspl�tzen gleicherma�en         |
|                                      | angelegt.                            |
+--------------------------------------+--------------------------------------+
| Liste "Produkte"                     | S�mtliche aktive localboot Pakete    |
|                                      |                                      |
|                                      | Die Auswahl erfolgt �ber die         |
|                                      | Kontrollk�stchen vor der Produkt ID. |
+--------------------------------------+--------------------------------------+
| Kalenderansicht                      | Geplantes Datum der Auftr�ge, der    |
|                                      | aktuelle Tag ist dabei hervorgehoben |
+--------------------------------------+--------------------------------------+
| Uhrzeitfeld                          | Startzeit der Auftr�ge               |
+--------------------------------------+--------------------------------------+
| Durchzuf�hrende Aktion               | Install = Setzt den                  |
|                                      | Anforderungsstatus des Pakets an der |
|                                      | Maschine auf "setup"                 |
|                                      |                                      |
|                                      | Uninstall = Setzt den                |
|                                      | Anforderungsstatus des Pakets an der |
|                                      | Maschine auf "uninstall"             |
|                                      |                                      |
|                                      | (Update = derzeit nicht verwendet)   |
+--------------------------------------+--------------------------------------+
| Event 'on\_demand'                   | Haken setzen, um einen on\_demand    |
|                                      | Auftrag pro Maschine zus�tzlich      |
|                                      | erstellen zu lassen                  |
+--------------------------------------+--------------------------------------+
| Wake On Lan                          | Haken setzen, um einen WakeOnLan     |
|                                      | Auftrag pro Maschine zus�tzlich      |
|                                      | erstellen zu lassen                  |
|                                      |                                      |
|                                      | Der WakeOnLan Auftrag wird mit dem   |
|                                      | in den                               |
|                                      | \ `Einstellungen <#opsiVerwaltungsbe |
|                                      | fehle>`__\                           |
|                                      | hinterlegten Vorlauf erstellt.       |
|                                      | Standardvorlauf ist 15 Minuten.      |
+--------------------------------------+--------------------------------------+
| |image46|                            | Joberzeugung ansto�en                |
+--------------------------------------+--------------------------------------+
| |image47|                            | Abbrechen, es werden keine Jobs      |
|                                      | erstellt.                            |
+--------------------------------------+--------------------------------------+

.. raw:: html

   </div>

Hinweise

Mit dem Personal Edition von HelpNDoc erstellt: \ `EPub-B�cher f�r das
iPad verfassen <http://www.helpndoc.com/de/epub-ebooks-erstellen>`__

Technische Hinweise
~~~~~~~~~~~~~~~~~~~

Verwendung des Zeitplaners:

Die von opsi Package Builder verwalteten Softwareverwaltungsauftr�ge
werden im Hintergrund direkt am opsi Server als sogenannte AT Auftr�ge
eingestellt. Dazu ist die Installation des ATD D�mon und der zugeh�rigen
Kommandozeilentools erforderlich. Wie dieser D�mon zu installieren ist,
kann der technischen Beschreibung der verwendeten Linux Distribution,
auf der der opsi Server installiert ist, entnommen werden.

AT Auftr�ge bestehen technisch gesehen aus einzelnen Linux Skripten, die
in einer bestimmten Reihenfolge und zu einem vordefinierten Zeitpunkt
ausgef�hrt werden. Diese befinden sich im sogenannten Spool-Verzeichnis
des ATD D�mon und k�nnen durch den Anwender oder Administrator direkt an
der Serverkonsole �ber die Kommandozeilentools at, atq, atrm, etc.
verwaltet werden. opsi Package Builder verwendet die gleichen Tools zur
Pflege der AT Auftr�ge.

Wenn viele AT Auftr�ge angelegt werden, spielt es im Rahmen der
Verwaltung mittels opsi Package Builder eine gro�e Rolle, wie viele
Dateien durch einen Benutzer gleichzeitig ge�ffnet werden d�rfen, da der
opsi Package Builder beim Anlegen und Auslesen der Auftr�ge jeden
einzelnen Auftrag analysieren muss. Da in gro�en Netzwerken aufgrund der
hohen Rechneranzahl durchaus viele Auftr�ge vorhanden sein k�nnen, ist
es gar nicht selten, dass auch mehrere tausend Auftr�ge erzeugt werden.

Linux ist als Betriebssystem in einem hohen Ma� konfigurierbar, um u. a.
vielen Einsatzm�glichkeiten gerecht zu werden. Aus Sicherheitsgr�nden
l��t sich daher die Anzahl der gleichzeitig zu �ffnenden Dateien
limitieren. Dieses Limit wird auch 'ulimit' genannt. Wenn dieses Limit
zu gering eingestellt ist, kann es bei der Verwaltung der AT Auftr�ge zu
Fehlern kommen. Daher sollte das eingestellte Limit VOR der Anlage einer
gr��eren Anzahl von Auftr�gen auf jeden Fall kontrolliert und ggf.
angepasst werden.

Um das ulimit zu �berpr�fen, meldet man sich am opsi Server direkt als
root Benutzer an und setzt folgendes Kommando ab: ulimit -n

Die damit ermittelte Zahl entspricht der Anzahl der gleichzeitig
ge�ffneten Dateien. In vielen F�llen wird dieser Wert auf 1024
eingestellt sein, sofern man nicht bereits vorher Anpassungen
vorgenommen hat. Um diesen Wert dauerhaft zu erh�hen, muss ein evtl.
bereits vorhandener Eintrag in der Datei /etc/security/limits.conf
angepasst oder eine neue Zeile hinzugef�gt werden. Um bspw. diesen Wert
auf 5000 zu erh�hen, wird folgender Eintrag ben�tigt:

\* soft nofile 5000

Dabei haben die 4 Werte folgende Bedeutung:

\*        - der Eintrag gilt f�r jeden Benutzer -> damit lie�e sich die
Anzahl der offenen Dateien auch nur speziell f�r den opsi-admin Benutzer
anpassen

soft        - der Wert kann nachtr�glich durch den Benutzer wieder
ge�ndert werden

nofile        - der Eintrag regelt die Anzahl der offenen Dateien

5000        - Wert der eingestellt werden soll

Mit der beispielhaft angegeben Zeile wird also f�r jeden User die Anzahl
der gleichzeitig offenen Dateien nachtr�glich �nderbar auf 5000 gesetzt.

Zus�tzlicher Hinweis zu CentOS (aufgetreten bei Version 6.4), k�nnte
aber auch bei anderen Linux-Distributionen wichtig sein:

Sollte der ATD zwischen der Abarbeitung der Jobs immer eine Pause
einlegen (1 od. mehrere Minuten), dann kann das folgenderma�en
korrigiert werden:

In der Datei /etc/sysconfig/atd daf�r sorgen, dass die OPTS-Variable mit
den Parametern -b 0 erg�nzt wird. Falls die Variable noch gar nicht
vorhanden ist, den folgenden Eintrag ans Ende der Datei anh�ngen:

OPTS="-b 0"

Der Parameter -b 0 deaktiviert die Pause zwischen der Ausf�hrung der
einzelnen AT-Jobs.

Ist der Wert eingetragen und gespeichert, muss der ATD neu gestartet
werden. Unter CentOS 6.4 kann das durch einen service atd restart Befehl
an der Konsole als root User erfolgen.

(Diese Beschreibung gilt nur f�r CentOS, dass die Startparameter f�r den
ATD aus der genannten Datei zieht. Es ist im Einzelfall pro Distribution
zu pr�fen, wo der genannte Parameter eingef�gt werden muss, damit der
ATD die Anpassung beim Neustart mitbekommt.)

Verwendung des Auftragsanlagedialogs:

-  Beim ersten �ffnen werden s�mtliche Maschinen und aktiven Localboot
   Produkte vom opsi Server ermittelt. Das kann bei einer hohen Anzahl
   Clients und Produkten einige Zeit in Anspruch nehmen! Bitte hier
   Geduld bewahren. Der Auslesevorgang findet auch nur einmalig nach
   Programmstart statt, au�er es wurde in den Einstellungen der Haken
   bei "Beim �ffnen des Zeitplaners Maschinen und Produkte immer
   einlesen" gesetzt. Dann werden die Daten bei jedem �ffnen des
   Zeitplaners ermittelt.
-  Wenn viele Auftr�ge auf einmal am Server eingestellt werden sollen,
   bitte Geduld bewahren! Das kann eine je nach Menge eine Weile in
   Anspruch nehmen:
   Beispielrechnung: 100 Clients � 5 Produkte, inkl. on\_demand und wol
   bedeutet 700 (!) Einzelauftr�ge
   In solchen F�llen kann es sinnvoll sein, statt der Einzelauftr�ge ein
   Paketb�ndel anzulegen und die (wie in diesem Beispiel 5) Produkte
   zusammenzufassen. Das senkt die Anzahl der Auftr�ge maximal.
   F�r die \ `Schnellanlage von Paketb�ndeln <#Paketbndelerzeugen>`__\ 
   kann die da�fr vorgesehen Funktion in opsi Package Builder genutzt
   werden.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
Kindle eBooks
Generator <http://www.helpndoc.com/de/funktionen-tour/ebooks-fuer-den-amazon-kindle-erstellen>`__

Paketb�ndel erzeugen
--------------------

|image48|

Mit der Funktion "Paketb�ndel erzeugen" k�nnen sog.
Meta-Installationspakete erstellt werden. Diese Pakete beinhalten
keinerlei Skriptfunktionalit�t, sondern bestehen nur aus Abh�ngigkeiten
zu anderen Paketen.

Beispiel:

Auf allen Clients sollen immer wieder die gleichen 15 Softwarepakete
installiert werden. Um nicht bei jedem Client 15 Pakete auf "setup"
setzen zu m�ssen mit der Gefahr, einzelne Pakete oder Clients
auszulassen, kann alternativ ein weiteres Paket erzeugt werden, das eine
Abh�ngigkeit zu allen anderen 15 Paketen besitzt. Wird dieses Paket auf
"setup" gesetzt, wird es gem�� seiner Abh�ngigkeiten erst dann
installiert, wenn s�mtliche anderen, abh�ngigen Pakete erfolgreich
installiert worden sind.

Damit lassen sich sehr leicht gruppen- und zweckorientierte
Anwendungspakete schn�ren.

Vorgehensweise

Um mit Hilfe von opsi Package Builder solche B�ndel zu erzeugen, einfach
wie folgt vorgehen:

#. �ber den Startdialog oder das Anwendungsmen� die Funktion
   "Paketb�ndel erzeugen" ausw�hlen Daraufhin werden s�mtliche aktiven
   Localboot Pakete des verbundenen opsi Servers ermittelt (sofern noch
   nicht geschehen, bspw. durch �ffnen des Zeitplaners) und in einer
   Tabelle dargestellt.
#. Die zu b�ndelnden Produkte mit einem Haken vor der Produkt ID
   versehen.
#. Den Dialog mit der Schaltfl�che "OK" best�tigen.
#. In der nachfolgenden Abfrage eine neue Produkt ID f�r das Meta-Paket
   erfassen und den Dialog mit "Ok" best�tigen. Es wird gepr�ft, ob ein
   Paket gleichen Namens existiert.

Damit ist generell ein neues Paket mit den entsprechenden Gegebenheiten
angelegt. Soll das Paket jetzt noch zus�tzlich direkt auf dem Server
gebaut und installiert werden, so auch den nachfolgenden Dialog mit "Ja"
best�tigen.

|image49|

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis EPub und
Dokumentationsgenerator <http://www.helpndoc.com/de>`__

Depot Manager
-------------

|image50|

Mit dem Depot Manager k�nnen Verwaltungsaufgaben im Bereich der
Softwaredepots vorgenommen. Hierzu geh�ren:

- Einlesen der einzelnen Depotst�nde

- Einlesen des Repository Ordners (/var/lib/opsi/repository)

- Vergleichen verschiedener Depots untereinander, hierbei sind alle
Kombination m�glich: Depot<->Depot, Repo<->Repo und Depot<->Repo

- Installieren / Deinstallieren /Upload von Paketen in einzelne Depots

- L�schen von Paketen aus dem Repository Verzeichnis

Hinweis:

Die Depotfunktionen sind bei der ersten Inbetriebnahme deaktiviert und
k�nnen in den Einstellungen, Reiter opsi Verwaltungsbefehle aktiviert
werden. Nach erfolgtem Neustart

derAnwendung werden autom. alle Depots vom Configserver ermittelt.

.. raw:: html

   <div class="rvps2">

+-------------------------+-------------------------+-------------------------+
| |image51|               | Die Tabellenanzeige     | Der Schalter arbeitet   |
|                         | schaltet zwischen       | wie ein Umschalter, d.  |
| |image52|               | Depotansicht und        | h. so lange er farbig   |
|                         | Repository              | markiert ist, wird der  |
|                         | Ordneransicht um.       | Inhalt des Repository   |
|                         |                         | Ordners angezeigt.      |
|                         |                         |                         |
|                         |                         | Ist diese Funktion      |
|                         |                         | gew�hlt, zeigt die      |
|                         |                         | Spalte "Typ" der        |
|                         |                         | Tabelle die MD5 Summe   |
|                         |                         | des Pakets an.          |
+-------------------------+-------------------------+-------------------------+
| |image53|               | Beendet den Dialog      |                         |
+-------------------------+-------------------------+-------------------------+
| |image54|               | | Vergleich der beiden  | Der Schalter arbeitet   |
|                         |   Tabelleninhalte       | wie ein Umschalter, d.  |
| |image55|               |   durchf�hren.          | h. so lange er farbig   |
|                         | |                       | markiert ist, werden in |
|                         | | WICHTIG: Werden REPO  | den beiden Tabellen nur |
|                         |   St�nde miteinander    | die Unterschiede        |
|                         |   verglichen, so        | angezeigt.              |
|                         |   erfolgt der Vergleich |                         |
|                         |   inklusive MD5 der     | W�hrend der Vergleich   |
|                         |   Datei.                | durchgef�hrt wird, ist  |
|                         |                         | die Schrift rot, nach   |
|                         |                         | Abschluss des           |
|                         |                         | Vergleichs gr�n.        |
+-------------------------+-------------------------+-------------------------+
| |image56|               | Depots und Depotst�nde  | Achtung: Die            |
|                         | neu einlesen            | vorhandenen Depotserver |
|                         |                         | werden �ber einen       |
|                         |                         | Programmneustart hinaus |
|                         |                         | zwischengespeichert!    |
|                         |                         | Falls Server in der     |
|                         |                         | Auflistung fehlen, kann |
|                         |                         | einmaliges Neueinlesen  |
|                         |                         | helfen.                 |
+-------------------------+-------------------------+-------------------------+
| |image57|               | Vergleichsreporte       |                         |
|                         | generieren              |                         |
+-------------------------+-------------------------+-------------------------+
| |image58|               | Paket in ein Depot      | Es wird nach dem        |
|                         | installieren            | Zieldepot gefragt.      |
+-------------------------+-------------------------+-------------------------+
| |image59|               | Diese Schaltfl�che      | Die Schaltfl�che �ndert |
|                         | erf�llt eine            | ihre Funktionsweise je  |
| |image60|               | Doppelfunktion:         | nachdem, was in der     |
|                         |                         | zuletzt angeklickten    |
|                         | Deinstallieren: das     | Tabelle gerade          |
|                         | zuletzt angeklickte     | angezeigt wird.         |
|                         | Paket in einer der      |                         |
|                         | beiden Tabellen wird    |                         |
|                         | auf dem zugeh�rigen     |                         |
|                         | Depot deinstalliert     |                         |
|                         |                         |                         |
|                         | L�schen: das zuletzt    |                         |
|                         | angeklickte Paket wird  |                         |
|                         | aus dem Repository      |                         |
|                         | Ordner (auf             |                         |
|                         | Dateisystemebene)       |                         |
|                         | gel�scht                |                         |
|                         |                         |                         |
|                         | (Mehrfachauswahl        |                         |
|                         | m�glich)                |                         |
+-------------------------+-------------------------+-------------------------+
| |image61|               | Paket in ein Repository | Die tempor�r auf den    |
|                         | hochladen. Dabei wird   | Configserver            |
|                         | das Paket erst auf den  | �bertragene Datei wird  |
|                         | Configserver in ein     | sicherheitshalber nicht |
|                         | tempor�res Verzeichnis  | autom. gel�scht.        |
|                         | geschrieben             |                         |
|                         | ("!inst\_tmp!"          |                         |
|                         | unterhalb der           |                         |
|                         | opsi\_workbench) und    |                         |
|                         | dann per                |                         |
|                         | "opsi-package-manager   |                         |
|                         | -u -d" verarbeitet.     |                         |
+-------------------------+-------------------------+-------------------------+
| |image62|               | Hebt die Registrierung  |                         |
|                         | des Depotservers am     |                         |
|                         | Konfigserver auf. Damit |                         |
|                         | wird der Depotserver    |                         |
|                         | ABER NICHT gel�scht,    |                         |
|                         | sondern nur aus der     |                         |
|                         | internen Hosttabelle    |                         |
|                         | entfernt!               |                         |
+-------------------------+-------------------------+-------------------------+
| |image63|               | F�hrt den Befehl        | Kann nur dann verwendet |
|                         | "opsi-setup             | werden, wenn "Hole REPO |
|                         | --set-rights            | Inhalt" aktiv ist.      |
|                         | /var/lib/opsi/repositor |                         |
|                         | y"                      | Ist bspw. dann          |
|                         | auf dem ausgew�hlten    | erforderlich, wenn auf  |
|                         | Depot aus.              | den Inhalt einer        |
|                         |                         | MD5-Datei eines Pakets  |
|                         |                         | nicht zugegriffen       |
|                         |                         | werden kann.            |
+-------------------------+-------------------------+-------------------------+
| |image64|               | F�hrt den Befehl        | Kann nur dann verwendet |
|                         | "opsi-package-updater   | werden, wenn "Hole REPO |
|                         | -vv" auf dem gew�hlten  | Inhalt" aktiv ist.      |
|                         | Depot aus.              |                         |
+-------------------------+-------------------------+-------------------------+
| |image65|               | Generiert f�r die       |                         |
|                         | ausgew�hlten Produkte   |                         |
|                         | auf dem betreffenden    |                         |
|                         | Repository die MD5      |                         |
|                         | Dateien.                |                         |
+-------------------------+-------------------------+-------------------------+
| |image66|               | Ping-Check auf das      |                         |
|                         | gew�hlte Depot          |                         |
+-------------------------+-------------------------+-------------------------+
| |image67|               | Reboot eines Depots     |                         |
+-------------------------+-------------------------+-------------------------+
| |image68|               | Shutdown eines Depots   |                         |
+-------------------------+-------------------------+-------------------------+
| |image69|               | Anzeige des Logbuchs    |                         |
+-------------------------+-------------------------+-------------------------+

.. raw:: html

   </div>

Beispiel I f�r eine Vergleichssituation zwischen zwei Depots:

|image70|

Im linken Depot befinden sich jede Menge Produkte, die das rechte Depot
nicht kennt. Umgekehrt hat das rechte ein zus�tzlich Produkt.

Beispiel II f�r eine Vergleichssituation zwischen Depot und Repository
Ordner:

|image71|

Wie man erkennen kann, sind folgende Funktionen aktiv:

- linke Tabelle: Ansicht Repository Ordner

- rechte Tabelle: Depot

- Vergleichsmodus ist eingeschaltet

-> Im rechten Repo sind 4 Pakete vorhanden, die sich im linken Depot
nicht befinden.

Hinweis:

Das in der Spalte "Typ" nur "(depo<->repo)" angezeigt wird, liegt daran,
dass im Repository Ordner die Produkttypen "NetbootProduct" bzw.
"LocalbootProduct" nicht einfach ermittelbar sind.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
EPub-Generator <http://www.helpndoc.com/de/epub-ebooks-erstellen>`__

Report generieren
~~~~~~~~~~~~~~~~~

|image72|

Mit Hilfe des Reportauswahl-Dialogs k�nnen gezielt Depotvergleiche
durchgef�hrt und als druckbare HTML Reporte ausgegeben werden.

HINWEIS:

Wird als Vergleichsbasis "Inhalt Repository Ordner" gew�hlt, kann die
Berichtsgenerierung bei einer gro�en Serveranzahl recht lange dauern.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
EBook-Editor <http://www.helpndoc.com/de/epub-ebooks-erstellen>`__

Client Agent verteilen
----------------------

|image73|

Erl�uterung zur Option "Nicht warten":

Wird diese Option angew�hlt, so wird der Deploy Befehl auf dem Server
abgesetzt und nicht auf die Beendigung der Ausf�hrung gewartet, d. h. es
gibt keine R�ckmeldung �ber das PLINK Log. Bei gr��eren Deploys f�hrt
das dazu, dass der opsiPackageBuilder nicht "ewig" zu h�gen scheint,
sondern man kann direkt weiterarbeiten.

Hinweise zum Feld "Vorab-Befehl":

Steht in diesem Fehle eine Anweisung, so wird sie vor dem Deploy via
winexe (entspricht weitestgehend psexec f�r Linux) direkt auf dem Client
ausgef�hrt.

| 
| Daran sind allerdings einige Bedingungen gekn�pft:

- Auf dem Server muss das Programm 'winexe' �ber die Pfadvariable
erreichbar sein vorhanden sein (mit whereis pr�fen) / hierbei wird nicht
auf die im opsi-client-agent mitgelieferte Version zur�ckgegriffen.

- Er kann nur auf einen einzelnen Client abgesetzt werden. Bei
Verteilung an mehrere Clients ist der Eintrag au�er Kraft.

- Befehlsverkettung funktioniert begrenzt. && und \|\| m�ssen in normale
Anf�hrungszeichen (kein Apostroph) gesetzt werden, bspw. "&&" oder
"\|\|"

- Piping und Ausgabeumlenkung sind sehr fallabh�ngig. Da hilft nur
opsiPackageBuilder Log einschalten und ausprobieren.

.. raw:: html

   <div class="rvps2">

+--------------------------------------------------------------------------+
| Beispiel:                                                                |
|                                                                          |
| - folgender Befehl soll abgesetzt werden:                cd              |
| c:\\TEMP\\RZInstall\\ETHLineSpeed && set NWDUPLEXMODE=AUTOSENS && start  |
| install.cmd                                                              |
|                                                                          |
| - gem. obiger Hinweise muss in das Feld:        cd                       |
| c:\\TEMP\\RZInstall\\ETHLineSpeed "&&" set NWDUPLEXMODE=AUTOSENS "&&"    |
| start install.cmd                                                        |
|                                                                          |
| - opsiPackageBuilder macht daraus im Hintergrund (plink Authorisation,   |
| Port k�nnen ja nach Einstellung variieren):                              |
|                                                                          |
| "plink.exe" -batch -P 22 <opsi admin>@<config server> -pw                |
| "<opsiserverpass>" winexe --debug-stderr --user "esaadm" --password      |
| "<localadminpass>" //client 'cmd /c cd c:\\TEMP\\RZInstall\\ETHLineSpeed |
| "&&" set NWDUPLEXMODE=AUTOSENS "&&" start install.cmd'                   |
|                                                                          |
| Das Kommando wir nat�rlich ohne Zeilenumbr�che abgesetzt. Die Werte in   |
| <> sind entsprechend der eigenen Umgebung zu ersetzen.)                  |
|                                                                          |
| Am besten ist es, den zu setzenden Befehl per Hand auf der Kommandozeile |
| erst an einer Maschine zu pr�fen und dann entsprechend im Feld zu        |
| hinterlegen. Die letzten 20 Befehle werden in der INI Datei gespeichert  |
| und bleiben somit f�r zuk�nftige Verwendung erhalten (Sollte in einem    |
| dieser Befehle das Paragraphensymbol "�" verwendet worden sein, wird die |
| Liste beim erneuten �ffnen des Dialogs merkw�rdig aussehen, da dieses    |
| Symbol intern f�r die Trennung der Kombobox Elemente verwendet wird.)    |
|                                                                          |
                                                                          
+--------------------------------------------------------------------------+

.. raw:: html

   </div>

Achtung:

- Wird an einen einzelnen Client verteilt, so kann im Multi-Depot
Betrieb der Quelldepotserver ausgew�hlt werden, um Leitungskapazit�ten
zu schonen.

- Wenn an mehrere Clients verteilt wird, dann kann im Multi-Depot
Betrieb KEIN Depotserver ausgew�hlt werden, da f�r den Deploybefehl eine
Liste in Dateiform erstellt werden muss. Dies ist momentan nur auf dem
Workbench Share des zugeordneten Konfigservers zul�ssig. Ebenfalls f�hrt
es zu Fehlern, wenn der Entwicklungsordner nicht auf dem Workbench Share
des Konfigservers liegt. Dann kann der Deploybefehl ebenfalls nicht
ordnungsgem�� abgesetzt werden.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Benutzerfreundliches
Werkzeug zum Erstellen von HTML-Hilfedateien und
Hilfewebsites <http://www.helpndoc.com/de/hilfeentwicklungs-tool>`__

Men�
====

Das Hauptmen� im Einzelnen.

`Men� "Datei" <#Datei>`__

`Men� "Werkzeuge" <#Werkzeuge>`__

`Men� "Extras" <#Extras>`__

`Men� "?" <#NeuesThema>`__

Erl�uterungen erfolgen in den einzelnen Kapiteln, falls notwendig.

Mit dem Personal Edition von HelpNDoc erstellt: \ `EBooks einfach
erstellen <http://www.helpndoc.com/de/funktionen-tour>`__

Datei
-----

|image74|

Mit dem Personal Edition von HelpNDoc erstellt: \ `eBooks f�r den Kindle
verfassen <http://www.helpndoc.com/de/funktionen-tour/ebooks-fuer-den-amazon-kindle-erstellen>`__

Werkzeuge
---------

|image75|

-  Skripte neu scannen
   Wenn �nderungen an den Installationsskripten durchgef�hrt und
   insbesondere weitere Include- oder Sub-Anweisungen eingebaut wurden,
   so kann die Paketstruktur hiermit f�r eine korrekte Darstellung im
   Skriptbaum neu eingelesen werden.

-  Paketrechte setzen
   Die Linux-seitig bestehenden Verzeichnisrechte auf den opsi Standard
   korrigieren. Dazu ist allerdings in den
   \ `Einstellungen <#Allgemein>`__\  die Hinterlegung des root
   Kennworts des opsi Servers notwendig.
-  Start opsi-winst
   Starten der opsi-winst Entwicklungsoberfl�che zum Starten/ �berwachen
   und Debuggen von opsi-winst Skripten.
   Der Men�punkt setzte eine bestehende opsi-winst-client Installation
   voraus, bzw sucht die winst32.exe in folgendem Pfad:
   %ProgramFiles%\\opsi.org\\opsi-client-agent\\opsi-winst\\winst32.exe
-  Skripteditor
   Startet den in den Einstellungen hinterlegten Editor.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
Hilfegenerator <http://www.helpndoc.com/de/funktionen-tour>`__

Extras
------

|image76|

-  Zeige PLINK Log
   F�r den Fall, die Anzeige des PLINK Logs nach erfolgter
   Onlinefunktion wurde in den Einstellungen abgeschaltet, kann die
   Anzeige hier manuell aufgerufen werden.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis
Kindle-Hersteller <http://www.helpndoc.com/de/funktionen-tour/ebooks-fuer-den-amazon-kindle-erstellen>`__

?
-

|image77|

-  Nach Updates suchen
   Manuellen Aktualisierung der installierten Version von opsi Package
   Builder durchf�hren, falls eine neuere Version verf�gbar ist.
-  Zeige Changelog
   Das opsi Package Builder Versions-Changelog anzeigen (im Gegensatz
   zum Paket-Changelog!)

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
Multiformat-Hilfsgenerator <http://www.helpndoc.com/de/hilfeentwicklungs-tool>`__

Einstellungen
=============

Nachfolgend werden die einzelnen Bestandteile des Einstellungen Dialog
kurz aufgezeigt:

`Allgemein <#Allgemein>`__

`Programmeinstellungen <#Programmeinstellungen>`__

`opsi Verwaltungsbefehle <#opsiVerwaltungsbefehle>`__

`Automatische Updates <#Nachrichten>`__

Hinweis: es kann mehr als eine Konfiguration parallel betrieben werden.
Genaueres zum Vorgehen dazu unter \ `Mehrere
Konfigurationen. <#MehrereKonfigurationen>`__

Mit dem Personal Edition von HelpNDoc erstellt: \ `Benutzerfreundliches
Werkzeug zum Erstellen von HTML-Hilfedateien und
Hilfewebsites <http://www.helpndoc.com/de/hilfeentwicklungs-tool>`__

Allgemein
---------

|image78|

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis
Webhilfegenerator <http://www.helpndoc.com/de>`__

Programmeinstellungen
---------------------

|image79|

Mit dem Personal Edition von HelpNDoc erstellt: \ `EPub-B�cher f�r das
iPad verfassen <http://www.helpndoc.com/de/epub-ebooks-erstellen>`__

opsi Verwaltungsbefehle
-----------------------

|image80|

Mit dem Personal Edition von HelpNDoc erstellt: \ `iPhone-Dokumentation
einfach
erstellen <http://www.helpndoc.com/de/funktionen-tour/erstellen-sie-iphone-webseiten-und-dokumentationen>`__

Nachrichten
-----------

|image81|

Mit dem Personal Edition von HelpNDoc erstellt: \ `Elektronische B�cher
einfach verfassen <http://www.helpndoc.com/de/epub-ebooks-erstellen>`__

Automatische Updates
--------------------

|image82|

Mit dem Personal Edition von HelpNDoc erstellt: \ `iPhone Websites
einfach
gemacht <http://www.helpndoc.com/de/funktionen-tour/erstellen-sie-iphone-webseiten-und-dokumentationen>`__

Tool "Skript Editor"
====================

Zusatztool "Skript Editor"

Ab opsi Package Builder Version 5.3 wird ein kleiner Skripteditor
mitinstalliert. Dieser Skripteditor kann, wenn entsprechend
konfiguriert, direkt �ber den Skriptbaum oder �ber den Link im Startmen�
aufgerufen werden.

|image83|

Wesentliche Merkmale:

-  Farbige Syntaxhervorhebung
-  "Falten" des Quellcodes (optional: kompakt, mit Kommentaren)
-  Lexerdefinition anpassbar (dazu muss der Editor per Startmen� Eintrag
   aufgerufen werden)
-  Autocomplete f�r Syntaxelemente und Variablen
-  Frei definierbare und wiederverwendbare Codebl�cke ("Snippets")

Die Kernkomponente des Editors bildet das Modul
"\ `Scintilla <http://www.scintilla.org/>`__\ ", welches auch in
bekannten Editoren, wie bspw.
\ `Notepad++ <http://notepad-plus-plus.org/>`__\ , verwendet wird. Die
lexikalischen Elemente (Syntaxhervorhebung und Faltung) sind allerdings
komplett in AutoIt geschrieben ist, da Scintilla f�r opsi Skripte kein
eigenes Modul zur Darstellung mitliefert. Dadurch, dass AutoIt eine
Interpretersprache ist, ist er damit langsamer als andere Editoren und
eignet sich daher nur bedingt zur Bearbeitung sehr gro�er Skripte, vor
allem bei eingeschalteter Syntaxhervorhebung und/oder Faltung. In den
\ `Einstellungen <#Programmeinstellungen>`__\  von opsi Package Builder
l�sst sich jedoch vorgeben, ob der Editor mit diesen Funktionen
�berhaupt aufgerufen wird oder nicht, sofern der Aufruf direkt �ber den
Skriptbaum erfolgt. Bei einem Aufruf �ber den Link im Startmen� sind
Syntaxhervorhebung und Faltung generell beim Start ausgeschaltet und
k�nnen �ber das Editormen� "Ansicht" aktiviert werden.

Alle weiteren Men�funktionen entsprechen denen g�ngiger Editoren und
werden nicht weiter beschrieben.

(Der Editor kann auch �ber die Kommandozeile aufgerufen werden. Weitere
Informationen zu den m�glichen Kommandozeilenparametern k�nnen mit der
Option "--help" aufgerufen werden.)

Mit dem Personal Edition von HelpNDoc erstellt: \ `EPub-B�cher einfach
erstellen <http://www.helpndoc.com/de/funktionen-tour>`__

Tutorial
========

(Muss noch geschrieben werden...)

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
Multiformat-Hilfsgenerator <http://www.helpndoc.com/de/hilfeentwicklungs-tool>`__

Kommandozeilenparameter
=======================

Kommandozeilenparameter f�r opsi Package Builder

Neben der normalen Fensteroberfl�che lassen sich zur Automatisierung
einige Funktionen per Kommandozeile aufrufen. Nachfolgend eine
Aufstellung der M�glichen Parameter und Kombinationen. Die Parameter
k�nnen hierbei sowohl in Lang- als auch in Kurzform geschrieben werden
(siehe Beipiele unten).

WICHTIG: siehe auch die Hinweise bei Verwendung mehrerer Konfigurationen
\ `hier <#MehrereKonfigurationen>`__

.. raw:: html

   <div class="rvps2">

+--------------------+--------------------+--------------------+--------------------+
| Kurz               | Lang               | Beschreibung       | Hinweise           |
+--------------------+--------------------+--------------------+--------------------+
| -p                 | --path             | Paketname oder     | Hier kann entweder |
|                    |                    | -pfad              | der komplette Pfad |
|                    |                    |                    | zum                |
|                    |                    |                    | Entwicklungsordner |
|                    |                    |                    | oder nur der Name  |
|                    |                    |                    | des Pakets         |
|                    |                    |                    | angegeben sein:    |
|                    |                    |                    |                    |
|                    |                    |                    | Hinweis: ein Pfad  |
|                    |                    |                    | au�erhalb des in   |
|                    |                    |                    | den Einstellungen  |
|                    |                    |                    | hinterlegten       |
|                    |                    |                    | Entwicklungsordner |
|                    |                    |                    | s                  |
|                    |                    |                    | ist nicht          |
|                    |                    |                    | zul�ssig.          |
+--------------------+--------------------+--------------------+--------------------+
| -w                 | --no-netdrv        | Entwicklungsordner | Falls das Programm |
|                    |                    | nicht mounten      | so eingestellt     |
|                    |                    |                    | ist, dass es beim  |
|                    |                    |                    | Start zuerst       |
|                    |                    |                    | versucht, die      |
|                    |                    |                    | Freigabe           |
|                    |                    |                    | opsi\_workbench    |
|                    |                    |                    | als Laufwerk zu    |
|                    |                    |                    | mappen, so kann    |
|                    |                    |                    | das mit dieser     |
|                    |                    |                    | Option deaktiviert |
|                    |                    |                    | werden. Das ist    |
|                    |                    |                    | dann sinnvoll,     |
|                    |                    |                    | wenn in einem      |
|                    |                    |                    | gr��eren Script    |
|                    |                    |                    | das Verzeichnis    |
|                    |                    |                    | vorher manuell     |
|                    |                    |                    | zugeordnet wurde.  |
+--------------------+--------------------+--------------------+--------------------+
| -b                 | --build            | Paketieren         | Diese Option hat   |
|                    |                    |                    | zus�tzlich vier    |
|                    |                    |                    | verschiedene       |
|                    |                    |                    | Parameter:         |
|                    |                    |                    |                    |
|                    |                    |                    | | a)               |
|                    |                    |                    |   --build=cancel   |
|                    |                    |                    | | Besteht das      |
|                    |                    |                    |   Paket bereits,   |
|                    |                    |                    |   erfolgt keine    |
|                    |                    |                    |   Paketierung      |
|                    |                    |                    |   (Vorgabe).       |
|                    |                    |                    |                    |
|                    |                    |                    | | b)               |
|                    |                    |                    |   --build=rebuild  |
|                    |                    |                    | | Ein bestehendes  |
|                    |                    |                    |   Paket wird mit   |
|                    |                    |                    |   der gleichen     |
|                    |                    |                    |   Versionierung    |
|                    |                    |                    |   �berschrieben.   |
|                    |                    |                    |                    |
|                    |                    |                    | | c) --build=new   |
|                    |                    |                    | | Die              |
|                    |                    |                    |   Paketversionsnum |
|                    |                    |                    | mer                |
|                    |                    |                    |   wird um einen    |
|                    |                    |                    |   Zeitstempel      |
|                    |                    |                    |   erweitert und es |
|                    |                    |                    |   wird neu         |
|                    |                    |                    |   paketiert.       |
|                    |                    |                    |                    |
|                    |                    |                    | | d)               |
|                    |                    |                    |   --build=interact |
|                    |                    |                    | ive                |
|                    |                    |                    | | Der Anwender     |
|                    |                    |                    |   wird interaktiv  |
|                    |                    |                    |   um eine          |
|                    |                    |                    |   Entscheidung     |
|                    |                    |                    |   gebeten (nicht   |
|                    |                    |                    |   mit --quiet),    |
|                    |                    |                    |   falls das Paket  |
|                    |                    |                    |   existiert.       |
|                    |                    |                    |                    |
|                    |                    |                    | Beispiel zum       |
|                    |                    |                    | Zeitstempel der    |
|                    |                    |                    | Variante c):       |
|                    |                    |                    |                    |
|                    |                    |                    | | Paketname mit    |
|                    |                    |                    |   urspr�nglicher   |
|                    |                    |                    |   Versionsnummerie |
|                    |                    |                    | rung:              |
|                    |                    |                    | | ->               |
|                    |                    |                    |   productname\_2.5 |
|                    |                    |                    | -1                 |
|                    |                    |                    |                    |
|                    |                    |                    | Paketname mit      |
|                    |                    |                    | zus�tzlichem       |
|                    |                    |                    | Zeitstempel:       |
|                    |                    |                    |                    |
|                    |                    |                    | ->                 |
|                    |                    |                    | productname\_2.5-1 |
|                    |                    |                    | .corr170739corr    |
|                    |                    |                    |                    |
|                    |                    |                    | Bei Variante c)    |
|                    |                    |                    | werden immer neue  |
|                    |                    |                    | Pakete erzeugt.    |
|                    |                    |                    | Hierbei ist auf    |
|                    |                    |                    | den                |
|                    |                    |                    | Speicherplatzbedar |
|                    |                    |                    | f                  |
|                    |                    |                    | zu achten!         |
+--------------------+--------------------+--------------------+--------------------+
| -i                 | --install          | Paket auf opsi     | Sollte in den      |
|                    |                    | Server             | Einstellungen      |
|                    |                    | installieren       | "Depotfunktionen   |
|                    |                    |                    | aktivieren"        |
|                    |                    |                    | gesetzt sein, wird |
|                    |                    |                    | diese Einstellung  |
|                    |                    |                    | tempor�r           |
|                    |                    |                    | deaktiviert und    |
|                    |                    |                    | der urspr�nglich   |
|                    |                    |                    | konfigurierte      |
|                    |                    |                    | Installationsbefeh |
|                    |                    |                    | l                  |
|                    |                    |                    | verwendet.         |
+--------------------+--------------------+--------------------+--------------------+
| -s                 | --instsetup        | Paket installieren | Kann nicht mit     |
|                    |                    | und auf allen      | --install          |
|                    |                    | Clients Aktion auf | kombiniert werden. |
|                    |                    | "setup" setzen, wo |                    |
|                    |                    | der Produktstatus  |                    |
|                    |                    | "installed" ist    |                    |
+--------------------+--------------------+--------------------+--------------------+
| -u                 | --uninstall        | Paket auf opsi     | Sollte in den      |
|                    |                    | Server             | Einstellungen      |
|                    |                    | deinstallieren     | "Depotfunktionen   |
|                    |                    |                    | aktivieren"        |
|                    |                    |                    | gesetzt sein, wird |
|                    |                    |                    | diese Einstellung  |
|                    |                    |                    | tempor�r           |
|                    |                    |                    | deaktiviert und    |
|                    |                    |                    | der urspr�nglich   |
|                    |                    |                    | konfigurierte      |
|                    |                    |                    | Deinstallationsbef |
|                    |                    |                    | ehl                |
|                    |                    |                    | verwendet.         |
+--------------------+--------------------+--------------------+--------------------+
| -r                 | --set-rights       | Paketverzeichnisre |                    |
|                    |                    | chte               |                    |
|                    |                    | neu setzen         |                    |
+--------------------+--------------------+--------------------+--------------------+
| -n                 | --no-gui           | Starte ohne        | Die Ausgabe von    |
|                    |                    | Oberfl�che         | Meldungen erfolgt  |
|                    |                    |                    | im aufrufenden CMD |
|                    |                    |                    | - Fenster.         |
+--------------------+--------------------+--------------------+--------------------+
| -x                 | --no-update        | Deaktiviere den    | �berschreibt die   |
|                    |                    | internen Updater   | im Einstellungen   |
|                    |                    | dauerhaft          | Dialog gesetzte    |
|                    |                    |                    | Option.            |
+--------------------+--------------------+--------------------+--------------------+
| -q                 | --quiet            | Kein Ausgabe       | Das Programm kehrt |
|                    |                    |                    | nach Aufruf ohne   |
|                    |                    |                    | weitere Meldungen  |
|                    |                    |                    | zum Prompt zur�ck. |
|                    |                    |                    | Ist gleichzeitig   |
|                    |                    |                    | der Parameter      |
|                    |                    |                    | --log angegeben,   |
|                    |                    |                    | so werden          |
|                    |                    |                    | weiterhin alle     |
|                    |                    |                    | Meldungen in der   |
|                    |                    |                    | Log-Datei          |
|                    |                    |                    | protokolliert.     |
|                    |                    |                    |                    |
|                    |                    |                    | Hinweis: kann      |
|                    |                    |                    | nicht mit          |
|                    |                    |                    | --build=interactiv |
|                    |                    |                    | e                  |
|                    |                    |                    | verwendet werden!  |
+--------------------+--------------------+--------------------+--------------------+
| -l                 | --log              | | Schreibe         | | Wir nur --log    |
|                    |                    |   s�mtliche        |   angegeben, so    |
|                    |                    |   Ausgaben in      |   schreibt opsi    |
|                    |                    |   Log-Datei        |   Package Builder  |
|                    |                    | | (auch bei        |   die Datei        |
|                    |                    |   --quiet)         |   standardm��ig in |
|                    |                    |                    |   den              |
|                    |                    |                    | | Ordner           |
|                    |                    |                    |   %AppData%\\opsi  |
|                    |                    |                    |   PackageBuilder.  |
|                    |                    |                    | |                  |
|                    |                    |                    |                    |
|                    |                    |                    | Beispiel um eine   |
|                    |                    |                    | andere Log-Datei   |
|                    |                    |                    | anzulegen:         |
|                    |                    |                    |                    |
|                    |                    |                    | --log=c:\\temp\\op |
|                    |                    |                    | sipackagebuilder.l |
|                    |                    |                    | og                 |
+--------------------+--------------------+--------------------+--------------------+
| -d                 | --debug            | Schreibe           | Hier werden        |
|                    |                    | zus�tzliche Debug  | zus�tzliche Debug  |
|                    |                    | Informationen      | Ausgaben erzeugt.  |
|                    |                    |                    | Im Regelfall nicht |
|                    |                    |                    | ben�tigt.          |
|                    |                    |                    |                    |
|                    |                    |                    | Hinweis: kann zu   |
|                    |                    |                    | SEHR viel          |
|                    |                    |                    | Textausgabe        |
|                    |                    |                    | f�hren.            |
+--------------------+--------------------+--------------------+--------------------+
| -h                 | --help             | Anzeige der Hilfe  | a) --help erzeugt  |
|                    |                    |                    | ein Dialogfenster  |
|                    |                    |                    |                    |
|                    |                    |                    | b) --help --no-gui |
|                    |                    |                    | gibt die Hilfe auf |
|                    |                    |                    | der Kommandozeile  |
|                    |                    |                    | aus                |
+--------------------+--------------------+--------------------+--------------------+

.. raw:: html

   </div>

Verarbeitungsreihenfolge, falls mehrere Prozessparameter angegeben
werden:

1.) Rechte setzen -> 2.) Paketieren -> 3.) Deinstallieren (falls
existent) -> 4.) Installieren

Wichtig:

Sollten die Depotfunktionen f�r den normalen GUI Betrieb aktiviert sein,
so werden sie bei Verwendung des Schalters --no-gui tempor�r
deaktiviert. Das

Ziel f�r s�mtliche Aktionen ist dann der im Reiter "Allgemein"
(Einstellungen) angegebene Konfigserver.

Genauso werden in diesem Fall die urspr�nglichen Befehle verwendet, die
in den Eingabefeldern des Reiters "opsi Verwaltungsbefehle"
(Einstellungen) hinterlegt wurden. Um diese Parameter trotz aktivierter
Depotfunktionen f�r den no-GUI Betrieb zu �ndern, wie folgt vorgehen:

- die Option "Depotfunktionen aktivieren" ausschalten

- die Befehle in den Eingabefeldern entsprechend ab�ndern

- Einstellungen speichern

- die Option "Depotfunktionen aktivieren" einschalten

- Einstellungen erneut speichern

Hinweis:

Wenn der Parameter --no-gui nicht angegeben ist, �ffnet sich zuerst die
normale Fensteroberfl�che und danach werden s�mtliche Prozessschritte
abgearbeitet.

Beispiel 1:

Langform: opsiPackageBuilder.exe --path=w:\\opsi\\testpak --build=new
--no-gui --log=c:\\temp\\opb.log

Kurzform: opsiPackageBuilder.exe -p=w:\\opsi\\testpak -b=new -n
-l=c:\\temp\\opb.log

Dieser Befehl startet das Programm ohne Oberfl�che, l�dt das Paket im
Ordner w:\\opsi\\testpak, erzeugt bei Vorhandensein ein neues Paket
inkl. Zeitstempel und schreibt s�mtliche Ausgaben in die Datei
C:\\temp\\opb.log.

Beispiel 2:

Langform: OPSIPackageBuilder.exe --path=testpak --build=interactive
--install --no-gui --log

Kurzform: OPSIPackageBuilder.exe -p=testpak -b=interactive -n -l

Dieser Befehl startet das Programm ohne Oberfl�che, l�dt das Paket im
Ordner w:\\opsi\\testpak (sofern w:\\opsi der hinterlegte
Entwicklungsordner ist), fragt bei Vorhandensein des Pakets interaktiv
nach dem weiteren Vorgehen, installiert das Paket nach Erstellung auf
dem Server und schreibt s�mtliche Ausgaben in die Datei %AppData%\\opsi
PackageBuilder\\opb-session.log.

Beispiel 3:

Gemischte Form: OPSIPackageBuilder.exe --path=testpak -b=rebuild
--install --uninstall --set-rights -q -l=.\\opb.log

Dieser Befehl startet das Programm ohne Oberfl�che, l�dt das Paket im
Ordner w:\\opsi\\testpak (sofern w:\\opsi der hinterlegte
Entwicklungsordner ist), setzt die Rechte auf dem Paketordner neu,
�berschreibt beim Paketieren ein evtl. vorhandenes Paket gleicher
Version, deinstalliert die bestehende Version (falls vorhanden) und
installiert die gerade neu paketierte Fassung. Auf der Konsole wird
nichts ausgegeben, s�mtliche Ausgaben gehen in die Log-Datei .\\opb.log.

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis
Hilfeverfassungsumfeld <http://www.helpndoc.com/de/hilfeentwicklungs-tool>`__

Mehrere Konfigurationen
=======================

Mehrere Konfigurationen f�r opsi Package Builder anlegen

Normalerweise werden s�mtliche Konfigurationsoptionen �ber den
Einstellungsdialog definiert. Diese Einstellungen finden sich in der
Datei "config.ini" in folgenden Pfaden:

-  Windows XP: C:\\Dokumente und
   Einstellungen\\<Benutzer>Anwendungsdaten\\opsiPackageBuilder
-  h�here Windows Versionen:
   C:\\Users\\<Benutzer>\\AppData\\Roaming\\opsiPackageBuilder

Um verschiedene Konfigurationen zu nutzen, k�nnen in dem jeweiligen Pfad
einfach mehrere, unterschiedlich benannte INI-Dateien hinterlegt werden.
Beim Start des Programms wird dann nach der zu verwendenden gefragt und
diese in "config.ini" umkopiert.

Beispielhafte Vorgehensweise:

-  beim allerersten Start nach der Installation erzwingt opsi Package
   Builder die Erstellung einer Konfiguration
-  opsi Package Builder schlie�en, dann die erstellte Datei config.ini
   (bspw.) im selben Ordner in die neue Datei produktiv.ini kopieren
-  beim jetzt folgenden Start fragt opsi Package Builder bereits, welche
   Konfiguration verwendet werden soll, dies einfach mit OK best�tigen
-  mit Hilfe des Einstellungedialogs die gew�nschte alternative
   Konfiguration erfassen
-  opsi Package Builder schlie�en, dann die ge�nderte Datei config.ini
   (bspw.) im selben Ordner in eine weitere Datei testumgebung.ini
   kopieren

Jetzt liegen zwei getrennte Konfigurationen vor.

Bei jedem nachfolgenden Start wird opsi Package Builder jetzt erst
fragen, welche verwendet werden soll und kopiert diese dann entsprechend
die Datei config.ini um.

ACHTUNG- Wird opsi Package Builder �ber die Kommandozeile aufgerufen
wird der Auswahldialog ausgeblendet, wenn folgende
\ `Parameter <#Kommandozeilenparameter>`__\  verwendet werden:

Es wird in diesem Fall immer die zuletzt gew�hlte Konfiguration
verwendet. Wurde also beim letzten Start per GUI bspw. die
"produktiv.ini" ausgew�hlt, so wird danach beim Start �ber die
Kommandozeile genau diese Konfiguration verwendet.

.. raw:: html

   <div class="rvps2">

+--------------------------------------+--------------------------------------+
| -p                                   | --path                               |
+--------------------------------------+--------------------------------------+
| -b                                   | --build                              |
+--------------------------------------+--------------------------------------+
| -i                                   | --install                            |
+--------------------------------------+--------------------------------------+
| -s                                   | --instsetup                          |
+--------------------------------------+--------------------------------------+
| -u                                   | --uninstall                          |
+--------------------------------------+--------------------------------------+
| -r                                   | --set-rights                         |
+--------------------------------------+--------------------------------------+
| -n                                   | --no-gui                             |
+--------------------------------------+--------------------------------------+
| -q                                   | --quiet                              |
+--------------------------------------+--------------------------------------+
| -h                                   | --help                               |
+--------------------------------------+--------------------------------------+

.. raw:: html

   </div>

Mit dem Personal Edition von HelpNDoc erstellt: \ `Funktionsreicher
EPub-Generator <http://www.helpndoc.com/de/epub-ebooks-erstellen>`__

Return Codes
============

Return Codes

opsi Package Builder gibt bei Ausf�hrung �ber die Kommandozeile folgende
Fehlercodes zur�ck:

.. raw:: html

   <div class="rvps2">

+--------------------------------------+--------------------------------------+
| 0                                    | OK                                   |
+--------------------------------------+--------------------------------------+
| 1010                                 | Can't open project                   |
+--------------------------------------+--------------------------------------+
| 2010                                 | Package file already exists, build   |
|                                      | canceled automatically               |
+--------------------------------------+--------------------------------------+
| 2020                                 | Package could not be deleted before  |
|                                      | re-building                          |
+--------------------------------------+--------------------------------------+
| 2030                                 | Package could not be saved before    |
|                                      | building                             |
+--------------------------------------+--------------------------------------+
| 2090                                 | Undefined error in build routine     |
+--------------------------------------+--------------------------------------+
| 3000                                 | Plink.exe not found                  |
+--------------------------------------+--------------------------------------+
| 3010                                 | PLINK - package exists already       |
+--------------------------------------+--------------------------------------+
| 3020                                 | PLINK - Error while building package |
|                                      | on server, check plink output        |
+--------------------------------------+--------------------------------------+
| 3030                                 | PLINK - Error while installing       |
|                                      | package on server, check plink       |
|                                      | output                               |
+--------------------------------------+--------------------------------------+
| 3040                                 | PLINK - Error while uninstalling     |
|                                      | package on server, check plink       |
|                                      | output                               |
+--------------------------------------+--------------------------------------+
| 5100                                 | Program already running              |
+--------------------------------------+--------------------------------------+
| 5200                                 | No INI file available                |
+--------------------------------------+--------------------------------------+
| 5300                                 | Mode incompatibility: --quiet and    |
|                                      | interactive mode combined on command |
|                                      | line                                 |
+--------------------------------------+--------------------------------------+
| 5400                                 | Incorrect commandline parameters     |
+--------------------------------------+--------------------------------------+
| 5500                                 | Could not allocate console window    |
+--------------------------------------+--------------------------------------+
| 5600                                 | Program exit due to running updater  |
+--------------------------------------+--------------------------------------+

.. raw:: html

   </div>

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis
Hilfeverfassungswerkzeug <http://www.helpndoc.com/de/hilfeentwicklungs-tool>`__

Systemvoraussetzungen
=====================

(Muss noch geschrieben werden...)

Mit dem Personal Edition von HelpNDoc erstellt: \ `iPhone-Dokumentation
einfach
erstellen <http://www.helpndoc.com/de/funktionen-tour/erstellen-sie-iphone-webseiten-und-dokumentationen>`__

Weitere Hilfe...
================

Weitere Hilfe, Anregungen und Tipps finden sich im eigenen Community
Bereich des opsi Forums f�r den opsi Package Builder.

Jegliche Form von sachlicher Kritik, Verbesserungsvorschl�gen und
Anregung sind nat�rlich herzlich willkommen.

Zum Community Bereich geht es \ `hier
lang <https://forum.opsi.org/viewforum.php?f=22>`__\ !

Mit dem Personal Edition von HelpNDoc erstellt: \ `Gratis EBook und
Dokumentationsgenerator <http://www.helpndoc.com/de>`__

Copyright � 2013-2014 by Holger Pandel. All Rights Reserved.

.. |image0| image:: img/AppLogo.png
.. |image1| image:: img/ProgTop3D.png
.. |image2| image:: img/Start.jpg
.. |image3| image:: img/ReiterPaket.jpg
.. |image4| image:: img/SkriptEdit.png
.. |image5| image:: img/SkriptSuch.png
.. |image6| image:: img/btnChangelog.png
.. |image7| image:: img/btnSkriptbaum.png
.. |image8| image:: img/ReiterAbhngigkeit.jpg
.. |image9| image:: img/btnNew.png
.. |image10| image:: img/btnUpd.png
.. |image11| image:: img/btnDel.png
.. |image12| image:: img/ReiterProduktvariable.jpg
.. |image13| image:: img/btnNew.png
.. |image14| image:: img/btnUpd.png
.. |image15| image:: img/btnSkripteLesen.png
.. |image16| image:: img/btnDel.png
.. |image17| image:: img/Paketfunktionen.jpg
.. |image18| image:: img/btnPacken.png
.. |image19| image:: img/btnInstallieren.png
.. |image20| image:: img/InstSetup.jpg
.. |image21| image:: img/btnEntfernen.png
.. |image22| image:: img/btnOrdner.png
.. |image23| image:: img/btnSpeichern.png
.. |image24| image:: img/btnInstallieren.png
.. |image25| image:: img/btnEntfernen.png
.. |image26| image:: img/ChangelogEdTop.png
.. |image27| image:: img/ChLogSimple.png
.. |image28| image:: img/btnSchliessen.png
.. |image29| image:: img/ChLogExt-Standard.png
.. |image30| image:: img/btnAnlegen.png
.. |image31| image:: img/btnUebernehmen.png
.. |image32| image:: img/btnEntfernen2.png
.. |image33| image:: img/btnSchliessen.png
.. |image34| image:: img/ChLogEdTopStandard.png
.. |image35| image:: img/ChLogEdTopIndividuell.png
.. |image36| image:: img/ChLogSiToEx.png
.. |image37| image:: img/ChLogExToSi.png
.. |image38| image:: img/Skriptbaum.png
.. |image39| image:: img/Zeitplaner.png
.. |image40| image:: img/btnJobsanlegen2.png
.. |image41| image:: img/btnJobslschen.png
.. |image42| image:: img/btnJobsRefresh.png
.. |image43| image:: img/btnJobsallelschen.png
.. |image44| image:: img/btnJobsschliessen.png
.. |image45| image:: img/JobAnlegen.png
.. |image46| image:: img/btnJobsanlegen.png
.. |image47| image:: img/btnAbbruch.png
.. |image48| image:: img/Paketbndel.png
.. |image49| image:: img/Paketbndel-Frage.png
.. |image50| image:: img/DepotManager.jpg
.. |image51| image:: img/btnHoleRepo.png
.. |image52| image:: img/btnHoleRepotBlau.png
.. |image53| image:: img/btnSchlie�en.png
.. |image54| image:: img/btnVergleichen.png
.. |image55| image:: img/btnVergleichenGr�n.png
.. |image56| image:: img/btnAktualisieren2.png
.. |image57| image:: img/btnVergleichsbericht.png
.. |image58| image:: img/btninstall.png
.. |image59| image:: img/btnDeinstallieren.png
.. |image60| image:: img/btnL�schen.png
.. |image61| image:: img/btnUpload.png
.. |image62| image:: img/btnDepotRegAufheben.png
.. |image63| image:: img/btnRechteSetzen2.png
.. |image64| image:: img/btnStartProdUpd2.png
.. |image65| image:: img/btnGeneriereMD5.png
.. |image66| image:: img/btnOnlineCheck2.png
.. |image67| image:: img/btnDepotNeustart2.png
.. |image68| image:: img/btnDepotShutdown.png
.. |image69| image:: img/btnPlinkLog.png
.. |image70| image:: img/DepotBeispielI.png
.. |image71| image:: img/DepotBeispielII.png
.. |image72| image:: img/ReportSelector.jpg
.. |image73| image:: img/DeployAgent.jpg
.. |image74| image:: img/MenuDatei.jpg
.. |image75| image:: img/MenuWerkzeuge.png
.. |image76| image:: img/MenuExtras.jpg
.. |image77| image:: img/MenuHelp.png
.. |image78| image:: img/Einst-Allgemein.jpg
.. |image79| image:: img/Einst-Programm.jpg
.. |image80| image:: img/Einst-opsi.png
.. |image81| image:: img/Einst-Nachrichten.jpg
.. |image82| image:: img/Einst-Update.jpg
.. |image83| image:: img/ScEdit.jpg
