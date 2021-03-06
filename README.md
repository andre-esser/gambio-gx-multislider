gambio-gx-multislider v1.0
==========================

Multislider für Gambio v2.1.x.x mit Text-Layern - kostenlos!

Ein kleines Demo-Video findest Du hier: [Gambio Multislider v1.0](http://www.stargutschein.de/content/gambio-gx2-slider-modul.html)



**Vorbereitung:**
-----------------

**Achte auf einen sorgfältigen Einbau und befolge genau die Anleitung!**

* Legen eine Sicherung Deiner vorhandenen Shop-Datenbank an.
* Sichere die Dateien des Shops vom FTP


* Führe die beiliegende SQL-Datei in einem geeignetem SQL-Programm aus. Bsp: [phpMyAdmin](http://www.phpmyadmin.net/home_page/index.php) oder [MySQLDumer](http://www.mysqldumper.de/)
* Lade die Datei-Struktur 1:1 auf Deinen Webserver ins Shopverzeichnis. Es werden keine vorhandenen Dateien überschrieben
* Das Verzeichnis `/multislider/uploads/` braucht rekusive Schreibrechte um Grafiken für den Slider uploaden zu können

> *Für einen fehlerhaften Einbau übernehmen wir keine Haftung!!*


**Integration:**
-----------------

*öffne:*

gm_javascript.js.php


*Suche:*

`/* EOF StyleEdit */`

*Füge danach ein:*

```
		if($_GET['page'] == 'Index'){
			include_once DIR_FS_CATALOG.'multislider/js/js_include.php';
		}
```



------------------------
*öffne:*

/system/classes/layout/IndexContentView.inc.php

*Suche:*

```
		protected function load_center_modules()
		{
```

*Füge direkt danach ein:*

```
		// Multislider
		$_multislider = MainFactory::create_object('MultisliderMainContentView');
	    $_multislider->set_('customers_fsk18_display', $_SESSION['customers_status']['customers_fsk18_display']);
	    $_multislider->set_('customers_status_id', $_SESSION['customers_status']['customers_status_id']);
	    $_multislider->set_('languages_id', $_SESSION['languages_id']);
	    $_multislider_view = $_multislider->get_html();
	    $this->set_content_data('MODULE_multislider', $_multislider_view);
```



--------------------------

*öffne*

/templates/EyeCandy/module/main_content.html

*Suche:*

```
{$MODULE_error}
```

*Füge danach ein:*

```
{$MODULE_multislider}
```


---------------------------

Fertig!

Nach der Installation:
--------
Da Gambio von Haus aus immer einen Cache aktiviert hat, ist es wichtig nach dem Einbau alle Cache-Dateien des Systems zu löschen. 
Dazu bitte einfach im Menüpunkt "Toolbox" im Admin-Bereich den Link "Cache leeren" auswählen und die ersten beiden Links anklicken.


Bugs:
-----
Sollte wieder erwarten ein Fehler auftauchen, schreibe in den [Bug-Tracker](https://github.com/bigclick/gambio-gx-multislider/issues/new). Wir werden uns so schnell wie möglich darum kümmern.



